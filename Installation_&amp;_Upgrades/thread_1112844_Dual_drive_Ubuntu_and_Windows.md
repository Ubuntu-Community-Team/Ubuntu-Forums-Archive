---
title: "Dual drive Ubuntu and Windows"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by sgcharest on 2009-04-01
I am running a P4 dual core with 2 GB ram and Intrepid.  The drive on which Intrepid and all data and files are kept is an SDI drive (let's call it Drive A).  I have a second drive (drive B) which had XP on it as well as files which I have moved to drive A.  Although Drive B *has* windows on it, it cannot load as the drive came from another machine and the processor seems to want a new install of Windows.

I want to format drive B and then install XP on it, then dual boot Ubuntu and XP so I will have Windows for those very rare times when WINE or MON won't quite do the trick.  Here's the difficulty:  I believe that in loading dual OSs on a single drive, one must install Ubuntu *second* or Windows takes over the disk, the processor, and the world. 

This is the desired outcome:  two drive, dual boot system using Ubuntu as primary and Windows only as needed.  This, I understand, is a pretty common setup. 

Here is my plan and I invite comments, questions, or "are you kidding?" statements:
1) Using Ubuntu, wipe and format drive B.
2) Physically disconnect drive A (Ubuntu and files).
3)  Boot from my XP disk and then install XP on drive B.
4)  Reconnect drive A, switch the boot drive in the BIOS to A so I boot from Ubuntu, and then run partition as usual for two drives.

My concern is that I will not be able to run Ubuntu at all once Windows is in.  Any thoughts on my plan?  Is there another, simpler, or less hazardous way to go about this?  Or should I wait till Jaunty comes out, then load Win once it is out, and follow up with loading Jaunty.

There must be a not-too-difficult way to do this.

sgc

---

### Post by Mark Phelps on 2009-04-01
Your plan is just fine -- I have multiple drives and that's exactly how I do it.  

After you switch boot to A, you will have to manually add a stanza to GRUB to boot into XP.  But there's not much to that.  You just have to open /boot/grub/menu.lst file with an editor and add a few lines.

Question is, why are you "running partition as usual" after you have both OSs's installed?

---

