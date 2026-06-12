---
title: "[SOLVED] Corrupt sd card"
date: 2008-10-10
forum: Hardware
---

### Post by IanB2 on 2008-10-10
I hope you can help.

I appear to have a corrupt 4GB sd card that will only auto mount as read only (some of the file names are very strange and the physical lock on the card is in the off position).

Even using sudo, I'm unable to change any of the file attributes on the card. In the past I've just reformatted the card using gparted but even this has failed (error messages but I don't know where gparted logs these).

How do I recover the card? Is there a way of forcing the card to mount so I can reformat it?

---

### Post by sh_son on 2008-10-10
Which file system do you use for your SD card?
I always use FAT/FAT32 for my 2Gb SD card which has been sitting in the SD-Card slot in my laptop for last 1.5 years.

Again, try format the SD card to FAT/FAT32 file system try if it helps.

[Edit]
1. in terminal type **'gksudo nautilus' **- then browse /media/ folder to see if it loads
2. trying format to FAT/FAT32
3. use force option (-o force) to mount command

---

### Post by IanB2 on 2008-10-10
> **sh_son said:**
> Which file system do you use for your SD card?
I always use FAT/FAT32 for my 2Gb SD card which has been sitting in the SD-Card slot in my laptop for last 1.5 years.

Again, try format the SD card to FAT/FAT32 file system try if it helps.

[Edit]
1. in terminal type **'gksudo nautilus' **- then browse /media/ folder to see if it loads
2. trying format to FAT/FAT32
3. use force option (-o force) to mount command

Thanks for your help.
1. the card now is not recognised by my system and the card is not mounting in the media folder
2. how do I reformat the card to fat 32 (as it was origninally?)
3. how do you force the card to mount - unsure of what to type in the terminal

I hope you can help me further

---

### Post by IanB2 on 2008-10-10
A GENIUS in another forum suggesting reformatting the sd card in a digital camera and it worked!!

---

