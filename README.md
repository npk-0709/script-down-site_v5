# script-down-site_v5
```javascript
function downloadFile(url) {
    var xhr = new XMLHttpRequest();
    xhr.open('GET', url, true);
    xhr.responseType = 'blob';
    xhr.onload = function () {
        if (xhr.status === 200) {
            var url = window.URL.createObjectURL(xhr.response);
            var hiddenLink = document.createElement('a');
            hiddenLink.href = url;
            hiddenLink.setAttribute('download', '');
            document.body.appendChild(hiddenLink);
            hiddenLink.click();
            document.body.removeChild(hiddenLink);
        }
    };
    xhr.send();
}
var links = document.querySelectorAll('a');
links.forEach(function(link) {
    if (link.href && link.href.includes('DownloadFile.php?DownloadFile=full&code=')) {
        downloadFile(link.href);
    }
});
```
