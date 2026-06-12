---
title: "can't access micro SD card - Permission denied"
date: 2008-12-02
forum: Hardware
---

### Post by Grumpyland on 2008-12-02
I have a 2gb micro SD card which is connected to my PC thru an adapter (to full size SD card) which is then connected via card reader. But when I plug it in, it does detect it and asks me what to do - to which I say open. Then it says permission denied and won't do anything with it. 

the file system is recognized as vfat

I tried googling, but without much avail, help appreciated.

---

### Post by jbrown96 on 2008-12-02
Try the following in a terminal:
1) ```
mkdir sd
```
2) (with the card plugged in) ```
sudo fdisk -l
```
Find the SD card. You will probably be able to tell by the size it reports. Remember the device name; it will be something like /dev/sdb1, /dev/sdc1, etc.
3) ```
sudo mount -t auto /dev/sdXX ./sd
``` change the /dev/sdXX to what you found in the last step
3) ```
sudo chown -R USERNAME:USERNAME ./sd
``` obviously chang USERNAME. Make sure you put it twice, separated by a colon.
4) ```
sudo umount ./sd
```
5) try removing it a plugging it back it. If everything works then delete the folder we made ```
rm -rf ./sd
```. If it doesn't, repeat steps 2 & 3. Then post the output of ```
ls -l ./sd
```

---

### Post by Grumpyland on 2008-12-04
Apparently, after couple reboots, it's working now. Kind of an inconsistent error there. I'll be sure to try it when it fails again. Thanks.

---

