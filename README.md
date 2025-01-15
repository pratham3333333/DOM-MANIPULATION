# DOM-MANIPULATION


# JavaScript DOM Manipulation with Examples ✨

This repository demonstrates various JavaScript DOM manipulation techniques with simple examples. The examples cover several important DOM methods and properties such as `querySelector`, `previousSibling`, `nextSibling`, `previousElementSibling`, `nextElementSibling`, and others.

## Table of Contents 📝
1. **Introduction to DOM Manipulation**
2. **Selecting DOM Elements**
3. **Changing DOM Elements**
4. **Adding, Removing and Replacing Elements**
5. **Event Bubbling**
6. **DOM Properties and Methods**
7. **To-Do List Example**
8. **Interview Questions & Answers**

---

## 1. Introduction to DOM Manipulation 📚

The **Document Object Model (DOM)** is a programming interface for HTML and XML documents. JavaScript can be used to manipulate this structure, making dynamic changes to a webpage.

---

## 2. Selecting DOM Elements 👨‍💻

In JavaScript, the most common way to select elements in the DOM is by using methods such as `document.querySelector`, `document.getElementById`, and `document.getElementsByClassName`.

### Example Code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM Manipulation Example</title>
</head>
<body>
    <div id="container">
        <p id="text">Hello, world!</p>
    </div>
    <script>
        // Selecting elements
        const container = document.getElementById('container');
        const text = document.getElementById('text');
    </script>
</body>
</html>
```

---

## 3. Changing DOM Elements 🔧

You can use properties like `innerText`, `innerHTML`, `textContent`, and others to change the content or structure of DOM elements.

### Example Code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Changing DOM Elements</title>
</head>
<body>
    <div class="container">
        <p class="content">This is some text.</p>
    </div>
    <script>
        const content = document.querySelector('.content');
        // Change content using innerText
        content.innerText = "Updated text using innerText";
    </script>
</body>
</html>
```

---

## 4. Adding, Removing, and Replacing Elements ➕➖

You can manipulate the DOM by adding, removing, or replacing elements using methods such as `append()`, `prepend()`, `replaceWith()`, etc.

### Example Code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Replace Elements Example</title>
</head>
<body>
    <div id="container">
        <p id="original">This is the original paragraph.</p>
    </div>
    <button id="replace">Replace</button>
    <script>
        const originalParagraph = document.getElementById('original');
        const replaceButton = document.getElementById('replace');
        
        replaceButton.addEventListener('click', () => {
            const newParagraph = document.createElement('p');
            newParagraph.textContent = "This paragraph has replaced the original one.";
            originalParagraph.replaceWith(newParagraph);
        });
    </script>
</body>
</html>
```

---

## 5. Event Bubbling ⚡

Event bubbling is when an event propagates from the innermost element to the outermost one, triggering all handlers along the way.

### Example Code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Bubbling</title>
</head>
<body>
    <div class="container">
        Parent Div
        <div class="child">
            Child Div
            <button class="button">Click Me</button>
        </div>
    </div>
    <script>
        const parentDiv = document.querySelector('.container');
        const childDiv = document.querySelector('.child');
        const button = document.querySelector('.button');
        
        parentDiv.addEventListener('click', () => {
            alert('Parent Div Clicked');
        });

        childDiv.addEventListener('click', (e) => {
            alert('Child Div Clicked');
            e.stopPropagation();
        });

        button.addEventListener('click', (e) => {
            alert('Button Clicked');
            e.stopPropagation();
        });
    </script>
</body>
</html>
```

---

## 6. DOM Properties and Methods 🔍

### `querySelector()`, `previousSibling`, `nextSibling`, `previousElementSibling`, `nextElementSibling`:

These methods allow you to traverse the DOM to access elements relative to a given element.

### Example Code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM Traversing Example</title>
</head>
<body>
    <div class="container">
        <p>This is the first paragraph.</p>
        <p>This is the second paragraph.</p>
    </div>
    <script>
        const container = document.querySelector('.container');
        
        const firstParagraph = container.firstElementChild;
        const nextSibling = firstParagraph.nextElementSibling;
        const prevSibling = nextSibling.previousElementSibling;

        console.log("First Paragraph:", firstParagraph);
        console.log("Next Sibling:", nextSibling);
        console.log("Previous Sibling:", prevSibling);
    </script>
