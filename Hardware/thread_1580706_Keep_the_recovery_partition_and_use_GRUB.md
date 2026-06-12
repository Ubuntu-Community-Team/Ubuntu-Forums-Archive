---
title: "Keep the recovery partition and use GRUB?"
date: 2010-09-23
forum: Hardware
---

### Post by Immolatus on 2010-09-23
Just got a thinkpad t410 and i need to dual boot win 7 and ubuntu.
Problem is I think the recovery system will give me a problem with grub. I made the factory recovery DVD's from within windows, but what i really want is to be rid of the recovery (as I have recovery on disk). Here's the rub recovery disk gives no partitioning options and reinstalls the stupid waste of space recovery partition.
any thoughts??
:confused:

---

### Post by eotakos on 2010-09-23
I kept mine. I dual boot with windows, because windows is my gaming platform. Also, I'm not always at home, so when I need my recovery (and as we know windows are not that reliable), I may not have access to my dvds.

I don't know... it also depends on what percentage of your total disk capacity the recovery partition occupies. To be franc though, triple booting to ubuntu, windows, recovery wasn't that easy in the beginning because i had issues with the partition table. Windows didn't like it the way gparted formed it, and vice versa, in the end I used a little of testdisk and now it works without problems.

---

### Post by Immolatus on 2010-09-23
well, I used gparted to resize and remove the recovery partition. I'm going to leave SYSTEM_DRV alone and try installing ubuntu on the space I made. I've read around that GRUB will install to the right place and that was my main worry. I'll post back and let you know if it pukes on me or not.:popcorn:

---

### Post by garvinrick4 on 2010-09-24
If you  have 3 primarys used for Window 7 make one large Extended and make all linux
in logicals. Do your partitioning ( I use gparted) before any installs and use the partitions you have made in gparted sda5, sda6, sda7 and so using manual install during installation
procedure.

---

### Post by Immolatus on 2010-09-25
Well, it worked. (by the way, holy partitions batman!!(see thumbnail above post)). 

Also regarding the "Thinkpad wireless" that comes with a lot of T series, I tried out Kubuntu 10.04 on this machine. Ubuntu was having a problem with the IntelHD integrated graphics. It worked out great and for some reason the thinkpad bgn wifi worked out of the box wich suprised the heck out of me.
Apparently  SYSTEM_DRV is where the boot loader goes on this machine, not the MBR? either way it worked.

Thanks for the suggestions.:guitar:

---

### Post by garvinrick4 on 2010-09-25
> **Immolatus said:**
> Well, it worked. (by the way, holy partitions batman!!(see thumbnail above post)). 

Also regarding the "Thinkpad wireless" that comes with a lot of T series, I tried out Kubuntu 10.04 on this machine. Ubuntu was having a problem with the IntelHD integrated graphics. It worked out great and for some reason the thinkpad bgn wifi worked out of the box wich suprised the heck out of me.
Apparently  SYSTEM_DRV is where the boot loader goes on this machine, not the MBR? either way it worked.

Thanks for the suggestions.:guitar: That would be a boot partition, I have one also. Grub still go's into sda. You can have or you can choose not to have a /boot partition. Still will be in mbr.
Confusing sometimes but is worth reading about in spare time. I believe when someone chooses side by side with Ubuntu and system 7 for install it uses a /boot partition by default.

---

### Post by irw on 2012-04-05
The first thing I did when I got a new laptop was to use gparted from a live cd to shrink the windows system partition to the size I wanted.
after a reboot into windows to check it was still working, I restarted with the live cd and installed Ubuntu.

I then created a dd image of the partition table, MBR and Windows partitions on an external hard disk.
This enables me to do a "factory restore" of Windows without killing Ubuntu, and is much faster than the normal windows restore and Ubuntu reinstall.

Backup the Partition Layout:
```
sfdisk -d /dev/sdX > /[LOCATION]/backup-sdX.sf
```

Backup the Master Boot Record (MBR):
```
dd if=/dev/sdX of=/[LOCATION]/backup-sdX.mbr count=1 bs=512
```

Backup Windows Partitions:
```
dd if=/dev/sdX bs=1024 conv=noerror,sync | pv | 7za a -mx9 /[LOCATION]/backup-sdX.7z -si
```
I use 7zip to compress the image and pv to watch progress (sudo apt-get install p7zip-full pv)

If you just want the image uncompressed:
```
dd if=/dev/sdX of=/[LOCATION]/backup-sdX.img bs=1024 conv=noerror,sync
```

Another option is to save the backup images on a partition on the hard disk, then you can restore them from the working ubuntu system or a live cd, not the external drive as well.

---

