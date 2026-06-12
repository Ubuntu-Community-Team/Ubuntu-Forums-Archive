---
title: "Faulty Firefox 3 CSS rendering(no it's not the fonts)"
date: 2008-08-03
forum: General Help
---

### Post by offline on 2008-08-03
I am reading a book about CSS and following the examples it provides. Unfortunately, Houston, we have a problem in ubuntu version of FF3 CSS handling.

My ubuntu version is 8.04. I attach "the evidence" material regarding rendering of:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
     <head>
        <style type="text/css">
            * {
                font-family: sans-serif;
                color: white;
            }

            /**
             * Apply this style to all h1 elements regardless of where they
             * appear in the page.
             **
            */

            h1, form h2 {
                background: gray;
            }

            h1, h2, form {
                margin: 0;
            }

            h1 {
                font-size: 24px;
                padding: 5px;
                border-bottom: 5px solid black;
                letter-spacing: -2px;
                width: 510px;
                -moz-border-radius-topleft: 10px;
                -moz-border-radius-topright: 10px;
            }

            form {
                background: lightgrey;
                padding: 10px;
                width: 500px;
                -moz-border-radius-bottomleft: 10px;
                -moz-border-radius-bottomright: 10px;
            }

            /**
             * Apply these styles to label elements, but only if they
             * appear inside of an input form
             **
            */

            form label {
                display: block;
                font-weight: bold;
                margin: 5px;
                width: 225px;
                text-align: right;
                background: black;
            }

            /**
             * These styles are shared between h2 and label elements
             * that appear inside of a form
             **
            */

            form h2, form label {
                font-size: 15px;
                -moz-border-radius: 10px;
                padding: 3px;
            }
            
            /**
             * Direct Child Selectors
             **
            */
            
            form > div > label {
                float: left;
            }
            form > div {
                clear: left;
            }
            div > input, div > select {
                margin: 3px;
                padding: 4px;
            }
            select > option {
                padding: 4px;
            }
            /**
             * Direct Adjacent Sibling Combinators
             **
            */

            label + input, label + select, label + textarea {
                background: darkgray;
            }
            
            /**
             * Attribute Selectors
             **
            */
    
            option[value] {
                letter-spacing: 2px;    
            }
            option[value='newspaper'] {
                background: orange;    
            }
            option[value='magazine'] {
                background: red;
            }
            option[value='television'] {
                background: black;
            }
            option[value='radio'] {
                background: green;
            }
            option[value='other'] {
                background: blue;
            }
            input[name$='[name]'] {
                color: darkred;
            }
            input[name$='[email]'] {
                color: darkblue;
            }
            textarea[name$='[address]'] {
                color: purple;
            }
            textarea[name$='[message]'] {
                color: black;
            }
            select[name$='[heard]'] {
                color: darkgreen;
            }
            input[name^='feedback'], select[name^='feedback'], textarea[name^='feedback'] {
                font-weight: bold;
            }
            /**
             * Class Selectors
             **
            */

            label.spanform {
                float: none;
                width: auto;
                text-align: left;
            }
            div.spanform {
                text-align: center; 
            }

            /**
             * ID Selectors
             **
            */
            
            div#buttons {
                text-align: right;                  
            }
            
            input#button {
                background: black;
                font-weight: bold;
                border: 1px solid white;    
            }
            div#copyright {
                margin-top: 10px;
                border-top: 1px dashed black;
                padding-top: 10px;
                font-size: 10px;
                text-align: center;
                color: black;
            }

        </style>
        <title>Feedback Form - Widgets and What's-its</title>
    </head>
    <body>
        <h1>Widgets and What's-its</h1>
        <form>
            <h2>Tell us what's on your mind..</h2>
            <div>
                <label for='feedback[name]'>Name:</label>
                <input type='text' size='25' name='feedback[name]' />
            </div>
            <div>
                <label for='feedback[email]'>Email:</label>
                <input type='text' size='25' name='feedback[email]' />
            </div>
            <div class='spanform'>
                <label for='feedback[address]' class='spanform'>Address:</label>
                <textarea name='feedback[address]' cols='40' rows='3' wrap='virtual'></textarea>
            </div>
            <div class='spanform'>
                <label for='feedback[message]' class='spanform'>Comments:</label>
                <textarea name='feedback[message]' cols='40' rows='6' wrap='virtual'></textarea>
            </div>
            <div>
                <label for='feedback[heard]'>How'd you hear about us?</label>           
                <select name='feedback[heard]'>
                    <option value=''>Choose...</option>
                    <option value='newspaper'>Newspaper</option>
                    <option value='magazine'>Magazine</option>
                    <option value='television'>Television</option>
                    <option value='radio'>Radio</option>
                    <option value='other'>Other</option>
                </select>
            </div>
            <div id='buttons'>
                <input type='submit' 
                       name='feedback[action]' value='Submit' id='button' />
            </div>
            <div id='copyright'>
                &copy; Copyright 2004 What's-its and Widgets, All Rights Reserved.            
            </div>
        </form>
    </body>
</html>

