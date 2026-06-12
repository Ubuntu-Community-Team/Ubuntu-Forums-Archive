---
title: "No  sound"
date: 2006-05-16
forum: Hardware &amp; Laptops
---

### Post by xanthorrhea on 2006-05-16
I have  just  installed  ubuntu Ver 5.10 on my  Acer 4064WLMI Notebook, everything works exept there  is no  sound whatsover. Nothing  is  greyed  out under settings and CDs appear to  work [progress  bar  moves allong].  
Using google  I have bean  searching  for a fix to  no avail, is the  following  information any  help to  you.
 
roberto@Saturn:~$ sudo lspci |grep -i audio
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
roberto@Saturn:~$

Sound  works OK under MS XP.

rgds
Roberto

---

### Post by waster on 2006-05-16
unfortunately there are a few ways this could be going wrong. I've had a problem before that sounds defaults to mute, although I think ubuntu fixed this. Check this.

In the volume applet preferences, check that you are controlling the right/both sound cards. sometimes two appear, representing different internal subsystems even if only one sound system is there, as far as you are concerned.

---

