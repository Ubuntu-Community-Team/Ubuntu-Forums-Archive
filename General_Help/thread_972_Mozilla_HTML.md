---
title: "Mozilla HTML"
date: 2004-10-17
forum: General Help
---

### Post by Infatuated_iPod on 2004-10-17
I know this isnt the Mozilla forum, but since most of you guys use mozilla, i have a question. Whenever i try to put a picture in my html it does not show up on mozilla, but does show up on internet explorer, same thing happened when i tried to change the background. What is the deal. Is there some sort of different html for mozilla?  Thanks.

---

### Post by HungSquirrel on 2004-10-17
Post the code between [****code][/****code] tags and perhaps we can help you.  But no, Gecko (Mozilla's HTML renderer) is supposed to render &lt;img&gt; tags the same way IE does.

---

### Post by jeremy on 2004-10-17
It sounds like you are doing it wrong, but because IE is less 'strict' about standards, it shows.

---

### Post by Infatuated_iPod on 2004-10-17
this is how i usually put images on IE, &lt;img src="img.jpg"&gt; is that wrong?

P.s...
the code thing didnt work.

---

### Post by jeremy on 2004-10-17
Your img tag looks fine.
The code thing does work, press the 'code' button. paste the code, then press the button again.

---

### Post by Infatuated_iPod on 2004-10-17
Where is the code button?

---

### Post by Rancoras on 2004-10-17
Just above where you type your replies.

---

### Post by Infatuated_iPod on 2004-10-17
No, haha, i think there is a mistake. I am trying to post an image on my webstite, it does not show up on Mozilla, i am using notpad to write the html. It works fine on IE but does not show up on Mozilla, same thing with some colors.

---

### Post by adbak on 2004-10-18
What Hung was trying to say was to post your html (your img tags specifically) on this thread using the code buttons to make it easy to read.  Hung just wants to proofread, I believe.

---

### Post by Infatuated_iPod on 2004-10-18
I am not asking about posting images on this foru, i am talkin about making a website using HTML, the images dont show up on Mozilla, but they show up fine on IE.

---

### Post by Rancoras on 2004-10-18
We all know what you are asking.  We want you to post the html code you are using here so we can proofread it for you.  You have to help us before we can help you.  

Press the code button above the box where you type your reply.
Paste your code from the html file after the code tag that appears.
Press the code button again and a closing tag will appear.
This way we can see if there is an error in your html code.

---

### Post by Infatuated_iPod on 2004-10-18
I already did that earlier in the post, 
 
&lt;img src="img.jpg"&gt; 

.. whats wrong with that? 

Here is the whole entire thing. 

```
&lt;html&gt;
&lt;title&gt;
Mom's Computer
&lt;/title&gt;
&lt;body bgcolor=&quot;yellow&quot;&gt;
&lt;center&gt;&lt;b&gt;&lt;font color=&quot;red&quot;&gt;
MOM's COMPUTER!!! 
&lt;/center&gt;
&lt;br&gt;
&lt;br&gt;
&lt;br&gt;
1. The Case! 
&lt;br&gt;
&lt;code&gt;&lt;img src=&quot;C&#58;\Documents and Settings\Lev\My Documents\My Documents\Misc\Mom's Computer\case.jpg&quot;&gt;&lt;/code&gt;
&lt;br&gt;
&lt;br&gt;

2. The Monitor! 
&lt;br&gt;
&lt;img src=&quot;C&#58;\Documents and Settings\Lev\My Documents\My Documents\Misc\Mom's Computer\monitor.jpg&quot;&gt;

&lt;/body&gt;
&lt;/html&gt;
```

---

### Post by triad169 on 2004-10-18
Infatuated_iPod,

I dont know if this will answer yoru question but looking at your code.

If you try to open that html document in Linux it will not work because Image Location Path would be different in Linux then In Windows.  ie

Windows:
> &lt;img src="C:\Documents and Settings\Lev\My Documents\My Documents\Misc\Mom's Computer\case.jpg"&gt;

You should use relative Paths for HTML.  example:

```

&lt;html&gt;
&lt;body&gt;

&lt;p&gt;
An image&#58;
&lt;img src=&quot;images/constr4.gif&quot;
width=&quot;144&quot; height=&quot;50&quot;&gt;
&lt;/p&gt;

&lt;p&gt;
A moving image&#58;
&lt;img src=&quot;images/hackanm.gif&quot;
width=&quot;48&quot; height=&quot;48&quot;&gt;
&lt;/p&gt;

&lt;p&gt;
Note that the syntax of inserting a moving image is no different from that of a non-moving image.
&lt;/p&gt;

&lt;/body&gt;
&lt;/html&gt;

```

You html file would be loacted in main directory and you would have a sub directory called images to put images in.

Take a look at :

[http://www.w3schools.com/html/default.asp](http://www.w3schools.com/html/default.asp)

For a much better explanation then me.

Hope this is what you where looking for.

Triad[/quote]

---

### Post by Infatuated_iPod on 2004-10-18
I am doing this in windows, sorry. It shows up fine on IE, but not at all on Mozilla.

---

### Post by HungSquirrel on 2004-10-18
> &lt;img src="img.jpg"&gt; 

.. whats wrong with that?
What's wrong with that is it wasn't your exact code, which is what we need to help you.  Now that I see your exact code, I can help you better.

Three suggestions:

Prepend file****:/// to your URLs, e.g. &lt;img src="file:///C:\whatever.jpg"&gt; .

Take the &lt;code&gt; tags off your images.  You don't need them.

Put your &lt;title&gt; inside a &lt;head&gt;, e.g.

```
&lt;head&gt;
&lt;title&gt;
Mom's Computer
&lt;/title&gt;
&lt;/head&gt;
```

---

