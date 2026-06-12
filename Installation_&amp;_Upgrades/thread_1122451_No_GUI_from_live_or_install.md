---
title: "No GUI from live or install"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by :Matt: on 2009-04-11
I've been running Ubuntu on my Desktop for about a semester, and I decided to install it on my laptop this weekend. I'm using an ASUS G2K, which has an ATI Mobile Radeon 2600 graphics card.

Anyway, I downloaded the Ubuntu 8.10 32bit ISO, and I am trying to install the OS now. When I try to do just a live boot I get the Ubuntu splash screen, then a black screen. I can press alt+f1 to get to a shell. The same thing happens when I select "Install Ubuntu".

After bringing up a shell, if I try startx I get these errors:

Saw signal 11. Server aborting.
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Enable CRTC 0 success
Unblank CRTC 0 success
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error

I also tried installing Ubuntu from my Windows OS, but when I tried to start up Ubuntu I had the exact same problem.

Edit: I downloaded the Desktop Edition, I burned the ISO to a CD, I checked the CD for errors

If I try startx in safe graphics mode I get the no screens found error.

---

### Post by :Matt: on 2009-04-11
bump.

No ideas? I was planning to get some work done this weekend for my research class and for that I need Ubuntu working, but it looks like I won't be able to do anything.

---

### Post by :Matt: on 2009-04-11
bump

---

### Post by :Matt: on 2009-04-11
bump

---

### Post by kjaada on 2009-04-11
Had a similar problem with the live disk then downloaded the alternate iso.
The install went good and I now have 9.04 working 100%

---

### Post by :Matt: on 2009-04-11
By alternate iso do you mean the text version? If so, what did you do after installing to get the GUI desktop?

---

### Post by cariboo on 2009-04-11
The alternate install cd does a full installation, including the desktop. You could also try starting the LiveCD in safe graphics mode. Press F4 and select safe graphics mode and then continue booting.

Jim

---

### Post by :Matt: on 2009-04-11
As stated in my first post, I have already tried starting the LiveCD in safe graphics mode, and I get a "no screens found" error.

Edit: I'm burning the alternative installer now.

---

### Post by :Matt: on 2009-04-12
With the text installer, it won't let me make a new partition or mount to that partition with any format.

---

### Post by toupeiro on 2009-04-12
Did you try some of the usual things when googled for this problem like  pci=noacpi or apic=off in the boot options of the CD install?

---

### Post by :Matt: on 2009-04-13
> **toupeiro said:**
> Did you try some of the usual things when googled for this problem like  pci=noacpi or apic=off in the boot options of the CD install?

I've been doing a lot of googling but I haven't seen that recommendation, nor do I know what it does. However, setting pci=noacpi seems to be working. It's just finished repartitioning with the GUI installer now.

---