</body>
</html>
```

---

## 7. To-Do List Example 📝

This example demonstrates how to create a simple to-do list with a feature to delete tasks.

### Example Code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
</head>
<body>
    <div class="container">
        <h2>To-Do List</h2>
        <input type="text" id="itemInput" placeholder="Type something...">
        <button onclick="add()">Add to Wishlist</button>
        <div class="itemlist"></div>
    </div>
    <script>
        let Input = document.getElementById("itemInput");
        let text = document.querySelector(".itemlist");

        function add() {
            if (Input.value == "") {
                alert("enter the task");
            } else {
                let newElement = document.createElement("li");
                newElement.innerHTML = `${Input.value} <i>click to delete</i>`;
                text.appendChild(newElement);
                Input.value = "";

                newElement.querySelector("i").addEventListener("click", remove);
                
                function remove() {
                    newElement.remove();
                }
            }
        }
    </script>
</body>
</html>
```

---

## 8. Interview Questions & Answers 🧠

### Q1: What is the difference between `previousSibling` and `previousElementSibling`?

**Answer:**  
- `previousSibling` returns the previous node in the DOM tree, which can be a text node or an element.
- `previousElementSibling` returns the previous sibling element (ignoring text or comment nodes).

### Q2: How do you prevent an event from bubbling?

**Answer:**  
Use `e.stopPropagation()` inside the event listener function.

### Q3: Explain the difference between `innerHTML` and `textContent`.

**Answer:**  
- `innerHTML` returns or sets the HTML content, including HTML tags.
- `textContent` returns or sets the text content, without any HTML tags.

---


---

### 1. **What is the DOM?**
   **Answer:** The DOM represents the document structure, allowing programs to interact with HTML or XML documents.

### 2. **What is the difference between `innerHTML` and `textContent`?**
   ```html
   <div id="example"></div>

   <script>
     const div = document.getElementById('example');
     div.innerHTML = '<p>This is <b>HTML</b> content</p>';
     console.log(div.innerHTML); // <p>This is <b>HTML</b> content</p>
     console.log(div.textContent); // This is HTML content
   </script>
   ```

### 3. **What is the use of `document.getElementById()`?**
   ```html
   <div id="myDiv">Hello, World!</div>
   <script>
     const element = document.getElementById('myDiv');
     console.log(element.textContent); // Hello, World!
   </script>
   ```

### 4. **What is the difference between `getElementById()` and `querySelector()`?**
   ```html
   <div id="uniqueId">Hello</div>
   <div class="class">Hello</div>

   <script>
     const idElement = document.getElementById('uniqueId');
     const classElement = document.querySelector('.class');
     console.log(idElement.textContent); // Hello
     console.log(classElement.textContent); // Hello
   </script>
   ```

### 5. **What is an event in the context of the DOM?**
   ```html
   <button id="clickBtn">Click Me</button>
   <script>
     const button = document.getElementById('clickBtn');
     button.addEventListener('click', function() {
       alert('Button clicked!');
     });
   </script>
   ```

### 6. **What is event delegation?**
   ```html
   <ul id="list">
     <li>Item 1</li>
     <li>Item 2</li>
     <li>Item 3</li>
   </ul>

   <script>
     const list = document.getElementById('list');
     list.addEventListener('click', function(event) {
       if (event.target.tagName === 'LI') {
         alert('You clicked on ' + event.target.textContent);
       }
     });
   </script>
   ```

### 7. **What does `event.stopPropagation()` do?**
   ```html
   <div id="parent">
     <button id="child">Click Me</button>
   </div>

   <script>
     const parent = document.getElementById('parent');
     const child = document.getElementById('child');
     
     parent.addEventListener('click', () => alert('Parent clicked!'));
     child.addEventListener('click', (event) => {
       alert('Child clicked!');
       event.stopPropagation();
     });
   </script>
   ```

### 8. **What does `event.preventDefault()` do?**
   ```html
   <a href="https://example.com" id="link">Go to Example</a>

   <script>
     const link = document.getElementById('link');
     link.addEventListener('click', (event) => {
       event.preventDefault();
       alert('Link click prevented!');
     });
   </script>
   ```

### 9. **What is the `document.createElement()` method used for?**
   ```html
   <script>
     const newDiv = document.createElement('div');
     newDiv.textContent = 'This is a new div';
     document.body.appendChild(newDiv);
   </script>
   ```

### 10. **What does `appendChild()` method do?**
   ```html
   <div id="container"></div>
   <script>
     const div = document.createElement('div');
     div.textContent = 'Appended Child';
     document.getElementById('container').appendChild(div);
   </script>
   ```

### 11. **What does `removeChild()` do?**
   ```html
   <div id="parent">
     <p id="child">This is a child paragraph</p>
   </div>

   <script>
     const parent = document.getElementById('parent');
     const child = document.getElementById('child');
     parent.removeChild(child);
   </script>
   ```

