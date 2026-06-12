---
title: "Flash drive not in disk -l"
date: 2016-01-17
forum: Hardware
---

### Post by gabriel65 on 2016-01-17
]I have a weird problem with my USB drive. It is recognize in the  ubuntu Disk utility as been a No Media drive and it name is SMI USB  MEMORY BAR (1000) but I cannot see it in 
```
 sudo disk -l
``` 
The stick seem to had a problem while using Rufus under Win10. When  Rufus ask me to format the disk I press cancel because it was the wrong  stick. Since then I successfully use it twice for transferring and  deleting data so I know that my USB is not formated and pretty full of  files actually 56g of 64g. I have try it on a WinXP, Win10 and Ubuntu  and it did get recognize twice in Win10 but I haven't get any luck after  that. Gparted don't see it too. So here the thing, the disk is full of stuff but somehow I cannot  acces it. Is there a way I can do that? It a month old Lexar 64g USB  drive. Thanks!

---

### Post by blueridgedog on 2016-01-17
Some more information would be useful.  Can you post the output of:

```
mount
sudo fdisk -lu
lsusb
```

---

### Post by gabriel65 on 2016-01-17
I still see nothing about this flash drive with these commands.

I know that this drive is full of data because It did work twice.

---

### Post by blueridgedog on 2016-01-17
The people on this forum won't be able to help without data that they can see and analyze.  If you post those, it is a good launching point to what to look at next.

---

### Post by gabriel65 on 2016-01-19
That what Chipgenius say about my USB!

> Description: [H:]USB Mass Storage Device(SMI USB MEMORY BAR)
Device Type:        Mass Storage Device


Protocal Version: USB 2.10 <- Hint: This device can run faster when plugged to a USB3.0 port
Current Speed: High Speed
Max Current: 500mA


USB Device ID: VID = 090C PID = 3267


Device Vendor: Silicon Motion,Inc.
Device Name: SM3267AB MEMORY BAR
Device Revision: 0100


Manufacturer: SMI
Product Model: USB MEMORY BAR
Product Revision: 1000


Controller Vendor: SMI
Controller Part-Number: SM3267AB - ISP NONE


---

