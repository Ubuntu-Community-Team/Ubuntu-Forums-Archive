---
title: "mp3 Player won't mount - wtf???"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by seismicmike on 2007-08-07
My mp3 player won't mount.... seriously... It was working fine and then today I plug it in and it says "Invalid mount option when attempting to mount the volume". wtf??????????????????

Before I did this it was doing this thing where if I tried to add songs to it (first off I can't get Amarok working at all) it would start transfering and bring up a progress bar, but not do anything - NOTHING... The bar never moves.

But that doesn't even matter b/c now I can't even get it to mount!

WTF?????????????????????????????????/

---

### Post by eggdeng on 2007-08-07
Plug the device in and post the output of ```
dmesg | tail
```

---

### Post by seismicmike on 2007-08-07
```
[74707.356000] sdb: Write Protect is off
[74707.356000] sdb: Mode Sense: 00 26 00 00
[74707.356000] sdb: assuming drive cache: write through
[74707.356000] SCSI device sdb: 3881984 512-byte hdwr sectors (1988 MB)
[74707.356000] sdb: Write Protect is off
[74707.356000] sdb: Mode Sense: 00 26 00 00
[74707.356000] sdb: assuming drive cache: write through
[74707.356000]  sdb:
[74707.360000] sd 8:0:0:0: Attached scsi removable disk sdb
[74707.360000] sd 8:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by eggdeng on 2007-08-08
Looks OK to me. Create a folder to mount the device to, for example
```
sudo mkdir /media/mp3device
```
Then
```
sudo mount /dev/sdb1 /media/mp3device
```and
```
ls /media/mp3
``` to see if it has mounted.
Apologies for the redundancy if you have tried this already.

---

### Post by zero244 on 2007-10-03
Try this
[http://ubuntuforums.org/showthread.php?t=564001&highlight=Mp3+player+mount](http://ubuntuforums.org/showthread.php?t=564001&highlight=Mp3+player+mount)

---

