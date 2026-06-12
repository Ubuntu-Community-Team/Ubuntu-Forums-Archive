---
title: "Waccom pen and tablet too pressure sensitive"
date: 2012-01-12
forum: Hardware
---

### Post by M0phead on 2012-01-12
I have recently installed Ubuntu Ocelot on my laptop, and encountered problems using a previously (on Windows) functional Wacom drawing tablet: Bamboo Pen model "CTL-460".

The tablet works fine in terms of tracking and clicking, but in both Gimp and Inkscape the pressure sensitivity for drawing is set far too high. There is still a degree of variance obtainable, but nothing like the range I have known the device to provide.

I did several searches and found this page reporting what appears to be the same bug:
[http://ubuntuforums.org/newthread.php?do=newthread&f=332](http://ubuntuforums.org/newthread.php?do=newthread&f=332)
...However:

After following instructions linked on that page to compile a working set of drivers, which unless I've misread looks to be the only fix reported to have worked, the problem persists. Reading other posts on the page speculating over incorrect values being set in the xorg.conf.d configuration file, I attempted without success to locate my own version of this file. Am I right to be concerned at it's apparent absence?
Fixes for this device, for this issue and others, that I have been able to find always seem to reference an xorg.conf.d file.

It might be worth mentioning that I additionally already experienced the issue mentioned on this page, and followed the instructions there to resolution of said issue:
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)

I am relatively new to Linux as most likely you can tell, any help fixing this problem would be much appreciated.

---

### Post by M0phead on 2012-01-13
...Bump?

---

### Post by Favux on 2012-01-14
Hi M0phead,

Your link to the bug and the bug fix is broken so I don't know where you're at.  I'm assuming you compiled input-wacom?  If not see part I. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Of course if you've installed a PPA that uses a dkms implementation of a wacom.ko that will prevent any new wacom.ko from being used.

I can't remember what kernel the fix was submitted to.  I would have thought it was in the 3.0 kernel.  I guess not.

---

### Post by M0phead on 2012-01-14
Hello Favux.

I just checked it and I see what you mean, seems like I've pasted the wrong link... Oh, the joys of making forum posts at One in the morning. Sorry about that, here's a link that works:
[https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/786952](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/786952)
Reading over the posts I've just noticed your name; I guess you're familiar with this one then?
I any case, having visited the page you linked a few days ago I confess to not having followed the instructions on part 1. The notation said to skip that if running Ocelot or Natty? ...Wait, no, on closer examination that only applied to first generation tablets... My own error again, I'll go compile the driver now... :redface:
The PPA you're talking about here being the one I installed to rectify the issue described in my second link? I used the instructions in post #86 by poster Aapo, which fixed the screen jumping problem completely.

Thanks for your help, it's really appreciated. My apologies for my own lack of technical knowledge making this more difficult than it needs to be; I'll post again with results when I've followed your instructions regarding compiling the driver.

---

### Post by M0phead on 2012-01-14
I just finished compiling the driver and testing the tablet, it works absolutely fine now. Looks like I need to learn to read instructions more carefully...

Thanks very much for sorting this :)

---

### Post by Favux on 2012-01-14
Good.  :)

The Launchpad bug report link refreshed my memory.  That was June last year after all.  Right the fix is in the 3.1 kernel.

So you have brutally exposed my lapse in the HOW TO.  At one point there was information on how to fix the first generation Pen's pressure levels.  Looks like I lost it in the prunings I did to the HOW TO over the last month trying to unclutter it a little.  My goof too.

No, not the Gimp PPA.  That doesn't do anything with the kernel so there is no need for a dkms (dynamic kernel module support).  Compiling input-wacom produces a wacom.ko, which is the Wacom usb kernel driver/module.  So PPA's that include the wacom.ko usually include a dkms implementation of it.  That means you don't have to recompile it with each kernel update, but the flip side is you are stuck with the same wacom.ko until you remove the dkms for it.

---

### Post by M0phead on 2012-01-14
I'd say that if only one person has had trouble in the last month with this, then your prunings were probably OK. Personally I'd put my troubles down to inexperience and oversight, primarily the second of those as if I'd simply compiled the drivers as instructed then everything would have been fine.

I think I understood about four fifths of that... So my education continues. ;)
Do you mind if I ask how and when you got into using Linux? Purely out of interest, I'm not doing a survey or anything.

---

### Post by Favux on 2012-01-14
I enjoy tinkering.  Linux was something new to tinker with on my then brand new tablet PC with its humongous hard drive.  Suddenly having a hard drive that large just demanded another OS.  I guess all the cobbling I had been doing to nurse my ancient Desktop on had gotten less fulfilling.  It was quite the Frankenstein.  I had managed to shoehorn Fedora 2 (or 3?) into an ancient laptop earlier.  Even though it was heavily underspecified RAM-wise it managed to run Fedora fine, albeit very slowly due to heavy use of the swap drive.

---

### Post by M0phead on 2012-01-14
That's pretty interesting. What are the specifications of the device?
It sounds like a lot of people come into Linux by way of an old, dedicated, tinkering computer. My account on here is three years old because I put Xubuntu on an ancient machine with limited RAM a while back at the recommendation of my cousin, who did the same with a laptop which I suspect to have been constructed in the Bronze Age.
In any case, I'm trying to learn to use Linux properly now after spending a year with and subsequently becoming tired of an entry level Windows laptop. Admittedly this wasn't a great start, but I guess my knowledge can only improve from here :L

---

