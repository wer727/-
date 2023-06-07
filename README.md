<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>证件照制作程序</title>
</head>
<body>
	<h1>证件照制作程序</h1>
	<p>请选择照片规格尺寸：</p>

	<!-- 规格尺寸选择表单 -->
	<form>
		<label>
			<input type="radio" name="size" value="1" checked>
			3.5cm x 4.5cm
		</label>
		<br>
		<label>
			<input type="radio" name="size" value="2">
			4cm x 5cm
		</label>
		<br>
		<label>
			<input type="radio" name="size" value="3">
			5cm x 5cm
		</label>
		<br>
		<label>
			<input type="radio" name="size" value="4">
			3cm x 4cm
		</label>
		<br>
		<label>
			<input type="radio" name="size" value="5">
			2.5cm x 3.5cm
		</label>
		<br><br>
		<input type="file" id="file-input">
		<br><br>
		<button type="button" onclick="createPhoto()">制作证件照</button>
	</form>

	<!-- 证件照预览区域 -->
	<div id="preview"></div>

	<!-- JavaScript代码 -->
	<script>
		// 获取规格尺寸选择表单元素
		const sizeForm = document.querySelector('form');
		// 获取文件输入框元素
		const fileInput = document.getElementById('file-input');
		// 获取证件照预览区域元素
		const previewArea = document.getElementById('preview');

		// 创建证件照函数
		function createPhoto() {
			// 获取选中的规格尺寸
			const selectedSize = sizeForm.querySelector('input:checked').value;
			// 获取选择的文件
			const file = fileInput.files[0];

			// 检查是否选择了文件
			if (!file) {
				alert('请先选择照片文件');
				return;
			}

			// 创建图片元素
			const img = document.createElement('img');
			img.src = URL.createObjectURL(file);

			// 根据选择的规格尺寸设置图片大小
			switch (selectedSize) {
				case '1':
					img.width = 413;
					img.height = 531;
					break;
				case '2':
					img.width = 472;
					img.height = 590;
					break;
				case '3':
					img.width = 590;
					img.height = 590;
					break;
				case '4':
					img.width = 354;
					img.height = 472;
					break;
				case '5':
					img.width = 295;
					img.height = 413;
					break;
			}

			// 显示证件照预览
			previewArea.innerHTML = '';
			previewArea.appendChild(img);
		}
	</script>
</body>
</html>
