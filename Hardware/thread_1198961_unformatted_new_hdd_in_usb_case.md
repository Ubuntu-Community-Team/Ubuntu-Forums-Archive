---
title: "unformatted new hdd in usb case"
date: 2009-06-28
forum: Hardware
---

### Post by yzx on 2009-06-28
hi folks. i have an usb hdd case that obiviously work in linux-with old 80 gb pata hdd which has already formatted when i first plugged it in. system saw and ran both ext3 and ntfs partitions. 

i bought new 320gb hdd and tried to format it with linux-but system not see my new hdd-no partitions shown as plugged(i guess its unformatted). then i open gparted- it doesn't see anything either,even not recognized that new  disk(just sees laptop hdd). 
 
how can i manage it to see unformatted hdd and format it(create partition)?

---

### Post by Dysport on 2009-06-28
Does your system see se hdd? Type *lsusb* in a terminal to see whether your HDD is listed. If you see something familiar there, try typing *sudo fdisk -l* to see whether it's correctly identified as a harddisk.

You could use qtparted, maybe you see the device with that program. Or you could try using the *fdisk* command in the terminal, that has to work if your computer "sees" the harddrive. For more information type *man fdisk* or search the forums for fdisk, you should find plenty of information.

---

