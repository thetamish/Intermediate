##Getting Started

Go to the [Beginner Project](https://github.com/CreatingChange/Beginner) and click on the "Download ZIP" button in the right hand column. Navigate to where your computer has downloaded this file.

Double click on the downloaded "Beginner-master" Zip file so that it will unzip, then move that folder into a location where you want to store your project. I have a folder I call "Code". You also may want to rename the "Beginner-master" folder to reflect the name of the website you're working on today.

Next we need a program to edit text. Download [Sublime](www.sublimetext.com) and open it. There are many text editors available; this is just one that we like.

Run Sublime, select the "open" menu option, select your project folder ("Beginner-master" or whatever you renamed it), and select "open". You should see the Beginner-master folder, which includes several folders and files.

Continue by [downloading JQuery](http://jquery.com/download/) and choose the uncompressed, development version, 1.11.2. This should download to the same place the project did.

Create a few folder inside your project folder called `js` and put your newly downloaded JQuery file in that folder. While you're there, create a new, empty file called `scripts.js`. This is where all of your Javascript and JQuery will go.

Finally, open index.html in your browser and check out the simple website that the Beginner group is creating. We will be taking it to the next level by adding interactivity.


##Embedding Twitter Feed

Your personal or organization twitter feed is a really good way to share all the latest relevant news. It's pretty easy to embed this information into your website.  Below is a short tutorial how to access that information.

Go to your orgs/personal twitter page. Make sure you are logged in. Click your avatar at the top of the page. Navigate to "Settings" in the dropdown menu. Then on the left side of the page, in the list find "Widgets". Create a New widget. This is where you will manage what your twitter feed will look like on any specific site.  Once your widget it created. There will be a few lines of code under the feed preview.  All you have to do is copy and paste this code into your site. And now your twitter feed is live for all of your people to see.

##What is Javascript?
Javascript is a programming language that's built-in to web browsers. It enables a user to interact with a website (and vice versa). In Javascript, you can do all kinds of basic programming logic, like loops and if statements. While incredibly fun and interesting, that kind of programming logic is a bit harder to find a practical use for when building a simple website. That's why today we'll be focusing on the interactive potential of Javascript using JQuery, a Javascript library that makes it easier to use. If you want to learn more about Javascript as a programming language, there are many online resources available, including [Code Academy](http://www.codecademy.com/en/tracks/javascript).

The first thing we're going to do is prepare our scripts.js file. We need to tell it to run our Javascript code only after the HTML has been read and the page is ready to be manipulated by user interaction. So all of the Javascript we'll be writing in this lesson will be within this function in scripts.js.

```javascript
$(document).ready(function() {

});
```

If you'd like to learn more about why we need this, [JQuery has documentation](http://learn.jquery.com/using-jquery-core/document-ready/) that tells us that the function will be run when the [Document Object Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction) is ready.

##Writing Code

Open your `index.html` file in Sublime and put the following HTML right inside `<head>` tags. Don't copy and paste any of the code on this tutorial. Typing it out for yourself will significantly increase your learning.

```html
<script src="js/jquery-1.11.2.js"></script>
<script src="js/scripts.js"></script>
```

These tell our HTML where to find the javascript resources we're going to provide both from our code and JQuery. It's important that our own `scripts.js` file goes after jQuery, as it will rely on jQuery functionality that must be loaded first.

Now open your `scripts.js` file in Sublime as well.

Let's use some JQuery to interact with an image element on our page. Elements like `<img>` tags can have attributes assigned to them through class and id values. These let us locate a specific element and use Javascript and JQuery to interact with them. In index.html, note that all 6 of the images hava a class of "image_1". We can then reference that class when we're writing our Javascript code.

Inside your `scripts.js` file now add this bit within the document ready function:

```javascript
$(document).ready(function() {
    $(".image_1").click(function() {

    });
});
```

If we break this down there are several parts to even this small bit of code. `$(".image_1")` means that using JQuery we're going to look for an interaction with any page element with a class of "image_1". The `$` is simply a much shorter way of saying `jQuery` which you'll be seeing a lot in this lesson.

When locating or styling elements a period is used for classes and a pound sign (hash) is used for ids. Classes can be used over and over again on many different elements in one page. Ids are expected to be unique.

The next section, the `.click(function()` section says what specific action to listen for. In this case we're looking for the cursor to click on an element but many different options exist including:

<ul>
    <li>.hover()</li>
    <li>.dblclick()</li>
    <li>.show()</li>
    <li>.focus()</li>
    <li>.keypress()</li>
</ul>

I bet you already have some idea what a lot of those do!

The empty line between the `{` and the `}` is where we'll be placing the code that tells our site *what* to do when it "hears" the even happen. These collectively are called *Event Listeners* or *Event Handlers*.

When a user clicks on one of the 6 images, we're going to make the top row of images disappear. In order to do that, let's assign just the top row of images on the page to a class called "hide_this".

```html
<div class="row">
    <div class="hide_this">
        <img class="image_1" src="img/rsz_image_1.jpg" alt="Are you a boy or girl? No.">
        <img class="image_1" src="img/rsz_image_1.jpg" alt="Are you a boy or girl? No.">
    </div>
</div>
```

Now that we have the "hide_this" class we can use, let's add an event listener.

```javascript
$(".image_1").click(function() {
    $(".hide_this").hide();
});
```

Check it out in the browser!

##Complete the Functionality

Now let's create some content that we want to appear when we click the top left hand image. Let's get a replacement image. On the top of this page (by README.md), save rsz_trans_symbol.jpg by right-clicking it and downloading it. Save it in your img folder.

Go back to your `index.html` file and place everything inside of the `<div id=click_image>` and `</div>` tags where you see it in the code snippet below.

```html
<div class="col-md-6">
    <div class="row">
        <div class="hide_this">
            <img class="image_1" src="img/rsz_image_1.jpg" alt="Are you a boy or girl? No.">
            <img class="image_1" src="img/rsz_image_1.jpg" alt="Are you a boy or girl? No.">
        </div>
        <div id="click_image">
            <img class="image_2" src="img/rsz_trans_symbol.jpg" alt="Trans Symbol">
            <img class="image_1" src="img/rsz_image_1.jpg" alt="Are you a boy or girl? No.">
        </div>
    </div>
```

Now let's update scripts.js to include a bit about showing the replacement row of images.

```javascript
$(".image_1").click(function() {
    $(".hide_this").hide();
    $("#click_image").show();
});
```

Remember that the hash is used in front of "click_image" because "click_image" is an ID, not a class. With your partner, see if you can talk through step-by-step what's going on when the page loads and an image is clicked on.

Additionally, we need to ensure that the bit of HTML that will be shown isn't initially. To do that, go to your `styles.css` and add the following:

```css
#click_image {
    display: none;
}
```

##More JQuery Functions

You might have noticed by now that, while you can click to make the hidden image replace the original, clicking again will not swap them back. This is a relatively simple matter of reversing our JQuery. We have all the infrastructure we need in the tags, classes, and ids that we need in our HTML already. Place this `.click()` in its place on the `scripts.js` page immediately following the previous code you wrote, but still wrapped within the document ready function.

```javascript
$("#click_image").click(function() {
    $(".hide_this").show();
    $("#click_image").hide();
});
```
This should be all that's required to impliment the "return click" functionality that was previously lacking. Now when a user clicks an image, the replacement top row will appear. If they click the top row of images again, it will go back to the original images.


##Adjust the Font Size on the Fly

Let's examine an example of how you might use this new knowledge to increase user access. It's not uncommon for web designers to spend very little time thinking about the design choices they've made and how that might impact users of different ability levels. One very basic example might be using an extrordinarily small font size. We can add the ability to adjust the font size on the fly with JQuery.

First, let's physically add the buttons to our navbar. Find the section of the HTML just below:

```html
    <ul class="nav navbar-nav">
      <li class="active"><a href="index.html">Home</a></li>
      <li><a href="about.html">About</a></li>
      <li><a href="contact.html">Contact</a></li>
    </ul>
</div>
```
Once you've found it, at the end of it, insert this bit of HTML. (It should still be within the `<div class="container-fluid"` but outside of `div class="navbar-header"`). We're adding some text and two butons, one labeled with a minus and the other with a plus.

```html
<div class="navbar-right font-adjust">
    <p class="navbar-text">Adjust Font Size</p>
    <button type="button" class="btn btn-default navbar-btn">-</button>
    <button type="button" class="btn btn-default navbar-btn">+</button>
</div>
```
What we're doing here is adding two buttons to increase and decrease font size respectively. They don't function yet, that's what the JQuery will be doing. We've wrapped both these buttons in a separate `<div>` tag so that we can push them to the right inside the navbar as a whole. `class="navbar-right"` is something bootstrap gives us. `font-size` is a class we've added on our own to hook the JQuery into in a moment.

###Button Styling

The `<p>` tag right after the above `<div>` is simply a label for our buttons so users know what they're for. Once again, the class that's attached is simply a preexisting bootstrap class that ensures our text is styled consistently with the rest of the navbar.

If you look at the live version of your page at the moment, you'll see that your second button is hugged right up against the far right side of the navabar. Let's fix that quickly. Go into your `styles.css` file and add the code below:

```css
.font-adjust {
    margin-right: 10px;
}
```

###Button Functionality

Now let's add some actual JQuery functionality to our buttons. Like before, we'll need to grab onto some sort of class or id and then add the functionality. Let's add a click event whenever someone clicks on something with the class "font-adjust". That part is like before. Now when that happens and the code inside the function is run, instead of showing or hiding something, we're going to change the css style of all text within the container class. Let's change it to something really big, like 50 pixels.

```javascript
$(".font-adjust").click(function() {
    $(".container").css("font-size", "50px");
});
```
Wow! Much bigger.

###Making It Relatively Bigger

So what if just we want the text to get bigger than it was before, not uniformly huge?

Instead of making everything 50 pixels, we need a way to reference the font size of each thing in the container and increase it slightly. We need to write a function.

First we want to get the font size of each item in the container. The way we refer to "each item" in this case is using `this`. We'll get the font size of each item like so: `$(this).css("font-size")`, which will give us a string.

The `.css()` function, like `.show()` and `.hide()` allow us to alter something; in this case the value of a css selector. We're telling it to alter the `font-size` selector that we had previously added to `styles.css`.

What's a string? Let's take a little detour here. Javascript holds data in a few different ways. We'll be using [strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) and integers today. A string holds data in text form. Here are some strings: "hello world", "Creating Change is awesome!", "42". Here are some integers: 4, 8, 15, 16, 23, 42. Notice that 42 can be written as a string or as an integer. But standard operations like addition, subtraction, and multiplication only have meaning when applied to 42 as an integer. If you try to "add" two strings (or a string and an integer), then they just get concatenated (joined together end-to-end). For example, if you added together two integers like 5 + 3, you get 8. But if you "add" together the two strings "5" + "3", you get "53".

Ok, so we know how to get the font size of each thing in the container, but it's a string. We need to turn it into an integer so that we can add 1 to it and make it larger. We can use [parseInt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt) to turn whatever that string is into an integer. So now we've got `parseInt($(this).css("font-size"))` and we can add 1 to it.

We are getting so close. So now we have a new font size as an integer that we want to apply. It has to take the same form as when we used "50px" (a string), so we have a little more manipulation to do. Let's concatenate our number with "px" and send it off to be applied as a new font-size.

```javascript
$(".font-adjust").click(function() {
    $(".container").css("font-size", function() {
        return parseInt($(this).css('font-size')) + 1 + 'px';
    });
});
```

We need the word "return" to complete the computation and send the resulting value.

Now if you reload your page you'll see that our "plus" button will increase the font size on the entire page! The problem you'll run into if you poke around for a minute is that the "minus" button doesn't work. It increases font size too! Before we fix that, see if you or your partner can explain why that's happening.

###Button Differentiation

Go ahead and change the `font-size` classes on your buttons to what you see below.

```html
<button type="button" class="btn btn-default navbar-btn font-size-down">-</button>
<button type="button" class="btn btn-default navbar-btn font-size-up">+</button>
```
Because we need each button to do something different, we'll need a different bit of JQuery for each button. Edit your most recent JQuery code in the `scripts.js` file to hook onto `.font-size-up` instead of `.font-adjust`. We'll be doing something very similar for `.font-size-down` so copy that code and paste it right before the final closing brace in `scripts.js`. We'll need to change just a couple of things so it looks like this.

```javascript
$(".font-size-down").click(function() {
    $(".container").css("font-size", function() {
        return parseInt($(this).css('font-size')) - 1 + 'px';
    });
});
```
You'll notice that this bit hooks into the `.font-size-down` class that you added just a few minutes ago to the `index.html` file. Finally, the line that returns the changed number of pixels for the font size needs to now subtract one pixel instead of add one so that our button will decrease the page's font size.

Potentially add more content here!

##Conclusions

We hope at this point that it's clear what relatively simple javascript/JQuery functions can do for your basic web page. They have the potential to add all kinds of functionality as well as address increasingly complex web accessibility issues. You'll find resources to continue adding to your web knowledge below. Feel free to use them or ask us a few questions at the end of the presentation.

##Taking Action

Coding and web applications have a lot to offer to social justice movements in terms of tools. Let's figure out how to make it easy for an ally to contact their US Senators about our issues.

In your `index.html` file, find where all the navbar links are created in their `<li>` tags and add one more.

```html
<li><a href="take_action.html">Take Action</a></li>
```

Now create a `take_action.html` file the same directory as `about.html`, `contact.html`, and `index.html`.

Into that `take_action.html` file, copy this:

```html
<html lang="en">
  <head>
      <title>Creating Change Website</title>
      <link rel="stylesheet" href="css/bootstrap.css">
      <link rel="stylesheet" href="css/styles.css">
      <script src="../js/jquery-1.11.2.js"></script>
      <script src="../js/scripts.js"></script>
  </head>
  <body>
    <div class="container">
      <nav class="navbar navbar-default">
        <div class="container-fluid">
          <div class="navbar-header">
            <!-- <a class="navbar-brand">Logo goes here</a> -->
            <ul class="nav navbar-nav">
                <li class="active"><a href="index.html">Home</a></li>
                <li><a href="about.html">About</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
          </div>
          <div class="navbar-right font-adjust">
            <p class="navbar-text">Adjust Font Size</p>
            <button type="button" class="btn btn-default navbar-btn font-size-down">-</button>
            <button type="button" class="btn btn-default navbar-btn font-size-up">+</button>
          </div>
        </div>
      </nav>
      <p>Our cause is great and important! We need your help to convince your representatives to care about our cause too and use the institutional power of --Insert Government Here-- to affect change. Fill out the form below and you'll be redirected to a letter we'll email on your behalf to your representatives.</p>
    </div>
  </body>
</html>
```

This is all the structural html from the index page. We've helpfully cut out all the images, text, the header link to this page, ensured that the indentation is clean, and added a text message for users with a `<p>` tag. Into this page we're going to add some forms. Forms are used all over the web from logins to profile pages to address forms. They're a basic component of web development. When building a form in just HMTL you'll use the `<input>` tag.

##Building the Forms

A proper input tag will have a few components. Here's what ours will look like:

```html
<form>
  <div class="form-group">
    <input type="text" class="form-control" name="name" id="name" value="Name">
  </div>
  <div class="form-group">
    <input type="text" class="form-control" name="state-code" id="state-code" value="State Abbv.">
  </div>
  <div class="form-group">
    <input class="btn btn-default mail form-control" type="submit" name="submit" value="Submit">
  </div>
</form>
```
There are a few things worth talking about here. The first is that it's a good idea to wrap your `<input>` tags inside a `<form>` tag. This is one place you can add a class or id to help you style just these forms.

In addition, you've noticed that any indivitual `<input>` tag has a few values associated with it. The type is required. "Text" is used for text fields, "submit" for your actual submission buttons, and there are other useful ones out there. the name and id should generally match and be something specific. Something like "form3" is generally not useful because these are often used as hooks to do other, more complicated things with forms on a page and need to be easily identified. Finally, the value is the literal text that will appear as a placeholder in the text box.

##Form Styling

The `<div>` elements, `<form>` element, and the classes, both on the div and the input tags themselves are used for styling by bootstrap. They have predefined styles for both "form-group" and "form-control" so that individual forms receive reasonable spacing, etc. The one thing that we should know is that anything styled with bootstrap's "form-group" class will receive the CSS style `width: 100%`. There are a number of ways to fix this. The easiest (and worst) of the options would be to overrride bootstrap's definition of "form-group" and force it to be a width like 30% in our `styles.css` file. This is less than ideal  for a number of reasons, one of which is that that will effect everything on every page in your project that usess that fairly common boostrap class. Instead we'll be a little tricky and redefine what counts as "width:100%"" for these form items. Add `class="col-md-4 class-col-md-offset-4" to the form tag.

What this does is that it limits the space that the forms see within bootstrap's grid.


##Bootstrap and the Grid

Check out the grid system in [Bootstrap's own words](http://getbootstrap.com/2.3.2/scaffolding.html#fluidGridSystem)

As you can tell, the system is based on 12 columns so it's not uncommon to see classes like the one above calling for an element to take a certain number of columns as its own space. This lets you accurately place elements side by side, above and below one another, etc. The "col-md-offset-4" says to leave 4 columns before placing this four column sized element, definied by "col-md-4", onto the page, resullting in forms that are centered.

You can and should use "col-lg-x", "col-sm-x" etc. when working on large projects to remain responsive and have the ability to define how your project looks on different screen sizes. Boostrap itself has info about what qualifies as small, medium, large, etc. For now, we'll stick to medium for the sake of time.


##Contact your senator!

In this section we are going write the code that will allow a person to enter their state abbreviation and find their senator.

This function 




