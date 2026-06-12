---
title: "sd/mmc card access"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by nanook9_99 on 2005-03-20
I am tryng to access the sd/mmc card reader built into this laptop (compaq r3320ca).
The device shows up in Konqueror as sda1 but I get the following when I click on it.

Could not mount device

The report error was
mount: can´t find /dev/sda1 in /etc/fstab or /etc/mtab

Any ideas on how to correct this?

---

### Post by Qdlaty on 2005-03-20
Do you have any **sda** devices in /dev ??

try do this like this:
make a directory in /media for cardreadre (mine is usbcr)
run terminal and do:
*sudo mount /dev/sda1 /media/usbcr*

if it works add a line to /etc/fstab:
_/dev/sda1       /media/usbcr    vfat    user,noauto     0       0_

Assuming, you have /dev/sda1 device ;-)

---

### Post by telmo on 2005-03-20
Just a question... in case i don't have sad in /dev, do you have any idea in what to do? You see... my laptop has a 5in1 card reader, and when i plug a card ubutu (hoary) reads it untill he freezes...

Can you help?

---

### Post by Qdlaty on 2005-03-21
Could you give me some more information about your system, kernel version etc.
So far all external card readers I tried it worked OK.

---

