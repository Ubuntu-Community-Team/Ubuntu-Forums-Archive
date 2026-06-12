---
title: "Flash in Firefox isn't wroking"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by neeeck on 2009-09-28
I'm new to ubuntu and I decided to try it out on my netbook to see how I like it and I love it, however I can't watch youtube video's or do my online homework because, what I guess is the flash player, isn't working. I've installed the latest adobe flashplayer, but all the shows up when i try to watch a youtube video is the picture, nothing moves, but the audio works. 

I'd really appreciate if someone could help me out with this, I've tried reinstalling the plugin, and I've been looking for the solution to this problem for about three days.

thank you for your help

---

### Post by earthpigg on 2009-09-28
hi,

did you install flash by doing the 'click here to install flash!' thing at youtube or some other website? in Linux, that is nearly always the incorrect way. 

we generally try to only trust & install software from our distribution (Ubuntu), not random-website-advertisement.com, around these parts :D

if that is how you installed flash ("click here to download crapware!" at random website such as youtube.com or adobe.com), open a terminal and type this in:

```
sudo apt-get install ubuntu-restricted-extras
```

***or***, if you would rather point-and-click go to add/remove programs and search for ubuntu restricted extras there.

good luck, and let us know if you run into any more problems :D

---

### Post by neeeck on 2009-09-28
> **earthpigg said:**
> hi,

did you install flash by doing the 'click here to install flash!' thing at youtube or some other website? in Linux, that is nearly always the incorrect way. 

we generally try to only trust & install software from our distribution (Ubuntu), not random-website-advertisement.com, around these parts :D

if that is how you installed flash ("click here to download crapware!" at random website such as youtube.com or adobe.com), open a terminal and type this in:

```
sudo apt-get install ubuntu-restricted-extras
```***or***, if you would rather point-and-click go to add/remove programs and search for ubuntu restricted extras there.

good luck, and let us know if you run into any more problems :D


I tried this both ways, its installed, but so is the adobe flash plugin, which i got from the adobe site. I'm going to uninstall the adobe one and see how that works.

---

### Post by serpentalis on 2010-06-28
I tried that, and flash still isn't working for me. I have tried so many command lines, downloads, tutorials, etc. in the past 24 hours, I'm almost ready to give up. Can anyone help?? I want to get flash working in both Firefox & Chrome.

---

### Post by Michl on 2010-06-30
After the most recent update in hardy (June 30) which
included a firefox update and many other things
I wasn't paying attention to because usually there
are no problems, flash was also a problem.  I;m
hoping the next update will correct it.

---

