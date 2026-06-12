---
title: "grub &quot;unknown filesystem&quot;"
date: 2010-07-17
forum: Hardware
---

### Post by mlinchits on 2010-07-17
I run the system off of a usb hard drive. The drive was originally partitioned between kubuntu and a non-bootable ext4 file partition that I set up myself. After changing just the non-bootable partition to ntfs, I get a grub error "unknown filesystem." What are the basic steps to resolving this. Do I need to reinstall grub or add a new grub menu file? 

thanks

---

### Post by ajgreeny on 2010-07-17
If it's grub2 you just need to run ```
sudo update-grub
``` in terminal.

---

### Post by mlinchits on 2010-07-18
this is the output (i am working from a live cd with the harrdrive attached via USB by the way) :

grub-probe: error: cannot find a device for /.

---

### Post by ajgreeny on 2010-07-18
Yes, it looks as if you may need to reinstall grub with the live CD.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
there is a link in this thread to grub2 method which is different to legacy grub.

---

### Post by mlinchits on 2010-07-18
thanks.  unfortunately "find /boot/grub/stage1" returns "Error 15: File not found." The more complicated alternative tips at the bottom of the article return errors also.

---

### Post by ajgreeny on 2010-07-18
I can't think what else to suggest.

Sorry!

---

