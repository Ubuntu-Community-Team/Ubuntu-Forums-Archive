---
title: "Accessing Linux files from Windows on on Wubi installed Ubuntu?"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by aeiouna on 2009-09-06
I'm currently running a dual boot Windows Vista/Ubuntu 9.04 system, having used Wubi to install Ubuntu.

I know it's possible to access my Windows files while booted into Ubuntu by accessing the /host and /media files, and have done so many times.

What I'd like to know if it's possible to go the other way around, and access my Ubuntu files while booted into Windows?

---

### Post by ronparent on 2009-09-06
Not if the files are on a linux formatted partition (ext2, ext3, ext4, etc.).

---

### Post by Lerxst51 on 2009-09-07
Try looking at the links here:

[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) can I access the Wubi files from Windows?

---

### Post by aeiouna on 2009-09-10
Okay, so it looks like I need to install a second program?

---

### Post by Mark Phelps on 2009-09-10
> **aeiouna said:**
> Okay, so it looks like I need to install a second program?

Yes ... because MS Windows is not able to read other filesystems without additional help.

---

