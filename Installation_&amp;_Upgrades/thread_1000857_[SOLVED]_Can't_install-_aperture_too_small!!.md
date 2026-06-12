---
title: "[SOLVED] Can't install- aperture too small!!??"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by karamu on 2008-12-03
I have just put together a new system- it's:

ASUS M2A-VM HDMI mobo
Athlon 64x2 processor
2 Gig PC4000 RAM
200 Gig Maxtor HDD

I have installed Windows XP no problem- except I want a dual boot system and to use Ubuntu primarily.

When I try to run the (64bit) Ubuntu 8.1 install CD, it initially boots to the screen where I can select to try without changing system (ie run live), install Ubuntu etc.

When I select run or install, the screen goes black and I see:

oooo.4 aperture too small 32mb not 64mb (or similar, I can't remember the exact words)

it just sticks then and I can't do anything other than hit reset.

I believe it is some kind of problem with my BIOS, but I can find no setting related to "aperture"- the shared video RAM is set at 256mb so I am stuck....!!!

Any ideas anyone?

---

### Post by karamu on 2008-12-03
Well, looks like I've found a workaround- Ubuntu 8.04 boots fine (I'm writing this using its live function)- guess I'll install that tomorrow and wait for the next upgrade.....

---

### Post by oldos2er on 2008-12-03
Not sure about the error you're getting. Maybe you should run 'Check CD for defects' first just to make sure the disc is ok. If it is and you're still seeing the error, try googling for it.

 Ubuntu 8.04 is a perfectly fine distro, and since it's LTS, you won't need to worry about upgrading for quite awhile.

---

### Post by karamu on 2008-12-04
Yeah, I tried Googling it and couldn't find much that was the same as I have- some other people reported the same error message on boot but could still run Ubuntu (but had video performance issues). I have had the same issue with two different CDs so it isn't the disc.

I think I will just run with 8.04 for the time being- as you said it is perfectly OK and is long term supported.

Thanks for the help anyway.

---

### Post by razy60 on 2008-12-04
have you tried the 32bit version, or is it absolutely necessary for you to have 64bit.

Raz

---

### Post by karamu on 2008-12-04
I have tried the 32bit version- I get the same problem. The 64bit version of 8.04 boots so I don't think that is the issue.

---

### Post by psusi on 2008-12-05
Try lowering the shared video memory size in the bios to only 32 megs.  It sounds like the bios is saying it should be 128 but only supplying a 32 meg window in the memory map to see it.

---

### Post by karamu on 2008-12-05
OK, thanks for the suggestion- I'll give it a try when I get home tonight.

---

### Post by karamu on 2008-12-05
Still the same even if I change the onboard video memory allocation- looks like I'm going with 8.04......

---

### Post by karamu on 2008-12-08
I've started a new thread for all my installation woes>>>

[http://ubuntuforums.org/showthread.php?p=6330413#post6330413](http://ubuntuforums.org/showthread.php?p=6330413#post6330413)

in case anyone stumles upon this and has some ideas!!

---

