---
title: "Format a SD card"
date: 2010-11-15
forum: Hardware
---

### Post by André Ferreira on 2010-11-15
Hello every one

I'm new and i don't know if this is a better place to put my question. If doesn't please informs me.

I have a SD card used in BOSH to program the GPS used in the radio. But this card is protected to write. I already checked the switch and don't work.

the type of the card is a msdos.

i used the follows commands to try solve the problem:

sudo umount /media/(name of the card)

sudo mkfs.msdos /dev/mmcblk0p1

and when i finish this commands i mount again the card and the documents still there, don't erase the card.

sorry for my english and thanks for yours concern.

---

### Post by ajgreeny on 2010-11-15
Try using gparted either from the ubuntu live CD, or install it to your desktop system and use it from there.  Make sure the partition(s) on the card are unmounted, and then try deleting them and making a new partition formatted as fat32.

---

### Post by cchhrriiss121212 on 2010-11-15
Try using either disk utility or gparted from the system menu.

---

### Post by André Ferreira on 2010-11-15
I install the gparted but i don't solve my problem, because occurred an error when the gparted try to create a empty partition... 

anyway thanks for your help...

---

