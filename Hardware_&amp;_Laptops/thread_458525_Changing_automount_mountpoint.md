---
title: "Changing automount mountpoint"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by Mets on 2007-05-29
I have an external hard drive from Western Digital that I often use on my laptop.  Whenever plugged in, the device is identified as "WDC Combo" and Ubuntu mounts the device to "/media/WDC Combo".  This however seems to cause a lot of problems because of the space in the word "WDC Combo."  I always seem to get errors when I'm doing things like compiling, etc. because it always tries to access /media/WDC instead.  Is there a way that I can change the name to something like /media/WDC_Combo or /media/WDCCombo, etc.?  Thanks.

---

### Post by taurus on 2007-05-29
Just change the volume label of the drive from "WDC Combo" to "WDCCombo" or whatever you want to call it.  Is it ntfs filesytem?

---

### Post by Mets on 2007-05-29
thanks taurus.  I'm not sure if FAT32 or NTFS.  How would I change the volume label though?

---

### Post by taurus on 2007-05-29
Whether it's ntfs or fat32, the easiest way is to connect it to a Windows machine and change the volume label of it.  Otherwise, you can try using gparted (probably best to do that from a LiveCD) to see if you can change it that way.

Try Windows first if you have XP.

---

### Post by Mets on 2007-05-29
Thanks taurus that worked, it took one second in XP.  Why is it so hard to do in Ubuntu

---

