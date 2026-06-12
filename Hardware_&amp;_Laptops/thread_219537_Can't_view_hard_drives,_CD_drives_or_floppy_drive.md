---
title: "Can't view hard drives, CD drives or floppy drive"
date: 2006-07-20
forum: Hardware &amp; Laptops
---

### Post by Lard on 2006-07-20
I've just started running Ubuntu from the CD.

Trying to browse the computer I can't view contents of any drives.  I get the error message:

"Unable to mount the selected volume
error: device /dev/hda5 is not removable

error: could not execute pmount
"

How can I fix this problem?

thanks
L

---

### Post by StefanoCole on 2006-07-20
Open a terminal, type the following command and post its output:

$sudo fdisk -l

Stefano

---

### Post by Lard on 2006-07-20
ok, will do that when I've managed to get it to boot again - locks up after the user name/password screen

---

