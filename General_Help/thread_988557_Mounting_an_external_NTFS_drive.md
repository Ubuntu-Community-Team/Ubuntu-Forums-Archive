---
title: "Mounting an external NTFS drive"
date: 2008-11-20
forum: General Help
---

### Post by rmcellig on 2008-11-20
I am running Ubuntu 8.10. I have an external NTFS drive that mounts fine on my Mac but not in Ubuntu. What should I do to get it to mount properly?

---

### Post by john183 on 2008-11-20
What is the error that you are getting when trying to mount the NTFS drive?
With the info from the error i can tell you how to fix it.

---

### Post by dexter on 2008-11-20
Check the output of dmesg. It should list the detection and mounting of the external drive and possible errors.

---

### Post by taurus on 2008-11-20
See if you can mount it by hand from a terminal.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows
```
Assuming that /dev/sda1 is your external harddrive.

---

### Post by rmcellig on 2008-11-20
The problem I have is that the drive doesn't even mount even after restarting the PC. Mounts fine on my Mac though.

---

### Post by rmcellig on 2008-11-20
Here is the error I receive:

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by aeronotix on 2008-11-20
Gonads and Strife.

[http://ubuntuforums.org/showthread.php?t=981050](http://ubuntuforums.org/showthread.php?t=981050)

---

