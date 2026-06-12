---
title: "using an electro harmonix 2880 with ubuntu"
date: 2017-05-12
forum: Hardware
---

### Post by didpoutrator on 2017-05-12
Hello to all
I am using linux for a long time now to play and record music. I have a piece of music hardware that records raw wav file onto a compactflash card. It's an electro harmonix 2880. I am able to see the 2880 as an external drive BUT it's impossible to mount it. On OSX or Windows it doesn't require any kind of third party software or driver but with linux it seem to be impossible to achieve. I can see the sevice as /dev/sdb but it says that there is no recognised filesystem. I have tried to format it to any kind of file format but it stops and unplug the device before the end and outputs an error message. 
Can anyone help me too find the right direction to take? 
I can provide the schematics and any log you ask me to provide if necessary.
thanks, any help is appreciated.

---

### Post by ajgreeny on 2017-05-12
What filesystem is on the compactflash card?

The terminal command ```
sudo parted -l
``` will show us what it is.

If larger than 32GB it is probably exFAT and you will need to install exfat-utils and exfat-fuse to your Ubuntu installation.

---

### Post by didpoutrator on 2017-05-12
thanks,
I have already tried fdisk, cfdisk, sfdisk, gparted, parted and testdisk. none of them can define what type of filesystem it is. The card is 1Gb only. Apprently there is no mbr but when I try to create one it doesn't work and if I try to format the card it fails. I will post the different logs later (i am not home)
to be continued

---

### Post by ajgreeny on 2017-05-12
It is possible the card has been formatted without first creating a partition, so try gparted again but this time choose to "Create partition table", use the default msdos partition table, then create a new partition of the whole and now unallocated space, and that may be all that is necessary for you to be able to use the card.

---

