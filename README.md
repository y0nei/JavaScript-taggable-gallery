# Extensible Plain JS gallery with Jquery example

This is one of my old projects that i have decided to release to the public \
The JavaScript loads files from a directory, tags them and displays them to the website allowing easy extensibility for large amount of files \
There is a [plain js example](plain.js) or [jquery example](jquery.js) if thats your cup of tea

## How does this work?
First it gets all the loaded elements from the `baseDir` directory
```js
var elements = xhr.response.getElementsByTagName("a");
```
Then it matches file extensions of your choice and creates html elements to contain all of them
```js
if (x.href.match(/\.(jpg)$/)) {
    ...
}
```
The JS script searches for strings in the file names of those images and matches them to the `datatypes` list
```js
var datatypes = ["landscape", "flower", "pet", "cat", "dog"]
```
if a match is found, it adds the coresponding class to div containing the image
```js
for (var i of datatypes)
    if (x.href.indexOf(i) > -1) {
        imagebox.classList.toggle(i, true)
        console.log(imagebox.classList); // Log DOMTolenList
}
```
<b><i>note: all of those have an `imagebox` class to allow viewing all of them </i></b> \
Finally it displays those elements containing the value in the `datatypes` list after selecting a category in the navbar
```js
document.querySelectorAll('.list').forEach(list => {
    list.addEventListener('click', e => {
        const value = e.target.dataset.filter; // Target
        document.querySelectorAll('.imagebox').forEach(imagebox => {
            // If All is selected, just display all of those elements
            if (value == 'All') {
            imagebox.style.display = 'block'
            } else {
            imagebox.style.display = imagebox.classList.contains(value) ? 'block' : 'none';
            }
        });
        ...
    });
});
```
Finally Adds/Removes the `.active` class on selected category
```js
...
        e.target.classList.add('active');
        Array.from(e.target.parentNode.children).forEach(sibling => {
            if (sibling != e.target) {
            sibling.classList.remove('active');
            }
        });
```
***
<p align="center">
  <a href="https://ko-fi.com/zimmy4"><img src="https://ko-fi.com/img/githubbutton_sm.svg" alt="Ko-Fi" /></a>
</p>