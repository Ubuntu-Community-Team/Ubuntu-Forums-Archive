---
title: "resolution on laptop"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by one_ro on 2005-08-29
Hi folks,

I have the following problem: a newly installed Kubuntu 5.04 on a Fujitsu Siemens laptop wouldn't switch to another resolution but 640x480 (which is _really_ annoying :)
I have edited the [FONT=Arial Black]/etc/X1/xorg.conf[/FONT] file and everything seems ok (there are some other different resolutions there).
Right-clicking on desktop for display settings don't seem to show that.
I suspect Kubuntu doesn't recognize the video card, which is:
[FONT=Arial Black]intel video 82845 v6.13.1.3845[/FONT]

Could you please suggest what I should do from here?
Thanks in advance,
Adrian

---

### Post by frodon on 2005-08-29
You could need to add hsync and vertsync parameters in devise section to enable higher resolutions. Also check that you use the good [driver](http://www.ubuntuforums.org/showthread.php?t=27029&highlight=intel+video+resolution)  for your video card. Use the search field in the forum with good keywords and you will find a lot of threads about that, all is already in this forum.

---

### Post by one_ro on 2005-08-29
[QUOTE=frodon]You could need to add hsync and vertsync parameters in devise section to enable higher resolutions. Also check that you use the good [driver](http://www.ubuntuforums.org/showthread.php?t=27029&highlight=intel+video+resolution)  for your video card. Use the search field in the forum with good keywords and you will find a lot of threads about that, all is already in this forum.[/QUOTE]

Thank you very much, that was exactly the problem. Adding those missing parameters solved it.
Cheers,
Adrian

---

### Post by frodon on 2005-08-29
Cool  :) 
I hope you put the construstor's parameters of your screen for hsync and vertsync parameters, because wrong parameters could destroy your screen.

bye one_ro  ;-)

---

