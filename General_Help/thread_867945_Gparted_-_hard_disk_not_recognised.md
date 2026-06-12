---
title: "Gparted - hard disk not recognised"
date: 2008-07-23
forum: General Help
---

### Post by MrDidot on 2008-07-23
[FONT="Arial"]I installed ms-sys and now my computer does not recognise my hard drive on boot.

I can see the filesystem through File Browser but can't reinstall Ubuntu using LiveCD as there are no visible partitions to mount the program.

The computer is an old Pentium III but I love it.

Any way to turn back the clock?[/FONT]

---

### Post by jimv on 2008-07-23
When you say there are no partitions in Gparted, is it showing the whole drive as "unallocated"?

---

### Post by MrDidot on 2008-07-23
Jimv,

[FONT="Arial"][/FONT]When I run GPArted it scans the drives and concludes with "No devices detected".

Which is odd cos I can browse the hard disk directories and files through File Browser ....?

---

### Post by jimv on 2008-07-23
Wow, well that's odd to say the least.  I didn't think formatting the MBR would make the drive invisible to Gparted. Hmmm.

You might want to try booting from a Super Grub Disk and restoring a Windows MBR with it.

Here's the URL to download the ISO:
[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by MrDidot on 2008-07-23
I launched Super Grub Disk but for some reason my keyboard is diasbled so I cant press return to boot the OS.

I can use the keyboard to get into Bios before Super Grub Disk loads but it wont work afterwards.  

Maybe I've got a load more problems than I first thought.

---

### Post by MrDidot on 2008-07-23
i can't get the computer to recognize the keyboard at the crucial moment send a return signal to launch the OS in Super Grub.

Is there any fix for this? THe keyboard is a usb.  I've tried using the other ports.

---

### Post by confused57 on 2008-07-23
> **MrDidot said:**
> i can't get the computer to recognize the keyboard at the crucial moment send a return signal to launch the OS in Super Grub.

Is there any fix for this? THe keyboard is a usb.  I've tried using the other ports.
You could go into your bios setup, see if there is a setting for something like USB Legacy, which you can try enabling.

---

