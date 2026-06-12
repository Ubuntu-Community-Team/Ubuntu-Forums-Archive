---
title: "Transferring hard drive to new computer.  Help?"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Infran on 2009-06-13
I just got a couple computers.  They're both Pentium4 with 512 MB memory and a blank 40 GB HD.  One is a 2.2 Ghz Dell (it says it's a DHM model - I don't know how else to identify it) and the other is a 2.4 Ghz that says "Power Star" on the front.

I have an 80 Gig drive with Ubuntu 9.04 on it that I was using in an older 1.4 Ghz Intel.  I want to transfer the drive, physically, and use it.  For various reasons, I'd prefer to have it in the Dell.

I actually already put the drive in the Dell.  It's set to cable select and is currently the master drive.  When I boot of the machine, however, it briefly shows the Intel logo (if I recall) and then it changes to a black screen with a flashing text marker... the little white underscore-thingy.  (Trying to boot off the blank disc, accidentally or otherwise, asks if I want to attempt to boot again or do stuff with the BIOS.)

Like I said, if at all possible, I'd like to be able to use the drive at it is, preferably in the Dell.  How can I do this?

If I *have* to do a clean install, is there a way to transfer all the data as it is, username, settings, and whatnot?

---

### Post by cariboo on 2009-06-13
I would suggest you have a look at the jumpers, I personally have never had much luck with cable select, I usually just jumper for master or slave as needed. Once you have the jumper problem corrected, make sure the drive is detected in the BIOS correctly. 

I've done what you want to do many times, and never had a problem.

---

### Post by ajgreeny on 2009-06-13
It is also possible that you may need to run the live CD and reinstall grub.  It will depend very much on the setup of the computer from which you took the drive, but it should be possible to get it to boot, even if you then need to sort out graphics driver problems.

---

### Post by Infran on 2009-06-14
Okay, the drive that was blank is no longer blank.  Windows XP is installed on it.  The Ubuntu HD is currently disconnected, but we're planning on making it a secondary drive for double-booting.

Will it need to be set to 'slave'?  It's just that the particular drive I have Ubuntu on does not show the jumper settings for 'slave,' just 'master,' 'cable select,' and 'limit to 32 Gig.'  That, plus the fact that the other drive was (and is) on 'cable select,' is one big reason why I set it to that.

But yes, I looked when the BIOS was up, and it looks like it detects the drive properly.

Anyway, my install disc is actually for Intrepid instead of Jaunty, so I'm downloading the .iso just in case.  I'm downloading the alternate install because it the Dell didn't seem to like the graphic install.  So, how would I re-install grub, assuming that is the case?  Would I just select 'driver install' or something?

---

### Post by ajgreeny on 2009-06-16
With all the disks attached to the computer, just go ahead and install ubuntu to the empty disk, using the default way for ease, if you prefer, but make sure you use the correct disk when you get to the partitioning stage.  The install will, or should take care of grub installation to the windows MBR, and that will allow you to choose OS at boot time from the grub menu that appears.

If anything goes wrong, post back again and we'll try to help you out further.

---

### Post by Infran on 2009-06-17
There is no blank disc anymore.  To quote myself:

> **Infran said:**
> Okay, the drive that was blank is no longer blank.  Windows XP is installed on it.

And did I mention that I'd prefer not to do a re-installation, if possible?  I just want to get the two drives as they are both working in this machine, and since I'm not very familiar with Linux in general, and neither is anyone else in my house, I'd like to ask how to do it to reduce the chance of having (more) stuff go wrong, and wasting burnable discs.

So can you redo grub from the alternate install disc without touching anything else?  If so, how?  And how should I set the jumpers and whatever-else so that I can boot from either disc?

---

### Post by Polaris96 on 2009-06-17
don't worry about which IDE drive is master or slave.  Those terms are ancient and a little misleading.  Here's why: If you go into your BIOS setup, usuay by pressing DEL right after you power up, you will see a list somewhere called "boot device priority" or some such.  

If you want to make grub boot on startup, the Linux drive must be higher on the list than the windows drive.  If your system is REALLY old, you'll have to switch jumpers cables, etc, but I really doubt that will be necessary.

---

