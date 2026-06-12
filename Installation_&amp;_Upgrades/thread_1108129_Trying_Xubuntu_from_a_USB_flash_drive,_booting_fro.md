---
title: "Trying Xubuntu from a USB flash drive, booting from floppy"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by Mr Henderson on 2009-03-27
I want to try Ubuntu on an old PC. I've run Xubuntu from a live CD and now I'd like to try from a USB flash drive so it'll save changes. But there's no BIOS option on my PC to boot that way. Is there any simple way to make a floppy or CD which will find the drive and start Xubuntu, or any other variant? I've found enough on the forums and elsewhere to suggest it might be possible.

Note that I know almost nothing about Linux.

Two things I've tried that didn't work:
1. SuperGRUB floppy (used as described here: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB))
2. Modified Wakepup floppy as described here: [http://ubuntuforums.org/showthread.php?t=573508&page=2](http://ubuntuforums.org/showthread.php?t=573508&page=2)

---

### Post by Mr Henderson on 2009-03-31
I did it, despite my ignorance of Linux. I made a boot CD by following the instructions at: [http://www.pendrivelinux.com/usb-boot-cd-for-xubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-xubuntu-810/)
There are instructions elsewhere on Pendrivelinux.com for doing the same thing for Ubuntu and other variants.

You may find that some commands are not executed because you need administrator privileges. Unfortunately I've since discovered that the command I used to enable these commands is considered dangerous and is not to be advised. However, with a bit of research it should be possible to find a safe way.

Step 4 opens the text editor window. Start step 6 in a new terminal window.

Watch out for typos in the instructions - not too hard to spot one in steps 7 and 8.

I ended my Xubuntu session without burning the CD and couldn't find the ISO subsequently. Find it during the session, then copy and save it somewhere convenient on your hard drive. Then if the burn doesn't go right (I had problems with Ubuntu) it's there to try again later (I did it in Windows).

I was disappointed by how slowly Linux ran from the flash drive - slower than from CD, though of course it does make it possible to save changes.

---

