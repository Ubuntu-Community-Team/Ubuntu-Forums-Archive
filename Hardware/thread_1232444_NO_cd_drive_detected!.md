---
title: "NO cd drive detected!"
date: 2009-08-05
forum: Hardware
---

### Post by compucon on 2009-08-05
I have a LG cd burner, a Sony DL DVD burner, a samsung floppy drive and a 160 GB maxtor internal, second hard drive. ubuntu dosen't see ANY of them. however it does see the floppy drive, but it's not working. the floppy dive has a green light that's ALWAYS on. How can i get everything to work?:confused:

---

### Post by ajgreeny on 2009-08-05
If this is a new install it is very strange as the hard drive must have been detected in order to install to it and the CD drive must work, or you couldn't have read the CD to install in the first place.

Have you done anything strange to your /etc/fstab file in any way at all, as that is the configuration of the drives and what is mounted at boot time?  Run ```
sudo fdisk -l
``` in terminal and then put a CD in and run ```
mount
``` to see if the system does see the drive.

---

### Post by compucon on 2009-08-11
well, i don't know what that /dev/????? dir is. and the BIOS sees them, and the installer saw them. but the installed system dosent. and with the commands you gave, i didn't know how to tell.

---

### Post by compucon on 2009-08-11
also, the install is about a month old.

---

### Post by J A Smith on 2009-08-11
I had a similar problem with my DVD drive, that however was a loose connection. (The drive needed sliding back into place). It was a problem both in Windows and Ubuntu. Since your problem is happening on a number of devices, it seems unlikely to be the case here.

---

