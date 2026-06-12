---
title: "Fstab &amp; sudo fdisk -l being *really* wierd"
date: 2008-06-25
forum: Hardware
---

### Post by tannedin on 2008-06-25
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9968548d-bc6b-4005-b250-178c3de3d8c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=98c6c7fb-1170-41ad-9442-6487376a05f2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

sudo fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2034

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1c06006

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b9e8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   83  Linux
```

sudo blkid
```

/dev/sda1: UUID="edc439ea-d8fd-48e6-999c-32b71cc441a5" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="9968548d-bc6b-4005-b250-178c3de3d8c4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="8272b77a-a928-412d-87e8-00989a793f47" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="98c6c7fb-1170-41ad-9442-6487376a05f2" 
```

so, heres the rub... the server boots normally and recognizes the 500GB and the 80GB however does not automount them at boot.

fstab has sda as the boot drive, however everything else is pointing to sdb being the boot-flagged device... Mostly curious if anyone else has seen this and what to do about it...

my ending point is WTF

---

### Post by Odrodzona-Sarmacja on 2008-06-26
Xubuntu 8.04 doesn't automount hard drives on its own any more. You need to add lines for automounting them in fstab yourself.

---

### Post by tannedin on 2008-06-26
thats what my plan was.  However, the post was directed at the devices.  If you read the fstab vs the fdisk -l: 
(fstab) sda1 is the only mounting drive with sda5 as swap space
(fdisk) sdb1 has the boot flag and sdb5 as the swap space.
(blkid) sdb has the swap space, so it seems to "agree" with fdisk

So in the end, what am I mounting at boot and what would I add to fdisk, sdb or sda devices?

---

### Post by ukripper on 2008-06-26
First you need to add you drives to your fstab especially if it is USB drive

when booting sometimes your harddrives takes time to initialise and by then init has finsihed mounting your drives through fstab therfore, fails to mount.

you need to do this;
open rc.local using:
```
vim /etc/rc.local
```

and add > **mount -a **
before exit 0

save and exit.

and reboot. this time it will mount for you automatically using fstab

Make sure first you have added your drives to fstab otherwise it won't mount

---

### Post by tannedin on 2008-06-26
still doesn't explain why fstab and fdisk are showing two different devices for the boot device, which would lead to where I put the mountpoints.

---

### Post by ukripper on 2008-06-26
> **tannedin said:**
> still doesn't explain why fstab and fdisk are showing two different devices for the boot device, which would lead to where I put the mountpoints.

can you do this in terminal and post output here:
```
df -h /boot
```

---

### Post by tannedin on 2008-06-26
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              36G  3.8G   30G  12% /

```

---

### Post by Odrodzona-Sarmacja on 2008-06-26
> **tannedin said:**
> ```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              36G  3.8G   30G  12% /

```

It seems grub is booting from the other hd... from sdb1.
If you want it to boot from sda1, where your root partition is, then do so:
"sudo grub"
"root (hd0,0)"
"setup (hd0)"

---

### Post by ukripper on 2008-06-26
> **tannedin said:**
> ```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              36G  3.8G   30G  12% /

```


fstab has correctly mounted the boot partition. Check UUID in fstab and see the blkid UUID=9968548d-bc6b-4005-b250-178c3de3d8c4 is sdb1 which is correct. 

your boot partition is on sdb1 not on sda1

nothing unusual or weird about it i think you got confused by comments in fstab pointing to # /dev/sda1

---

### Post by Odrodzona-Sarmacja on 2008-06-26
> **ukripper said:**
> 
nothing unusual or weird about it i think you got confused by comments in fstab pointing to # /dev/sda1

Yea must be so. An updated fstab would be nice to see though.

---

### Post by ukripper on 2008-06-26
> **Odrodzona-Sarmacja said:**
> Yea must be so. An updated fstab would be nice to see though.

looks like fstab had already been manually amended and forgot to change commnets. fstab don't update comments it is user's job to do that.

---

### Post by tannedin on 2008-06-26
> **ukripper said:**
> looks like fstab had already been manually amended and forgot to change commnets. fstab don't update comments it is user's job to do that.

