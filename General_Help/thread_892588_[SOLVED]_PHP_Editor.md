---
title: "[SOLVED] PHP Editor"
date: 2008-08-17
forum: General Help
---

### Post by gmxgeek on 2008-08-17
Hello. I am an avid web-developer, primarily using PHP. I currently use nano in a terminal to write all my scripts, however on occasion I find myself wishing for a program with a little more oomph. Don' get me wrong, i love nano, and have been using it for years, but some features that would be nice to have would be:

Syntax Highlighting
Function Hints (arguments popup when writing a call to a function)
Custom templates to include a block of init code on all my pages

Does such a program exist?
If so, where might i find one?

---

### Post by sillyxone on 2008-08-17
I've been using Geany to write PHP applications for three years and totally satisfy with it. Recently a new co-worker tried to have both of us working on eclipse (with nice x-debug capability) but after a week, both of us went back to Geany. I've also used Bluefish before that but it wasn't quite good for me.

One of the things I like about Geany is the syntax highlighting can be customized. For example, I don't like having bold text, just need to go into the PHP template and edit that.

Function hinting works pretty well with both PHP's built-in and newly defined functions. I never used template but it does have that feature.

You should be able to find Geany in the repo (Synaptic or apt-get)

---

### Post by Sycron on 2008-08-17
I am using gedit for making my php scripts and works wonderful.

---

### Post by dje on 2008-08-17
+1 for geany, it's a great editor/ide for many languages

dje

---

### Post by gmxgeek on 2008-08-17
> **sillyxone said:**
> 
Function hinting works pretty well with both PHP's built-in and newly defined functions.

Thank you for the reply. I have just gotten Geany, and it seems to suit my purposes well so far, but the function hints don't seem to work. I made a new function called test($data="null") {}, but when i tried to use test(), the function hint didn't pop up. Is there a specific option to enable it?

EDIT: Built-in functions work fine, but no custom ones do

---

### Post by Achetar on 2008-08-17
Quanta Plus is good. Not sure if it does custom functions or not though. I don't think so. It uses QT3 and not GTK+, so it doesn't integrate as well. I hadn't tried geany, gonna give it a go.

---

### Post by sillyxone on 2008-08-17
> **gmxgeek said:**
> Thank you for the reply. I have just gotten Geany, and it seems to suit my purposes well so far, but the function hints don't seem to work. I made a new function called test($data="null") {}, but when i tried to use test(), the function hint didn't pop up. Is there a specific option to enable it?

EDIT: Built-in functions work fine, but no custom ones do


Sorry, I mistook function hinting for function-name auto-completion. Only bult-in functions has the hinting.

---

### Post by gmxgeek on 2008-08-17
Ah i see. Well, it still 90% suits my purposes. Thanks very much!

---

