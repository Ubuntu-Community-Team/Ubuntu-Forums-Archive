---
title: "FSF Privacy Key"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by djotaku on 2008-02-09
I recently got my FSF USB key and I was trying to use it on my Ubuntu laptop.  First I changed the mount point to /media/usbdisk as the scripts on the USB key require.  Then I run it an it runs, but nothing can be saved on the usb key.  When I try to create a gpg key, it doesn't work.  When I try to set up the password manager, every action is cancelled.  Nothing saves.  

Any luck getting this to work?

---

### Post by db0 on 2008-03-14
I can confirm that I have the exact same problem. First I changed the mount point by following the instructions [here](http://ubuntuforums.org/showthread.php?t=667455&highlight=usbdisk+mount+point) but I cannot create a passwords file or pgp keys :(

---

### Post by kevdog on 2008-03-15
Can you post 

mount

---

### Post by db0 on 2008-03-15
Relevant entry after running mount
```
/dev/sdc1 on /media/usbdisk type vfat (rw,nosuid,nodev,fmask=0000,dmask=0000)
```

The fmask and dmask are what I used in the mount options to allow rw. It doesn't work without them either.

---

### Post by kevdog on 2008-03-15
Can you save any file to this usb stick?

---

### Post by db0 on 2008-03-16
Yes. After I changed the dmask, I can copy files to it

---

### Post by kevdog on 2008-03-17
Things are working now?

---

