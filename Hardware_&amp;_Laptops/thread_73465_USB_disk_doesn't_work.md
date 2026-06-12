---
title: "USB disk doesn't work"
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by juantxorena on 2005-10-09
Greetings.
My USB disk doesn't work (as you can read in the title). In the past, it used to work.
I can mount it, but if I try to copy something from/to the usbdisk, I get an error:
```
cp: reading «/media/usbdisk/xxxxx»: Input/ouput error
```
 I have this line in /etc/fstab:
```
/dev/sda1       /media/usbdisk       vfat    rw,user,auto,noatime
```
Any ideas?

P.D. Sorry for my english

---

### Post by localzuk on 2005-10-09
Have you tried it in another machine? This sounds like a classic 'dead disk' response...

---

### Post by juantxorena on 2005-10-09
It works in windows, in the same computer.

---

### Post by juantxorena on 2005-10-10
Nobody?

---

