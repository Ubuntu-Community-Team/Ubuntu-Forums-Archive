---
title: "[SOLVED] Panel Menus - Make Transparent?"
date: 2008-10-22
forum: General Help
---

### Post by joey-elijah on 2008-10-22
Googled but most items i found were ollllld.

Currently using 8.10 - and i'm loving the new darkroom theme. After making my top panel semi-transparent, i'm wondering if there's a way to get the drop down menu's to follow suit?

[IMG]http://farm4.static.flickr.com/3283/2965873046_e4aa8abc28_b.jpg[/IMG]

bonus points for anyone who can tell me how to replace the running man log out icon with the normal icon without changing theme etc

---

### Post by steveneddy on 2008-10-22
Open CCSM

Go to General Settings

Go to Tab - Opacity Settings

Settings as follows:

dock     67
Menu    90
DropdownMenu   92
popupmenu        93

Change the settings as you like.

These settings come from my own configuration.

This is not a complete list.

Here's a link that may help you:

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

---

### Post by stevek42 on 2008-10-22
Odd, I don't see Opacity settings like that on Intrepid.  Any ideas there?

UPDATED:  My CCSM has it under Accessibility.

---

### Post by joey-elijah on 2008-10-22
was just asking haha

many thanks will try now

---

### Post by joey-elijah on 2008-10-22
that worked AWESOMELY, many many thanks!!

---

### Post by steveneddy on 2008-10-22
> **joey-elijah said:**
> that worked AWESOMELY, many many thanks!!

You are very welcome.

Please mark as solved.
:)

---

### Post by catchagato on 2008-10-31
I have also just upgraded to 8.10. I can't seem to make my drop down menus transparent. I also tried adding the window type in Opacify, but nothing happens. Can someone please explain step by step how to make transparency in 8.10 ccsm? Thanks in advance.

---

### Post by joey-elijah on 2008-11-01
Strange, because i'm now using Ibex and it works fine.

---

### Post by t60-raven on 2008-11-18
> **stevek42 said:**
> Odd, I don't see Opacity settings like that on Intrepid.  Any ideas there?

UPDATED:  My CCSM has it under Accessibility.

I've been having the same problem.

**CCSM has two options under Accessibility:**
[LIST]
[*]Opacity
[*]Opacity, Brightness and Saturation
[/LIST]

(I know I didn't see it either)

Go into **Opacity, Brightness and Saturation**

Then there's this whole syntax for matching attributes to windows.

Compiz's site explains it pretty thoroughly:
[http://wiki.compiz-fusion.org/WindowMatching]("http://wiki.compiz-fusion.org/WindowMatching")

drag the terminal commands from the compiz site, into the terminal and enter.  (cursor should change to cross-hair)
click on the window you want to know about, and the info appears
yatta yatta

[B]since you can't really do the click thing on menus:

       type=popupmenu


      type=dropdownmenu
[/B]

---

### Post by chunchengch on 2008-11-28
Here is the screenshot of Opacify setting window in Ubuntu 8.10, I can't either make the **dropdown menu** transparent, any comment? thanks!

[ATTACH]94526[/ATTACH]

---

### Post by I wanted to leave on 2008-11-30
> **chunchengch said:**
> Here is the screenshot of Opacify setting window in Ubuntu 8.10, I can't either make the **dropdown menu** transparent, any comment? thanks!

[ATTACH]94526[/ATTACH]

All you need to do is follow the instructions in the post above yours: i.e Go into Opacity, Brightness and Saturation, not Opacity :rolleyes:

---

