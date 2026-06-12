---
title: "Installation help- basic installtation instructions"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by mattj7 on 2009-02-23
I have recently been wanting to try ubuntu, so i decided to install it on an extra hard drive i had laying around to see if i liked it enough to install on my laptop.  I downloaded the iso and burned it to a cd.  I then put the other hard drive into the computer and poped in the newly burned cd.  I knew i was supposed to hit an f_ key to boot from cd, but the loading screen only said f3 for settings, so i just hit all the f keys like a madman.  I didnt think this would work, but sure enough there came the pretty orange loading bar bouncing back and forth and the ubuntu logo above it.  Then i got a screen to select language, but nothing i did on the keyboard had an effect on the screen.  It was on a timer though, so after 30 sec it selected english.  Then, instead of getting a setup screen like I expected, I got a blanc screen with code running down it that never ends that looked like this:
1324.5243
  at status: [drdy]
  something error, logical block at 115123462
ect ect
it just repeats and the number in front gets longer, i think its the seconds since boot because it increases at about that rate

what am i doing wrong? i though it just boot from cd and install, what else is there too it?

---

### Post by mtopro on 2009-02-23
There is not much else to it.  For me the startup/install was pretty straight forward, however when I upgraded my Compaq Desktop to 8.10 I also had dardy errors and similar problems.

My recommendation would be to download and try out 8.04 Hardy Heron.  You can find it here:
[http://releases.ubuntu.com/8.04/]("http://releases.ubuntu.com/8.04/")

8.04 installs on my older computers without any issues.  Good luck.

---

### Post by jchiar on 2009-02-24
The BIOS should be adjusted to boot from CD. 
Usually that is hold Del key at Windows boot. Not always, but often that is it, depends on a lot of other stuff. you have to find that out for your Motherboard, Computer type and such. Try computerhope.com for that.
Or look at one of the excellent write ups on How To Install,
[https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)
[https://help.ubuntu.com/8.10/installation-guide/i386/install-overview.html](https://help.ubuntu.com/8.10/installation-guide/i386/install-overview.html)
There are guides for every distro. 
Sounds like the BIOS settings or some hardware/software error or setting that may need adjusting, this can be undone at any point after install. 
The external hard drive that was laying around has a Windows MBR or boot.ini that could be causing the conflict. This sounds like a Master/Slave and or Boot Device=s.
I kind of agree with the 8.04 call as was suggested, then again I have seen this happen on many Linux installs.
If you notice on all of these Linux install guides, it repeats and repeats , make a back up. Start there so you do not loose anything, that goes for Apple,Windows, Linux, BeOS, Amiga or anything.

---

