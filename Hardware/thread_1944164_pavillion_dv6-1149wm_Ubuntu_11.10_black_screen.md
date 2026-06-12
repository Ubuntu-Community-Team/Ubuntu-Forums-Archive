---
title: "pavillion dv6-1149wm Ubuntu 11.10 black screen"
date: 2012-03-20
forum: Hardware
---

### Post by mvmacd on 2012-03-20
I have a pavillion dv6-1149wm, and I've been running Ubuntu 11.04. 
I finally decided to install 11.10.  I used UNetbootin to flash the 64-bit 11.10 ISO to my flash drive, booted from it, and after selecting the Default boot, it started to do something, and then the screen turned off.  I waited for a little, and nothing happened.

Then I rebooted, tried another boot option, and still got nothing.
I googled "ubuntu 11.10 black screen" and saw something about replacing 'quiet splash' with 'nomodeset'.  I tried this, and then I got some text.. it kept scrolling, and then it got stuck somewhere, and seemed to be going nowhere. 

So I pressed Ctrl+Alt+F1, then typed

```

$ sudo su
# startx

```
and it said something about "no screens found"

Anyone have any ideas? Or should I just sit tight till 12.04?

---

### Post by speedyzolw on 2012-04-19
I had a similar problem on my HP DV6 6B08SA when trying to use the 11.10 liveCD or liveUSB - I found I could just about bypass the problem by using an older version (10.10 or lower) or I could also get around it by using the 12.04 beta 2, with the boot option `radeon.modeset=0` (obviously this will only apply for a radeon graphics card, but maybe `nomodeset` will work instead if you don't have radeon) and removing `quiet` and `splash`. Does this help?

 Unfortunately it was at this point I realised HP have already used all the primary partitions you can have on a single hard-drive, so I gave up quite quickly after this point (since I didn't want to delete partitions on a new laptop) and so I never fully explored what works and what doesn't. 

But any road up, it may be sensible to wait for 12.04 to be released (very soon I think?) and if it doesn't work straight off, try some of the same tricks as you did with 11.10 and if your lucky it might work for you as it did for me

---

### Post by mvmacd on 2012-04-19
I do have AMD Radeon graphics  [A6-3400m CPU w/ integrated graphics], but I did not try the radeon.modeset=0, I did modeset=0.  

Anyway Ubuntu said they were almost ready to release 12.04 LTS, so I think I'll wait a little bit, and then try it when it releases.
If it doesn't work, then I will try your suggestions, thanks.

edit: I was able to install 12.04 without any black screen. however I still have some issues like the graphics being quirky and stuff

---