### 12. **What are `firstChild` and `firstElementChild`?**
   ```html
   <div id="parent">
     Text Node
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const parent = document.getElementById('parent');
     console.log(parent.firstChild); // Text Node (whitespace)
     console.log(parent.firstElementChild); // <p>Paragraph 1</p>
   </script>
   ```

### 13. **What are `lastChild` and `lastElementChild`?**
   ```html
   <div id="parent">
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const parent = document.getElementById('parent');
     console.log(parent.lastChild); // Text Node (whitespace)
     console.log(parent.lastElementChild); // <p>Paragraph 2</p>
   </script>
   ```

### 14. **What is the `childNodes` property?**
   ```html
   <div id="parent">
     Text Node
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const parent = document.getElementById('parent');
     console.log(parent.childNodes); // NodeList of all child nodes (including text nodes)
   </script>
   ```

### 15. **What is the `children` property?**
   ```html
   <div id="parent">
     Text Node
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const parent = document.getElementById('parent');
     console.log(parent.children); // HTMLCollection of child elements (excludes text nodes)
   </script>
   ```

### 16. **What does `parentNode` do?**
   ```html
   <div id="child">I am a child</div>

   <script>
     const child = document.getElementById('child');
     console.log(child.parentNode); // The parent element of the child div
   </script>
   ```

### 17. **What is `nextSibling`?**
   ```html
   <div>
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const firstP = document.querySelector('p');
     console.log(firstP.nextSibling); // Returns the next sibling node, which may be text
   </script>
   ```

### 18. **What is `previousSibling`?**
   ```html
   <div>
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const secondP = document.querySelectorAll('p')[1];
     console.log(secondP.previousSibling); // Returns the previous sibling node, which may be text
   </script>
   ```

### 19. **What is `nextElementSibling`?**
   ```html
   <div>
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const firstP = document.querySelector('p');
     console.log(firstP.nextElementSibling); // <p>Paragraph 2</p>
   </script>
   ```

### 20. **What is `previousElementSibling`?**
   ```html
   <div>
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const secondP = document.querySelectorAll('p')[1];
     console.log(secondP.previousElementSibling); // <p>Paragraph 1</p>
   </script>
   ```

### 21. **What does `querySelectorAll()` do?**
   ```html
   <div class="item">Item 1</div>
   <div class="item">Item 2</div>

   <script>
     const items = document.querySelectorAll('.item');
     console.log(items); // NodeList of all elements with class 'item'
   </script>
   ```

### 22. **What is `setAttribute()` used for?**
   ```html
   <img id="image" src="image.jpg" alt="Image">

   <script>
     const image = document.getElementById('image');
     image.setAttribute('src', 'new-image.jpg');
   </script>
   ```

### 23. **What is `getAttribute()` used for?**
   ```html
   <img id="image" src="image.jpg" alt="Image">

   <script>
     const image = document.getElementById('image');
     console.log(image.getAttribute('src')); // image.jpg
   </script>
   ```

### 24. **What is `removeAttribute()` used for?**
   ```html
   <img id="image" src="image.jpg" alt="Image">

   <script>
     const image = document.getElementById('image');
     image.removeAttribute('alt');
   </script>
   ```

### 25. **What is `createTextNode()`?**
   ```html
   <script>
     const text = document.createTextNode('This is some text');
     document.body.appendChild(text);
   </script>
   ```

### 26. **What is the purpose of `document.querySelector()`?**
   ```html
   <div id="uniqueDiv">Hello</div>

   <script>
     const element = document.querySelector('#uniqueDiv');
     console.log(element.textContent); // Hello
   </script>
   ```

### 27. **What is the `hidden` attribute in the DOM?**
   ```html
   <div id="hiddenElement" hidden>This is hidden</div>

   <script>
     const div = document.getElementById('hiddenElement');
     div.hidden = false; // Makes the element visible
   </script>
   ```

### 28. **What does `insertBefore()` do?**
   ```html
   <div id="parent">
     <p>Paragraph 1</p>
     <p>Paragraph 2</p>
   </div>

   <script>
     const newP = document.createElement('p');
     newP.textContent = 'Inserted Paragraph';
     const parent = document.getElementById('parent');
     parent.insertBefore(newP, parent.firstChild);
   </script>
   ```

### 29. **What is the `cloneNode()` method?**
   ```html
   <div id="original">
     <p>Original content</p>
   </div>

   <script>
     const original = document.getElementById('original');
     const clone = original.cloneNode(true);
     document.body.appendChild(clone); // Clone with child elements
   </script>
   ```

### 30. **What is `document.designMode` used for?**
   ```html
   <script>
     document.designMode = 'on'; // Turns on content-editable mode for the document
   </script>
   ```

---

