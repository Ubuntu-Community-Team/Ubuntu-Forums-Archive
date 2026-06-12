---
title: "Trying to repartition/reformat a 200gb xbox-hdd"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by El Cris on 2006-01-30
Hey guys, I want to use the 200gb-hdd from my xbox (I don't need so much space there) in my pc now, but when i first started my computer with the hd attached to it neither windows nor linux were able to boot, so I'm just sitting here with an old knoppix-version searching for a way to make it rereadable for the pc-OSs.

I am asking here for help now because I got stuck. I used xebian xbox-linux to cfdisk that hd and create a new partition as big as the hd is. I thought I would then be able to use it in my pc but it's still not possible.

So, final question: Is there a way using knoppix to make that hd reusable/redetectable by my pc?

---

### Post by skwid on 2006-01-30
Yeah, the PC sees it as some weird partition.   You will need to boot the PC with some advanced Partitioning tool to make sure you kill the existing (unknown) partition and rewrite a new ext3 or ntfs or whatever kind of partition you want back.   


If you have tried that I am stumped.

---

### Post by El Cris on 2006-01-30
Hmm yeah, that was what I've tried, well, i didnt write a filesystem on the partition I've created, so I'll try just that when I get back from shopping. *mehungry*

---

### Post by El Cris on 2006-01-30
Ok, so far it didn't work.
The partition is still being seen by cfdisk under xbox-linux xebian and I was able to write an ext2-fs on it.
I then attached it to my computer but the OSs still arent able to boot when it is attached, which is strange.
I mean, they just don't boot. :)
When trying to list the devices attached (I deattached the other hard drives before booting the knoppix live cd) using **fdisk -l** it says it isn't able to **open it**.
```
knoppix@ttyp0[knoppix]$ fdisk -l
Konnte /dev/hdb nicht öffnen
```

Don't wonder, it's german.

Any ideas how to carry on from now and get that fuc%!§"$ hd to work? :mrgreen:

---

### Post by El Cris on 2006-01-30
It couldn't be opened, because I was not root, but it's still not accessable.
When trying to access the hard drive using cfdisk, it tells something like (translated from german):
```
FATAL ERROR: Could not read from the hard drive
```

---

### Post by El Cris on 2006-01-30
Ok, I found [this here](http://www.xbox-scene.com/software/software.php?page=linux#newsitemEplkFAkkAyphdSfGCP) and try to "unlock" the harddrive first. :)

---

### Post by skwid on 2006-01-30
Yeah I forgot about that part.   Did you use a slayers disk or something for that xbox Hard Drive?

---

