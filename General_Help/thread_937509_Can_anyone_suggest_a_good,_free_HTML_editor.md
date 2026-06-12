---
title: "Can anyone suggest a good, free HTML editor?"
date: 2008-10-03
forum: General Help
---

### Post by PsychedelicWonders on 2008-10-03
I am trying to get into E-commerce and need to build a website.

I have NO CLUE where to begin and am currently reading Website 101 on build-website.com

They suggest if you are not a programmer (which I am not) to download a good, free HTML editor.

The website also says this:

For a more professional website, consider purchasing Microsoft FrontPage 2002 or Dreamweaver MX.

Should I get one of these two instead?

I am going for a professional website.

What do you guys suggest?

---

### Post by Bakon Jarser on 2008-10-03
[http://ubuntuforums.org/showthread.php?t=651977&highlight=web+page](http://ubuntuforums.org/showthread.php?t=651977&highlight=web+page)

---

### Post by techstop on 2008-10-03
> **PsychedelicWonders said:**
> <SNIP>

The website also says this:

For a more professional website, consider purchasing Microsoft FrontPage 2002 or Dreamweaver MX.

Should I get one of these two instead?

I am going for a professional website.

What do you guys suggest?

Uh oh! Alarm bells are ringing! FrontPage (any version) has a terrible reputation for producing non-standard rubbish html.

Since you're on the ubuntu forum, you could try kompozer. It's in the repository.

[http://www.kompozer.net/](http://www.kompozer.net/)

---

### Post by PsychedelicWonders on 2008-10-03
I'd prefer to use Ubuntu based applications, just because I love Ubuntu so much...

But will this give any of my visitors problems if I am building this on a Ubuntu platform?

I think I shall try out Kompozer... is that a pretty easy to use HTML editor?

What is the code to install it?

Thanks.

---

### Post by techstop on 2008-10-04
Go to Synaptic Package Manager

System>Administration>Synaptic Package Manager

...search for "kompozer".

---

### Post by PsychedelicWonders on 2008-10-04
4 things come up... which ones should I download?...

---

### Post by MaindotC on 2008-10-04
Gedit works fine and auto closes tags for me, highlights them in different colours, etc.

---

### Post by PsychedelicWonders on 2008-10-04
> **strAlan said:**
> Gedit works fine and auto closes tags for me, highlights them in different colours, etc.

What does "auto close tags" mean and what is the benefit of this?

---

### Post by Allah on 2008-10-04
Erm ... why don't you just use vim or emacs? Coupled with a document on HTML/XHTML basics, I reckon you'd be ok. Using something such as dreamweaver or frontpage isn't really going to add/remove anything from your ability to learn.

These editors (emacs/vim) are free, and are in the repositories, they may be difficult for you to learn, at first. So look at the manual pages; perhaps you should also look at the nano/pico editor. It's probably available on your system right now, simply type 'nano' in your terminal.

They have the capability of syntax highlighting, I'm not certain if nano does it by default, when you append the document name with an extension (i.e .html); but there are many documents on most search engines that will help you.

---

### Post by PsychedelicWonders on 2008-10-04
whats wrong with Kompozer?

It seems to be what I thought an HTML editor was...

But then again, I didnt know what an html edtor was before about 10 minutes ago... and still really dont.  

I do realize it allows you to make a page similar to word or something along those lines.

Which is what I'm looking for.

I'd prefer to not have to learn HTML right now and would just like to get up and going as fast and easy as possible.

---

### Post by jerome1232 on 2008-10-04
What you are talking about are called WYSIWYG editors (what you see is what you get) or alternatively what you see is what you'll never get (j/k... well that depends on the editor) ;) They tend to generate some garbage html that isn't needed.

vim and gedit are text editors that have syntax highlight capabilities + some more, and are often used to write up code. (html being a type of code... kinda) aka WYSIWYAF (what you see is what you asked for)

Generally you'll want to test your pages out with the browsers you expect to be used to view your site. There are differences in the way they render html.

I don't have a recommendation just thought I'd try and make that more clear.


edit: I realize reading my post I sound condescending towards wysiwyg type editors I was just making a joke about them and edited it a bit, and kompozer sounds very nice since it gives you a code view as well (it would help with learning the html tags and what they do, I just might give it a try, unless it's a qt app, I hate my theme not looking right.)

---

### Post by NNNNNNNNNN1515 on 2008-10-04
I second Kompozer. I've been using it for a while. It works great in ubuntu and the interface is simple. That being said, sometimes I've had to touch up some things editing the code manually. You can do this in Kompozer - there is a code view as well as a wsyiwyg. I used front page before. I think kompozer is superior. The code it puts out is a lot cleaner, and the program uses less resources than front page. Not sure if it has every feature front page has but a lot of front page features are garbage anyways if you ask me.

If you like to code by hand - gedit and emacs are great text editors.

---

### Post by rsambuca on 2008-10-04
From the description of your html knowledge, I highly recommend starting out with something like Kompozer.  The benefit when starting out is that you can generate pages without knowing all of the html syntax.  As you learn more of the proper syntax, you may wish to start using just a standard text editing program to modify the html code to your liking.  The code generated with Kompozer isn't perfect, but it usually gets the job done.  Certainly a good enough starting point.

---

### Post by MaindotC on 2008-10-04
> **PsychedelicWonders said:**
> What does "auto close tags" mean and what is the benefit of this?

Like if you start an html page by typing:

<html>

It will form a closing tag automatically like:

</html>

I mean anyone who has so much viewed a page source in FF should know this, but if you're a beginner then I would just assume this would be beneficial.

---

### Post by PsychedelicWonders on 2008-10-04
Alright so Kompozer it is.

But when I typed that in synaptic manager, it gave me 4 items, which ones should I actually install?...

---

### Post by jerome1232 on 2008-10-04
The one that just says kompozer

---

### Post by webbdawg on 2008-10-04
I downloaded Quanta Plus. It requires a couple of other packages but after I installed them things were running fine.

I use MM Studio 8 on my XP system and am considering trying one of the win to linux type thingys.

Oh yea, make sure you work with Kbuntu instead of Ubuntu. I first installed Ubuntu and installed QP things did not work well. Kbuntu seems to be more of a business / Work machine.

---

### Post by rsambuca on 2008-10-04
> **webbdawg said:**
> Oh yea, make sure you work with Kbuntu instead of Ubuntu. I first installed Ubuntu and installed QP things did not work well. Kbuntu seems to be more of a business / Work machine.Nonsense.  Pure and utter nonsense.

---

### Post by jerome1232 on 2008-10-04
> **rsambuca said:**
> Nonsense.  Pure and utter nonsense.

 +1

KDE vs Gnome is mostly a preference thing.

---

### Post by fragos on 2008-10-04
Kompozer is a good choice of HTML editor for a beginner that doesn't know HTML. It allows you to look at and edit in a number of ways -- including pure HTML. HTML isn't hard to learn and if you choose to learn Kompozer can help you do that. I've compiled some good information on site design and have a tutorial on using HTML. It all free -- sites in my signature below.

---

### Post by PsychedelicWonders on 2008-10-04
Yeah I dont know ANYTHING about HTML, but that isnt to say I cant learn.

I just need a "Barney" style program that will hold my hand as I try to accomplish what I want.

I think Kompozer is it, now I just gotta go through the tutorials.

I'll check your website out later tonight fragos, thanks.

---

### Post by rsambuca on 2008-10-04
Let us know how it goes, and give us links when it is done so we can see the products of your labour!

---

### Post by PsychedelicWonders on 2008-10-04
Alright, seems easy enough so far.

But what forum should I utilize for a bunch of Kompozer questions?

Is there a section on this forum dedicated to Kompozer?

It seems I will be using tables quite alot because I am going to be inserting a lot of various pictures.

But I want to be able to include a link embeded in the picture, so that when ever you click on the picture, it takes you to a particular website...

How exactly do I do that?

Also, it seems the various pictures I have are all different sizes.

What do I do to make all of my pictures the same size to keep everyting uniform?

Do I need to open the picture file in GIMP and resize them?

What is the quickest/easiest way to go about doing this?

I will be using many different pictures and need something that will be quite easy to quickly resize them.

---

### Post by Merk42 on 2008-10-05
I tried to install Quanta, both through add/remove and through the kdewebdev package.  Quanta refused to run though, the error is:

```
kbuildsycoca running...
QObject::connect: Cannot connect (null)::initiateDrag(QWidget *) to QuantaApp::slotTabDragged(QWidget*)
KCrash: Application 'quanta' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
```

---

### Post by fragos on 2008-10-05
"drkonqi" is in the "kdenlive" package in the Ubuntu repositories.

---