```

The FF3 portable behaves exactly like FF3 in windows. 

The book is Beginning CSS, from Wrox and there they provide the example code.

I think the problem is with the 'float', but don't ask me much I am just learning.

---

### Post by HyperHacker on 2008-08-03
Firefox problems should be reported to the Firefox developers, not here. As for your problem it looks like in Ubuntu the textboxes are bigger than the available width, so they wrap to the next line. Try specifying an exact width or size attribute (size takes # of characters).

Good luck, I've had trouble with floats before.

---

### Post by kostkon on 2008-08-03
Yes, it seems Firefox creates bigger text inputs and since you have set a specific width for the form (500px), they don't fit on this line and so they are forced to move below.

Try to set a smaller size for your inputs, now you have it to be 25 charactes. Set it for example to 20 and then set the *maxlength* attribute to 25. Thus, your inputs will have a smaller size but will still accept the same number of characters, i.e. 25.

Or you can make the width of the form a little bigger maybe.

Another thing is that it is not semantic to put divs or h2s inside a form, but this is another matter.

---

### Post by mb_webguy on 2008-08-03
Ok, first off, you're using malformed XHTML.  All attributes in XHTML must be enclosed in double quotes.  If your XHTML is malformed, FF goes into garbage mode and interprets the HTML as best it can, which isn't always how you think it should.

As for the alignment issues, the reason "Name" and "Email" are shifted to the right is because of the "text-align: right" property of the "form label" selector.  The "Address" and "Comments" labels are inside "spanform" divisions, which have the property "text-align: left".  The "How'd you hear about us?" label is not in a "spanform" division, so it's actually aligned to the right, but you can't tell because the text takes up the entire width of the label.

---

### Post by offline on 2008-08-03
Thanks for the replies. I believe either " or ' is valid in attribute values. The w3 validator(file upload) finds 8 mistakes but doesn't say a thing about quotes. The most important mistake is
"Line 2, Column 1: Missing xmlns attribute for element html. The value should be: http://www.w3.org/1999/xhtml"
There are many 
"character "[" is not allowed in the value of attribute "for" "
and 
"there is no attribute "wrap""
and some
reference to non-existent ID "feedback[xyz]"

But we are missing the point. As I mentioned, in the same ubuntu system, side by side, FIREFOX3 PORTABLE renders it nicely, Opera the same, safari the same. The one failing is ubuntu version of FF3

---

### Post by kostkon on 2008-08-03
> **offline said:**
> Thanks for the replies. I believe either " or ' is valid in attribute values. The w3 validator(file upload) finds 8 mistakes but doesn't say a thing about quotes. The most important mistake is
"Line 2, Column 1: Missing xmlns attribute for element html. The value should be: http://www.w3.org/1999/xhtml"
There are many 
"character "[" is not allowed in the value of attribute "for" "
and 
"there is no attribute "wrap""
and some
reference to non-existent ID "feedback[xyz]"

But we are missing the point. As I mentioned, in the same ubuntu system, side by side, FIREFOX3 PORTABLE renders it nicely, Opera the same, safari the same. The one failing is ubuntu version of FF3
It is a fact that your html is not perfect. To be sure that it is not a html rendering problem, it would be best if you could improve your code in order to make Firefox to render it in Standards compliance mode. Then after you manage that, even if then problem persists you'll know for sure that is not caused by Firefox rendering the page in quirks mode.

For example, you could change your code a little, like this:

```
<body>
        <h1>Widgets and What's-its</h1>
        <div>
            <h2>Tell us what's on your mind..</h2>
            <form>
                <label for="feedback[name]">Name:</label>
                <input type="text" size="25" name="feedback[name]" />

                <label for="feedback[email]">Email:</label>
                <input type="text" size="25" name="feedback[email]" />

                <label for="feedback[address]" class="spanform">Address:</label>
                <textarea name="feedback[address]" cols="40" rows="3"></textarea>

                <label for="feedback[message]" class="spanform">Comments:</label>
                <textarea name="feedback[message]" cols="40" rows="6"></textarea>

                <label for="feedback[heard]">How'd you hear about us?</label>           
                <select name="feedback[heard]">
                    <option value="">Choose...</option>
                    <option value="newspaper">Newspaper</option>
                    <option value="magazine">Magazine</option>
                    <option value="television">Television</option>
                    <option value="radio">Radio</option>
                    <option value="other">Other</option>
                </select>

                <input type="submit" 
                       name="feedback[action]" value="Submit" id="button" />
                </form>
            </div>
            <div id="copyright">
                &copy; Copyright 2004 What's-its and Widgets, All Rights Reserved.            
            </div>
    </body>
</html>
```
and change the CSS appropriately.

Also, you'll need to change your html tag to be like this
```
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
```

Also you don't need to have a strict DOCTYPE. You can loosen it up an little and use just transitional xhtml, i.e.
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

Also, I don't understand what is that wrap attribute you have in the textarea elements. It is not a valid one, for sure. I assume it's safe to remove it.

Nevertheless, maybe the problem is font related. You can easily see that the text input fields in Ubuntu's Firefox are bigger and they don't fit. Before explaining further, try for example setting a specific font size in pixels for the form or the container div. Don't worry, it will not change the size for the labels inside the form. The font size you have set for them will override the font size set for their container form/div.

---

