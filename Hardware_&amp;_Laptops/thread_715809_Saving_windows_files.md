---
title: "Saving windows files"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by saxxist on 2008-03-05
I have a Dell Inspiron 600m with a bad hard drive, unable to access the config.sys to boot the OS (WinXP).  How can I use the download to save the data files on the laptop?

---

### Post by taurus on 2008-03-05
Boot from Ubuntu LiveCD, mount your windows partition somewhere, and then access it to back up your important files from it.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows
ls -la /media/windows
```
_Assuming_ your windows is on /dev/sda1.

---

### Post by saxxist on 2008-03-05
Did that, but I believe that I may not have set up the Live CD correctly.

I downloaded the Xubuntu file (669mb ISO file), and copied it to a CD.  That is the CD that I used on the laptop.  Is there a step in the middle that I missed?

Thanks!

---

### Post by taurus on 2008-03-05
How did you "copy" the ISO image to a CD?  You need to burn the ISO image as an image file with a software, not as a data file.  So, if you just copied that one large file from a harddrive to a CD, then you won't be able to boot from it.  You must burn the ISO image with whatever app that you use as an image file.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

Then, you need to go into the BIOS and set CDROM as the first bootable device.

---

### Post by saxxist on 2008-03-05
And which file is it that I need to burn?  

Sorry - I am brand new to Ubuntu, not a compu-geek, but I can work my way around things if the instructions to do so are clear enough.  

Thanks.

---

### Post by taurus on 2008-03-05
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-desktop-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-desktop-i386.iso)

---

