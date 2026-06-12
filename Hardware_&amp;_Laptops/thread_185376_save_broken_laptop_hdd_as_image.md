---
title: "save broken laptop hdd as image"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by cselik on 2006-05-31
my friend has never been burning backups, and the worse scenario happened: her laptop hdd broke a week before she has to give in her diploma work. Nothing printed yet... She has 2xfat32 partitions there.
I took it out and bought an ide adapter to connect to my desktop, try to save as much as i can to an image file i can browse later. The only way bios could recognise the hdd was to use an old 40 pin cable (not the new 80 pin it wouldnt recognise it then), and it wants to be alone on the secondary bus, as a master.

ubuntu says this on boot:

Buffer I/O error on device hdc5, logical block xxxxx24..31 
over and over again

how can i make it ignore these errors, get the prompt and try to mount the fat32 partitions?

---

### Post by Clunsford on 2006-05-31
I would try using ghost to copy an image from that HDD to a less finiky drive... then try reading it.

not very scientific but fixing stuff aint exact'

---

### Post by schdefan on 2006-05-31
is it recognized in the bios as correct drive?

---

### Post by cselik on 2006-05-31
[QUOTE=schdefan]is it recognized in the bios as correct drive?[/QUOTE]
yes, it is a toshiba, 40 gigs, as it is printed on it

---

### Post by IYY on 2006-05-31
If all else fails, try following the instructions in this e-book. 

[http://www.governmentsecurity.org/forum/index.php?act=Attach&type=post&id=4036](http://www.governmentsecurity.org/forum/index.php?act=Attach&type=post&id=4036)

---

