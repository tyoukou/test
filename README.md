<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>打开相册选择图片</title>
</head>
<body>
    <button onclick="openAlbum()">打开相册</button>
    <br>
    <img id="preview" style="max-width: 300px; display: none;" alt="图片预览">

    <script>
        function openAlbum() {
            const input = document.createElement('input');
            input.type = 'file';
            input.accept = 'image/*'; 
            input.style.display = 'none'; 

            input.onchange = (event) => {
                const file = event.target.files[0]; 
                if (file) {
                    const reader = new FileReader();
                    reader.onload = (e) => {
                        const img = document.getElementById('preview');
                        img.src = e.target.result; 
                        img.style.display = 'block'; 
                    };
                    reader.readAsDataURL(file);
                }
            };

            document.body.appendChild(input);
            input.click();
            document.body.removeChild(input); 
        }
    </script>
</body>
</html>
