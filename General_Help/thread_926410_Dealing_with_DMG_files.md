---
title: "Dealing with DMG files"
date: 2008-09-21
forum: General Help
---

### Post by tbielawa on 2008-09-21
[SIZE="5"]Background[/SIZE]

I recently downloaded a DMG containing a collection of useful Free and Open Source Mac OS software. (You can get it [here]("http://www.freesmug.org/fscd/") if you're interested.) I didn't see any obvious way to handle this file with Ubuntu so I searched the forums and the wiki and google.

[SIZE="5"]Problem[/SIZE]

Everyone seemed to be pointing to the same broken solution, to use a PERL script called dmg2iso from [here]("http://vu1tur.eu.org/tools/"). I tried it out, once I got past installing the zlib libraries for perl and pointing the script at /usr/bin/perl it still didn't work :x

[SIZE="5"]Solution[/SIZE]

I set out to get a working solution to this problem of dealing with DMG files. It was pretty quick, I just compiled the dmg2img code also available on the site where dmg2iso is, mounted the image, and then made an iso with Brasero. 

[SIZE="5"]Tutorial[/SIZE]

Since the existing tutorial on [the Wiki]("https://help.ubuntu.com/community/ManageDiscImages#Old%20Method") was incorrect I went ahead and wrote [a new tutorial]("https://help.ubuntu.com/community/ManageDiscImages#New%20Method"). I've only tested the tutorial on Hardy Heron 8.0.4.1, AMD64.

If anyone has anything to say I'd love to hear it. I'm looking for feedback, errors in the tutorial, confirmation of the method working on other releases, or general praise (\\:D/).


Thanks everybody! I hope this helps some one out!

---

### Post by rbolio on 2008-09-22
so let me see if i got this straight...you got .dmgs to work in ubuntu?


<3 aperture :guitar:

---

### Post by tbielawa on 2008-09-22
> **rbolio said:**
> so let me see if i got this straight...you got .dmgs to work in ubuntu?


<3 aperture :guitar:


Well ya, I guess so.....

:D

It's not the most direct method for making them usable but they are usable now :)

---

