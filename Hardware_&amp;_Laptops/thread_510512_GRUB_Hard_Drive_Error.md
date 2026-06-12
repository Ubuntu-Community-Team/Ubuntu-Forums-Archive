---
title: "GRUB Hard Drive Error"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by Exeneva on 2007-07-26
Hello everyone!

     I run two hard drives in my computer. I had Windows XP SP2 installed in my first one and then I installed Ubuntu onto my second one. After installing Ubuntu, Windows XP no longer would boot. After removing the second hard drive I get a "GRUB hard disk error." I removed Ubuntu from my second hard drive and installed Windows XP on it, hoping that if I booted the computer with both drives connected I would be able to access my files. Unfortunately, I cannot access them because they are under a password-protected login; when I try to access the F:/Documents and Settings/Exeneva folder a pop-up displays telling me that access is denied.

     I've tried fdisk/mbr and fixmbr as well as fixboot; but none of those have worked. I really don't want to wipe my first hard drive. Is there any way to fix this?

                      Thanks,

                     Yang

---

### Post by ianare on 2007-07-27
You will probably need to use GRUB to boot your windows partition.

Make a grub boot floppy (you can do this from the ubuntu live CD) and boot into windows:
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

extra help:
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)


Worst comes to worst, you can use ubuntu to access you windows files (it will not care about password protected NTFS)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

