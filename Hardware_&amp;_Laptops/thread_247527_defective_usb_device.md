---
title: "defective usb device"
date: 2006-08-30
forum: Hardware &amp; Laptops
---

### Post by Denn1s on 2006-08-30
Hello everyone, ive got a 256 mgs Markvision USB memory stick that isnt workin properly, i dont knw why, i just wondered if there was a salvation for it. Could anyone give me some assistance?

this are some of the errors i get:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

$ fdisk /dev/sda
Unable to read /dev/sda

$ mkfs -t vfat -I /dev/sda
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: failed whilst writing reserved sector

$ dmesg
...
[17189822.064000] sda : READ CAPACITY failed.
[17189822.064000] sda : status=0, message=00, host=7, driver=00
[17189822.064000] sda : sense not available.
[17189822.064000] sda: Write Protect is off
[17189822.064000] sda: Mode Sense: 00 00 00 00
[17189822.064000] sda: assuming drive cache: write through
... (lots o times)

i know it may be not worth it but if there is an easy solution ill take it.
thanks in advance.

---

### Post by encompass on 2006-08-30
Don't know how to do it if it is possible in linux... But I would try formating it with fat32 again.
Or if you just use it with linux... try in a linux filesystem like reiserfs.

---

### Post by Denn1s on 2006-08-30
$ mkfs.reiserfs -f /dev/sda
...
bread: Cannot read the block (0): (Input/output error).
Aborted
...

$ mkfs.reiserfs -f -b /dev/sda
mkfs.reiserfs: strtol is unable to make an integer of /dev/sda

im beginin to lose hope... thanks anyway, even mkfs tells me to buy a new drive... :p

---

### Post by encompass on 2006-08-30
yup... they are getting cheaper all the time.

---

