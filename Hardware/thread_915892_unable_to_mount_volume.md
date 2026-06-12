---
title: "unable to mount volume"
date: 2008-09-10
forum: Hardware
---

### Post by geoffpl on 2008-09-10
Ubuntu 8.04 - Dell Inspiron 1405 operated by a Neewwwwbieee - (me)
I connected a USB external drive - It shows up under 'Places" but will not allow access to files stored there - error message "Cannot mount volume"

---

### Post by geoffpl on 2008-09-10
After some digging I was able to find an answer here in the forum that work like a charm for me. Thanks goes out to all. :KS

Quote:
First, just make sure the device is identified as /dev/sdb1 using
Code:

sudo fdisk -l

Copy and paste to avoid typos.
Now run
Code:

sudo apt-get install ntfsprogs

which will install a program which includes a repair utility. Run the utility (assuming the drive is sdb1)
Code:

sudo ntfsfix /dev/sdb1

With luck, this will repair and mount the drive.
Then restart your computer. Who need windows!!

---