so the fact that fstab is stating sda, and everything else is stating sdb is fine? seems, odd to me, since I would think the only boot device would be sda...

anyway to change it?
example: /dev/sda is the boot devices (30g if your backreading), /dev/sdb for the 80g, and sdc for the 500g?

PS/Edit: This is also a fresh 8.04 install fstab, unedited by the user

---

### Post by Ng Oon-Ee on 2008-06-26
The # in the fstab indicate those lines are comments, the real info is in the UUIDs.

What probably happened here is that on installation your 500GB hard disk (currently showing as /dev/sda, with only one partition called /dev/sda1) wasn't connected/detected by the system (I'd lean towards the former, hard disk detection isn't a big deal, depends on the BIOS.

So on installation, the boot drive WAS /dev/sda1 (what is currently shown as /dev/sdb1 in your fdisk). However, when you inserted/plugged in/turned on your 500GB hard disk, it is detected first by the BIOS (that's how sda/sdb/sdc gets assigned, in order of detection), so it is assigned /dev/sda, and your 40 GB hard disk which was previously /dev/sda is now pushed to /dev/sdb.

Ordinarily this could cause you problems with booting, fortunately even when the udev assignments are messed up, UUIDs of the individual partitions do not change, so Ubuntu defaults to assigning your fstab using the UUIDs (Universal Unique IDentifier) instead of /dev/sda1.

In summary, this should not cause a problem, and is actually perfectly normal behaviour (on my system, with a 250GB internal hard disk and a 640GB external, the 640GB is assigned /dev/sda if it is powered on on bootup while the 250GB gets /dev/sda if the external is not powered on on bootup). You'll need to take note of this only if you automount hard disks using the udev assignments (I'd recommend using UUIDs all the time).

Read my post in [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=836542") for a more detailed explanation.

---

### Post by tannedin on 2008-06-26
> **Ng Oon-Ee said:**
> The # in the fstab indicate those lines are comments, the real info is in the UUIDs.

What probably happened here is that on installation your 500GB hard disk (currently showing as /dev/sda, with only one partition called /dev/sda1) wasn't connected/detected by the system (I'd lean towards the former, hard disk detection isn't a big deal, depends on the BIOS.

So on installation, the boot drive WAS /dev/sda1 (what is currently shown as /dev/sdb1 in your fdisk). However, when you inserted/plugged in/turned on your 500GB hard disk, it is detected first by the BIOS (that's how sda/sdb/sdc gets assigned, in order of detection), so it is assigned /dev/sda, and your 40 GB hard disk which was previously /dev/sda is now pushed to /dev/sdb.

Ordinarily this could cause you problems with booting, fortunately even when the udev assignments are messed up, UUIDs of the individual partitions do not change, so Ubuntu defaults to assigning your fstab using the UUIDs (Universal Unique IDentifier) instead of /dev/sda1.

In summary, this should not cause a problem, and is actually perfectly normal behaviour (on my system, with a 250GB internal hard disk and a 640GB external, the 640GB is assigned /dev/sda if it is powered on on bootup while the 250GB gets /dev/sda if the external is not powered on on bootup). You'll need to take note of this only if you automount hard disks using the udev assignments (I'd recommend using UUIDs all the time).

Read my post in [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=836542") for a more detailed explanation.

totally awesome, the UUID configuration currently has everything 95% to perfect... my only complaint is that in gnome i have the icons for the devices now, however I can't change their name
Example: current setting "80.0 GB Media" vs "Music" (mount point is /media/music)

---

### Post by Ng Oon-Ee on 2008-06-27
> **tannedin said:**
> totally awesome, the UUID configuration currently has everything 95% to perfect... my only complaint is that in gnome i have the icons for the devices now, however I can't change their name
Example: current setting "80.0 GB Media" vs "Music" (mount point is /media/music)

Renaming your partitions on Linux is not as simple as in Windows, AFAIK. I was searching for information on it a week ago, seems there's different renaming programs for each file-system. If your external is either FAT or NTFS (as it probably is, since the whole world uses Windows), the easiest solution would probably be to rename the drive on a friend's Windows machine.

Ah, a quick search turned this up, try it out:-

[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

