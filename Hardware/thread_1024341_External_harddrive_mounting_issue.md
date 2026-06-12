---
title: "External harddrive mounting issue"
date: 2008-12-28
forum: Hardware
---

### Post by javaMonkeyMaster on 2008-12-28
I am a very new user to ubuntu 8.04lts  with very limited terminal understanding and use.  (Note: if my message is in the wrong spot please move it)

I just got a Verbatim 320gb external harddrive to hold my files on.  I plugged it into my computer and it mounted and a made a new folder on the drive, but before i could do anything else, the drive unmounted and would not remount.  I read some other forums and some terminal commands i tried were:

 sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force

i got the message:

ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

another command i tried was:

lsusb

and i got the message:
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I think this means that the computer is not detecting the drive, but it opened it let me browse some files and make a new folder so i am confused

---

### Post by taurus on 2008-12-28
Is it a brand new drive that has not been used before, creating a partition and formatting it?  

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by javaMonkeyMaster on 2008-12-28
it is brand new i have no idea what you mean by partitioning it though um the reply to the command was

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9327    74919096   83  Linux
/dev/hda2            9328        9729     3229065    5  Extended
/dev/hda5            9328        9729     3229033+  82  Linux swap / Solaris

however that is not right i believe that is my harddrive the 80gb is my harddrive not the external one though

---

### Post by Rohan Kapoor on 2008-12-29
> **javaMonkeyMaster said:**
> it is brand new i have no idea what you mean by partitioning it though um the reply to the command was

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9327    74919096   83  Linux
/dev/hda2            9328        9729     3229065    5  Extended
/dev/hda5            9328        9729     3229033+  82  Linux swap / Solaris

however that is not right i believe that is my harddrive the 80gb is my harddrive not the external one though

It sounds to me as if your external drive just died. Do you have another PC/MAC/LINUX box to test it on. If you just got the drive though and it has gon bad, you could return it and get a new one or request for warranty coverage, exchange, whatever. This doesn't sound like an Ubuntu problem.

---

### Post by javaMonkeyMaster on 2008-12-29
Thank you, you are right i tried it in another computer and it did not work it kind of stinks it was brand new.

---

### Post by Rohan Kapoor on 2008-12-29
Being brand new you should be able to contact the manufacturer (verbatim) and have them repair or replace it for free throught warranty.

---

