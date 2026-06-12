---
title: "how do you dual-boot windows xp with ubuntu?"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by Charity on 2009-06-05
I have two questions for anyone willing/able to help:

#1: Is there a way to dual-boot windows xp with ubuntu when your installing windows xp and already have ubuntu on your computer?

#2: How do you install windows xp when the auto-run for it doesn't work on your computer?

PS: whether or not you can help me with my problem I wish you have a good day if your reading this, just felt like typing that randomly...:D

---

### Post by tommcd on 2009-06-05
> **Charity said:**
> 
#1: Is there a way to dual-boot windows xp with ubuntu when your installing windows xp and already have ubuntu on your computer?
The easiest way to do this would be to install XP first to the whatever size partition you want, and leave the rest of the hard drive unallocated. Then install Ubuntu to the rest of the drive. You should consider using this option, since it is the easiest.
It is possible to install XP after Ubuntu. You should use a GParted or Parted Magic live CD to create a new NTFS primary partition and install XP to that. It is possible to install XP to a logical partition, but it is more complicated, so create a primary partition if you can. 
See these guides:
[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)
and this has a section on installing XP after Ubuntu:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Windows will overwrite the MBR, so you will need to reinstall grub to the MBR using the Ubuntu live CD:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
> **Charity said:**
> 
#2: How do you install windows xp when the auto-run for it doesn't work on your computer?

Set the computer to boot from the cdrom drive as the first boot device in the computer's BIOS. This should allow you to boot from the Windows XP CD. Then install XP to the NTFS partition that you created with GParted or Parted Magic.

And welcome to the Ubuntu forums!

---

### Post by Charity on 2009-06-12
Thank you very much but.....

> Set the computer to boot from the cdrom drive as the first boot device in the computer's BIOS. 

I do not know how to set the computer to boot from the CD-ROM, if this could be clarified for me it would be much appreciated.

---

### Post by presence1960 on 2009-06-12
> **Charity said:**
> Thank you very much but.....



I do not know how to set the computer to boot from the CD-ROM, if this could be clarified for me it would be much appreciated.

refer to your computer documentation to see which key or combination of keys must be pressed when booting to enter BIOS (sometimes called Setup). Once in BIOS you want to set your CD drive as first in boot order.

What make & model computer do you have?

It is easy to install XP to a machine already running windows. Just involves an extra step or two. But first let's see if you can get your CD drive to boot.

P.S. when your computer boots it should tell you what key to press to enter setup...mine says Press del to enter setup.

---

### Post by anystupidname on 2009-06-13
Regarding #2, just in case your system doesn't support booting from CD/DVD, you can use one of these boot loaders from a floppy as "jump starters":

[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)
[http://btmgr.sourceforge.net](http://btmgr.sourceforge.net)

---

### Post by jflaker on 2009-06-13
another option that I enjoy more than dual boot is to load VirtualBox and install XP as a Virtual machine.  That way you don't have to leave Linux to do something in Windows

---

