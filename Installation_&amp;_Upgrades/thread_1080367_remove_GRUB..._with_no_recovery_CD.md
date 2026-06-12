---
title: "remove GRUB... with no recovery CD"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by memilanuk on 2009-02-25
Hello all,

I have a PC that I want to clean up my Linux test stuff from and use just for XP - I have a different 'test mule' now for thrashing with Linux ;)

The only thing left is GRUB... I've done some searching, and have an idea what I need to do - get into the WinXP recovery console and fix the MBR.

Only one problem:  I don't *have* a Windows startup/install/recovery CD.  This machine is a Gateway that came with a system restore CD - basically it is a canned install CD, not a regular WinXP install CD.  'Recovery' is supposed to be done via a separate partition, so I don't have *any* Windows CDs at all.

So *now* how do I get in and clean up / reset the MBR?

Thanks,

Monte

---

### Post by Mark Phelps on 2009-02-25
I've read that the SuperGrubDisk can restore an MS Windows MBR but I've not personally tried it.  Google for that, download the ISO, and burn the disk.

---

### Post by Elfy on 2009-02-25
It does work - at least it worked when I used it.

---

### Post by memilanuk on 2009-02-25
So you did use it specifically to fix the MBR for Windows and it did work?  I had seen references to the project, but their site is apparently in the middle of a transition and a number of links (including the 'Download CD', and the documentation) don't seem to be working right... which made me a bit leery of 'em right off the bat.

---

### Post by caljohnsmith on 2009-02-25
Do you still have your Ubuntu Live CD that you can boot? If so, just run the following code to reinstall a Windows equivalent MBR to your sda drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Let me know how that goes.

---

### Post by memilanuk on 2009-02-25
Well, SuperGRUB didn't work worth a flip... sat there griping about it not being a bootable disk and looking for the floppy drive?

As it turns out... the last flavor of Linux I had on here was OpenSuSE and I had *not* removed it yet (on the to-do list)... fortunately yast keeps a copy of the original MBR and offers an option to restore it, which worked beautifully.

---

### Post by Elfy on 2009-02-26
> sat there griping about it not being a bootable disk and looking for the floppy drive You must have burnt it wrong then I would suspect.

---

### Post by memilanuk on 2009-02-26
I didn't 'burn' it, I was using the 'Auto' version from within Windows.  Downloaded it, installed it, rebooted the computer, SGD had added itself to the Windows boot list... I selected the SGD option, which ralphed as described earlier.  I rebooted and selected the normal Windows boot option, and upon startup and login SGD prompted to uninstall itself (like it was supposed to).  Then I rebooted again, selected OpenSuSE from the GRUB loader and started digging around in there until I found some applicable info (I'd also forgot I had my wifi card working inside OpenSuSE, which was handy.  Too bad dual booting just ain't much fun any more).  I restored the MBR via yast, and everything seems to be working normally.  I'll go back this morning after work and delete the Linux partitions and resize the Windows C:\ partition via System Rescue CD.

---

### Post by dsx2b on 2011-02-24
> **caljohnsmith said:**
> Do you still have your Ubuntu Live CD that you can boot? If so, just run the following code to reinstall a Windows equivalent MBR to your sda drive:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Let me know how that goes.

Thanks. This was the simpler method worked for me. No need to set the specific partition eg sda1 or sda2... just sda and the next time i booted i went straight to windows.

---

