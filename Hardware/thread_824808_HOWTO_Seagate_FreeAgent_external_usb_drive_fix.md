---
title: "HOWTO: Seagate FreeAgent external usb drive fix"
date: 2008-06-10
forum: Hardware
---

### Post by troupa on 2008-06-10
For anyone who has a Free Agent or Free Agent Pro external usb hard drive and has problems with it losing write permission:  this is caused by the drive going into standby and then registering errors which eventually ends up in the drive being mounted read-only.  

To fix:  
```
sudo apt-get install sdparm
sudo sdparm --clear STANDBY -6 /dev/sdX
```

where sdX is the /dev entry of your drive

---

### Post by sande87 on 2008-06-14
iv had some similar problems with a Western Digital 500gb disk. The disk works fine for while, but when it goes into standby it gets "angry" and says "Read only filesystem" when I try to delete something or write to it.

I didnt get the solution above to work, but remounting the disk worked.

I used: "sudo mount -t $FILESYSTEM /dev/$DEVICE $MOUNTPOINT -o
         $USER,remount"

example: "sudo mount -t vfat /dev/sdb1 /media/SANDE-o sande,
         remount"

$FILESYSTEM is the filesystem the parition uses
$DEVICE is the device or partition you want to remount
$MOUNTPOINT is where you want your disk remounted
$USER is your username

PS! im fairly new to linux, so there might be some better way to do this, but this solution worked for me, so feel free to mail me for corrections and/or questions

---

