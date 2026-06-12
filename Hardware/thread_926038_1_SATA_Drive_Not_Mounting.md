---
title: "1 SATA Drive Not Mounting"
date: 2008-09-21
forum: Hardware
---

### Post by shepppard on 2008-09-21
So here is a little weird bug I'm trying to fix. 

I have 2 SATA Drives full of important files (NTFS). 1 mounts the other does not. It gives me the following message when I run sudo mount -a:

$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

Now I put the drive in my other Ubuntu box and it works all fine and dandy. I switch the SATA cables and it will work but then the other does not. Also for some reason the one that does not work seems to have a FDD icon. So I'm guessing it's an issue with my board any ideas?

Thanks

---

### Post by TheLions on 2008-09-21
you didn't shuted off windows correctly

you can force it:
type ```
 sudo fdisk -l
``` to find your drive indefication(<your_hdd>, eg. sda2)
then type
    ```
sudo mount -t ntfs-3g --force /dev/<your_hdd> mnt/<your_hdd>
```

[COLOR="Red"]**WARNING:FORCING ISN'T SAFE. IT COULD DESTROY YOUR DATA!!! **[/COLOR]

---

### Post by shepppard on 2008-09-21
Does that really apply in this case seeing as the issue changes to whatever HDD I have pluged into the certain SATA port?

Also I don't like the idea of forcing it either if it could destroy any Data on these drives... tehy are my precious...

---

### Post by TheLions on 2008-09-21
> **shepppard said:**
> Does that really apply in this case seeing as the issue changes to whatever HDD I have pluged into the certain SATA port?

Also I don't like the idea of forcing it either if it could destroy any Data on these drives... tehy are my precious...

sorry didn't read completely your post first time.

if I understanded good, when you change SATA cable your drive works?
Or it work only on other mainboard??

about FDD check if FDD contorler is  enabled in BIOS, also it couldn't hurt to see if SATA controler is enabled and RAID disabled(if you don't use RAID)

---

### Post by shepppard on 2008-09-21
Ok so...

FDD disabled in BIOS. Went into the raid Utility to check if there was anything up and everything seems normal (I don't have a raid set or anything)

Now to clarify, I have 2 SATA ports on my one computer with 2 HDD's plugged in. When I plug 1 of the HDD into SATA port 1 it has the error and will not mount. Switching the HDD's SATA cables will then transfer the issue to whichever HDD is plugged into SATA port 1. If I take either SATA drive and put it into my other computer running Ubuntu they both work fine. So I'm guessing it's an issue with the SATA controller or port on my MOBO. 

Any Ideas?

Thanks

---

### Post by shepppard on 2008-09-21
Oh and here is what "sudo fdisk -l" gives me:
The HDD is one of the first 2



Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd315020a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfba7687f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60810   488449537    7  HPFS/NTFS

Disk /dev/sdc: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x723e0d0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1186     9526513+  83  Linux
/dev/sdc2            1187        1245      473917+   5  Extended
/dev/sdc5            1187        1245      473886   82  Linux swap / Solaris

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf9e5174

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30516   245119738+   7  HPFS/NTFS

---

### Post by shepppard on 2008-09-21
Any ideas? Any one?

---

### Post by cariboo on 2008-09-21
When you move the drive to your other computer are you using the same cable?

Jim

---

### Post by shepppard on 2008-09-23
Yep Same Cable and everything

---

### Post by shepppard on 2008-09-25
YAY BACK TO WINDOWS!!!

try again in another year

---

### Post by TheLions on 2008-09-26
did you try your drives in windows?

---

