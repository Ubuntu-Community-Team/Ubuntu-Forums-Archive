---
title: "Installation on a portable hard drive"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by DarkLinksSpirit on 2009-04-11
I have just recently heard of ubuntu moments before my dad bought a portable hard drive to back up some files. my question is if it is plausible to install ubuntu on that hard drive

so far we have attempted to:
download ubuntu
decompress file
install setup

the startup would for aboout 2 seconds start up ubuntu normally.
after this the command list will pop in with some things about grub.

so far we have no clue what the problem is.

---

### Post by RedSingularity on 2009-04-11
Where did you download the ISO file?  

Have you burned it to a CD-r and booted from it while the portable HD is plugged in?

---

### Post by DarkLinksSpirit on 2009-04-11
i am pretty sure i received the iso file from ubuntu.com

the download was performed from a usb thumbdrive (2 gig) at the root of the drive

---

### Post by RedSingularity on 2009-04-11
I am guessing you made the Thumb drive bootable?

---

### Post by DarkLinksSpirit on 2009-04-11
yes, i installed from the usb toward the portable drive

---

### Post by RedSingularity on 2009-04-11
Ok so you have it installed to the external HD already?  Can you say what grub is spitting out or is it too long to type in?

---

### Post by DarkLinksSpirit on 2009-04-11
using a command prompt after a startup attempt it scrolls:

loading please wait...

BusyBox v10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands

[    11.027344] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[    11.032272] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[    11.035763] sd 4:0:0:0: [sdd] Assuming drive cache: write through

(initramfs)_

---

### Post by RedSingularity on 2009-04-11
If you hit Ctl+Alt+F1 at this point does anything happen?

---

### Post by DarkLinksSpirit on 2009-04-11
nothing at all.

there was also an accidental dawnload which was cancelled 2 minutes in. we think that ubuntu is attempting to run on the cancelled installment.

---

### Post by RedSingularity on 2009-04-11
Well that may be then.  BusyBox runs if there is an error in the installation.  It is like a "Recovery prompt".  It looks like that prompt is running in your case because something didnt install correctly.  Why not try a complete reinstall onto the HDD?  At the live CD you can also pick the option "Check CD for errors".  This will make sure you have everything you need.

---

### Post by DarkLinksSpirit on 2009-04-11
probably a good idea.

---

### Post by DarkLinksSpirit on 2009-04-11
after retrying a few times and removing the boot usb(thumb), we received this from grub:

GRUB4DOS 0.4.4 2008-10-27, Memory:634K / 1013M, CodeEnd: 0x42910
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exists]

grub>

---

### Post by lindsay7 on 2009-04-11
Take a look at "unetbootin". you can find in on the internet. That should install on you portable hard drive.

---

### Post by DarkLinksSpirit on 2009-04-11
what difference does it contain versus the intitial download on ubuntu?

---

### Post by lindsay7 on 2009-04-11
It will automatically install Ubuntu or whatever you want and make it bootable. You do not have to download the ISO file or do any other setup work.

---

### Post by Muscovy on 2009-04-11
> **lindsay7 said:**
> It will automatically install Ubuntu or whatever you want and make it bootable. You do not have to download the ISO file or do any other setup work.
So you need to install nothing on a computer to be able to boot from the EHD?

---

### Post by lindsay7 on 2009-04-11
Thats correct. You just need to reset the bios so that your computer will boot from the ehd first. Set the boot preference in bios to boot 

1. ehd
2. cd/dvd
3. internal hard drive

or whatever you choose. You can change it back to your regular start up when you are done.  Just play with the start order until you get it the way you want.

---

### Post by Muscovy on 2009-04-11
I tried unetbootin, but at the startup of loading from the EHD I recieved "invalid tables".

---

### Post by lindsay7 on 2009-04-11
You probable have some files on there from you first attempt to put Ubuntu on it. I would format the external drive and try again.

---

### Post by Muscovy on 2009-04-11
Yep, I had wubi files still there, and I can see how that complicated things!

---

### Post by Muscovy on 2009-04-12
AHH!
I removed all Ubuntu install files and reinstalled, but I still got the tables error.
What does it *mean*?

---

### Post by Muscovy on 2009-04-12
I cleared all Ubuntu related things, but I still got 'partition table error'.

---

### Post by lindsay7 on 2009-04-12
I am not sure what is going on with this drive. This is what I would do.

1. Forget about installing Ubuntu for now, and just get the drive back to normal. They you can decide what to do with it.

2. Format the the drive with Windows or Gparted. I would not make any extra partitions, just format the whole drive. I would format it as Fat32. That way you can use it for Windows or Ubuntu (if you install Ubuntu it will change to a ext3 partition anyway).

If doing this does not get this drive back to normal. I would start a new thread on this forum and describe your situation and see if you can get some help from there.

---

