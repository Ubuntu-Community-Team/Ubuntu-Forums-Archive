---
title: "problem with external hardisk"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by alsaeeam on 2007-06-03
my external hardisk is killing me.
it cannot be mounted
it says Volume is scheduled for check. Please boot into Windows TWICE, or use the 'force' monut option. 
I tried to force by using "sudo mount -t ntfs-3g /dev/sda1 /media/Maxtor -o force"

and it gave me this message
WARNING: Dirty volume mount was forced by the 'force' mount option.
fusermount: failed to access mountpoint /media/Maxtor: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda1 (Maxtor)

It was working fine a couple of weeks ago. however, I've got a new hard drive to my laptop and haven't installed Ubuntu until a couple of days ago and here we go, the external hardisk does not mount.
I tried booting into Windows twice (I felt stupid for doing that) and still nothing

---

### Post by taurus on 2007-06-03
You need to boot into Windows and unmount your external harddrive first before you shutdown Windows.

---

### Post by alsaeeam on 2007-06-04
It did not work :(

don't anybody have any idea 
especially about the "fusermount: failed to access mountpoint" part????

---

