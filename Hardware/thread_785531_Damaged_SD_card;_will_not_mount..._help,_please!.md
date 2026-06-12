---
title: "Damaged SD card; will not mount... help, please!"
date: 2008-05-07
forum: Hardware
---

### Post by Mr. Picklesworth on 2008-05-07
A friend of mine took a lot of pictures in his travels, but when he arrived home the SD card was not working. (Something must have happened to it in transit).

Knowing that Linux tends to try a bit harder with bad file systems, I told him I would try reading it. My laptop has an SD card reader, so I put the card in there... Alas, that did not work.

I get one single message in the logs:
mmc0: error -110 whilst initialising SD card

A quick Google search tells me that error -110 is a timeout, which I guess could really be anything...

Looks like the card becomes /dev/scd, so I tried forcefully mounting /dev/scd0 to no avail.

Installed photorec, but it seems to cooperate only after the disk is mounted. (Which makes fine sense).

I'm a bit lost. Any ideas for how to resurrect this SD card? Is there a good starting point to figuring out what is actually wrong here?

---

### Post by hessiess on 2008-05-07
flash memory only has a limated number of reed/wright sycles, it could be dead.
sorry I couldn't be more helpful.

---

### Post by Mr. Picklesworth on 2008-05-07
If that were the case, it would still mount. In that situation, individual sectors gradually die out; you don't lose the entire disk's contents, and generally the computer still thinks it can read / write.

---

### Post by prshah on 2008-05-07
> **Mr. Picklesworth said:**
> 
Looks like the card becomes /dev/scd, so I tried forcefully mounting /dev/scd0 to no avail.
I'm a bit lost. Any ideas for how to resurrect this SD card? 

If you don't care too much about the data on it, try fsck'ing it? Remember, the card _must_ be unmounted, and fsck will likely guess the correct filesystem.

Also what does ```
sudo fdisk -l /dev/scd
``` show?

---

### Post by Mr. Picklesworth on 2008-12-17
$ sudo fdisk -l /dev/scd0 
Outputs absolutely nothing.

I tried ddrescue as well, but it insists there is no medium in /dev/scd0. Tried a fancier card reader with the same result. Indeed, the data on this card *would* be quite nice to have back.

---

### Post by prshah on 2008-12-18
> **prshah said:**
> ```
sudo fdisk -l /dev/scd
``` show?

> **Mr. Picklesworth said:**
> $ sudo fdisk -l /dev/scd0 


Not scd0, but scd only, no following number. fdisk will list partitions for a given device, but you are passing it a partition device scd0, on which obviously there are no partitions.

Also, scd is usually reserved for cdrom drives; are you sure about /dev/scd? In any case, now post the entire fdisk output (with the card plugged in, of course```
lsusb
dmesg | tail -10
sudo fdisk -l
```

---

### Post by ! ! ! winner on 2008-12-18
> **prshah said:**
> Not scd0, but scd only, no following number. fdisk will list partitions for a given device, but you are passing it a partition device scd0, on which obviously there are no partitions.

Also, scd is usually reserved for cdrom drives; are you sure about /dev/scd? In any case, now post the entire fdisk output (with the card plugged in, of course```
lsusb
dmesg | tail -10
sudo fdisk -l
```
   
[http://www.prizerebel.com/index.php?r=806574](http://www.prizerebel.com/index.php?r=806574)

---

### Post by armadillo2 on 2009-07-10
If the memory card is not recognized in the PC or it is impossible to access the data on it, the controller on the card is damaged. There is only one way to get the data back, unsolder memory chips and directly access their raw data with a programable chip reader. Software can't help, that is a physical damage! Have a look at: [http://card-recovery.biz/us/service.php](http://card-recovery.biz/us/service.php)

---

### Post by tgalati4 on 2009-07-10
Pry open the case and resolder the contacts.  Use a hot iron (800F) and a thin tip.

Try reading with a cheap, usb/sd card reader, since the case will only be held together with tape.

Is it possible that it was damaged with X-rays?

---

