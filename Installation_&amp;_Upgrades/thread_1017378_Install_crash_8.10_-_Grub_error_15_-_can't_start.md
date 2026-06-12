---
title: "Install crash 8.10 - Grub error 15 - can't start"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by prj44 on 2008-12-21
My laptop has happily had a dual-boot Ubuntu with XP. I wanted to go to new version: 8.10, using a CD I have used on another machine. 
In XP, I deleted the Ubuntu partitions, then re-booted Live CD to install 8.10. Received an I/O error reading from CD, reverted to Live CD. (Install was about 70% complete.) Tried to run install. Grub error 15 and everything stops.

Power down, power up; boot from HD.  Grub error 15. Now I can't even get into XP!

HELP!

---

### Post by caljohnsmith on 2008-12-21
If you want to be able to boot into Windows, you could download and use the [Super Grub Disk]("http://www.supergrubdisk.org"); or to restore a Windows MBR (Master Boot Record) to the HDD so you can boot directly into Windows, you can do the following from a terminal (Applications > Accessories > Terminal) from the Live CD:
```
sudo lilo -M  /dev/sda mbr
```
How about giving that a shot and let me know how it goes.

---

### Post by prj44 on 2008-12-21
Thank you.  Unfortunately, the Live CD won't boot either ... it proceeds to the same Grub error 15 and does not go any further.

I presume I have a mangled MBR to thank for this.  My plan was to use a Windows utility to fix the MBR.  (Presuming I can boot from a CD and if not that, from a floppy.)  That should allow me to remove the partially completed installation and start again.

Is there a file on the first partition (other than MBR) that I need to be aware of as well?

Thanks in advance.
 (What a way to get my Linux skills ....)

---

### Post by caljohnsmith on 2008-12-21
> **prj44 said:**
> 
Is there a file on the first partition (other than MBR) that I need to be aware of as well?

Is the first partition Windows? It sounds like the main goal at this point is to reinstall a Windows MBR so that you can at least try to boot straight into Windows. Fortunately there's no files you need worry about when you install a Windows MBR. How did you previously install Ubuntu? Do you have any Live CD's that will boot? Did you try the Super Grub Disk? The Super Grub Disk will also let you restore a Windows MBR.

---

### Post by prj44 on 2008-12-21
Sorry, I should have provided more detail.  The Laptop is a Sony Vaio, containing a 5 GB partition with the Windows source files, two NTFS partitions (Windows C and D) and a fourth partition that has been created for Ubuntu.  (I think there is a four partition limit! Creating the Swap file would put it over that number ... perhaps that is the cause.)

My first objective is to get back to my presumably still stable Windows, then add the Linux material.  Perhaps I have to reduce partitions!

Thanks for your help.

---

### Post by prj44 on 2008-12-21
Unfortunately, once I got a different Live CD (8.04) to work, the command:
sudo lilo -M  /dev/sda mbr

produced the result "Command not found."

???

---

### Post by caljohnsmith on 2008-12-21
Do you have internet access from the Live CD? If so, instead try:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
And please post the output if you get any errors.

---

### Post by prj44 on 2008-12-21
Your last instructions worked like a charm.  No errors at either stage.  Final result: 0 + 1 records in, 0 + 1 records out, 410 bytes copied. 

Result: clean Windows boot!

Thanks for your assistance.

I still want a dual-boot capability on the laptop, but I am leary of another try just now.  I suspect grub and I suspect the NTFS file system; so I am generally paranoid.  Has this problem proved to be a frequent one?  Any added reading most welcome.

Thank you again.

---

### Post by caljohnsmith on 2008-12-22
It sounds like your original problem was about getting the 8.10 Live CD to work, true? Did you check the md5sum of the ISO image before burning it? And did you try burning the ISO at a slow speed, like 4X? That might help. If you previously installed Ubuntu successfully, I don't think you have to be too worried about doing it again. I would recommend using the "manual" partition option in the installer, and then you can make sure you install Ubuntu to new partitions and not touch your Windows partition. Here are a few guides that might help:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html) (manual partition setup)
[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html) (using gparted first)

Anyway, let me know how it goes.

---

