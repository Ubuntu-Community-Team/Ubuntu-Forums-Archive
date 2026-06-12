---
title: "New install, now my 2nd hd isnt visible"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by Mr.Auer on 2005-07-05
I have 2 hard drives, 30gb and 120gb. Linux is on the smaller one, all my storaged files on the 120gb one. I re-installed linux, didnt do anything to the big drive, and now i cant see the other drive on my ubuntu. It is visible in device manager, but it doesnt have a mount point? its mount point on previous install was /varasto, but i cant get it mounted with that now. Im new to linux, so pls tell me what to do to see the other drive..

---

### Post by darrell on 2005-07-05
try this:
open a terminal
recreate your mount point:
```
sudo mkdir /varasto
```
find out what your second hard drive is known as to Linux:
```
sudo fdisk -l
```
you should be able to work out from this whether it's /dev/hdb1 or whatever. I'll use /dev/hdb1 as an example
inform ubuntu about your 2nd hard drive
```
sudo gedit /etc/fstab
```
add a line to this file:
```
/dev/hdb1       /varasto          auto        noauto,users,rw,umask=002  0   0
```
save and exit

now go to Places-Computer - it should show up now.

---

