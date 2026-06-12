---
title: "Ubuntu 9.04 wont boot"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by VegaTDM on 2009-07-28
Ive been running 8.10 since it came out and had no problems, i finally got around to up grading to 9.04 the other day. burned a CD, checked it and it had no problems/errors installed it normally. got it up, installed all the programs i wanted, then updated it. after that it said it needed to restart. so i clicked "restart now". it powered down normally, then it went to boot up. it went well until it got to the loading bar, it got about 98% done. then my screen flickered some and it showed the screen it was on, with green vertical lines running down the top of my screen and (as far i can tell) random blue blots at the very top.


it does this every time i try to boot. and when i try to go to the command line it says something about kinit no resume image

---

### Post by QIII on 2009-07-29
What sort of graphics card do you have?

Bah!  Never mind.  Didn't see your last line.

Wait a bit and I'll do some research.

---

### Post by QIII on 2009-07-29
OK.  Back to my original question, I guess.

"kinit no resume image, doing normal boot" apparently just means there is no hibernate image to boot from.  Who knows?  Maybe you did a hard shut down by accident.

Anyway, you can apparently ignore that for now.

The behavior you are seeing seems to indicate a graphics issue.

What type of graphics hardware do you have?

---

### Post by VegaTDM on 2009-07-29
> **QIII said:**
> OK.  Back to my original question, I guess.

"kinit no resume image, doing normal boot" apparently just means there is no hibernate image to boot from.  Who knows?  Maybe you did a hard shut down by accident.

Anyway, you can apparently ignore that for now.

The behavior you are seeing seems to indicate a graphics issue.

What type of graphics hardware do you have?



i have no idea, i bought the computer used from one of my friends and never used it for much more than web browsing, i found a old 6.06 disc and installed that beside 9, it works fine but it wont work with my USB wireless adapter, how do i view my graphics setup in 6.06?

---

### Post by Guineapig1 on 2009-07-29
Hi there, guys.

  I have the same problem with Ubuntu Jaunty in a MSI VR630 notebook (the one with the sempron CPU).
  I could install the SO just fine and added a lot of things like Beryl-Fusion, XBMC and Nvidia drivers 185.18.14 ver. But when i reebooted for the first time and commanded GRUB to boot the Linux Kernel that comes with this distro, i get the splash screen which hangs up at around %15 for a few minutes. Later it does load completely and the Nvidia logo shows up but the GUI crashes at this moment. So, i type ctrl+alt+F1 and it enters to the console and it does, and before it does some green bar lines and red japanese fonts i see in the screen. But the SO doesn't mount any device but cdrom.
  It hope it is not a case for Mulder and Scully. So, if someone could help me please, i'll be thankfuly.

  The specs of the notebook:
  * CPU  - AMD Sempron
  * GPU  - Nvidia 9100M G
  * RAM  - 2GB

The HD is partitioned like this:

sda1 ext3  ubuntu
sda2 ntfs  windows vista
sda3 fat32 my personal files
sda4 swap  for swapping (doh)

Thanks so much!!!

---

### Post by stlsaint on 2009-07-29
for the first poster it sounds like a graphics issue update drivers or use older version of ubuntu....for the second it sounds like a error on install or corrupted OS...(not SO!!!;) also it may be graphics for you...try down grading to an older ubuntu and without all the beryl-graphics...fyi we no longer use beryl--theres compiz for that! try it and post results!

---

### Post by QIII on 2009-07-29
In Argentina, the OP may be used to referring to an SO.  

In English, we put adjectives (in this case a gerund form) before nouns, thus "operating system" or OS.

Romance languages do the reverse.  So he speaks of a "sistema operativo", or SO.

And now back to our regularly scheduled program...

---

### Post by Guineapig1 on 2009-07-30
Hola, muchachos.

You are totally right, stlsaint. It was my mistake to write SO instead of OS.
At the moment i posted i had a long time with no sleep at all, and i am not an english language expert.

The important thing is that i booted the OS :D with the nosplash option and i figured out a video driver problem. I don't think that i installed a corrupted distro because i checked with the CD application.

---

