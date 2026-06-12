---
title: "[SOLVED] Some Hard Drives Not Mounting in 7.10"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by xcusmwah on 2008-02-24
I have a few hard drives that are not able to mount.  I'm new to Ubuntu, can someone advise how to help fix this?  Thank you!

---

### Post by deepclutch on 2008-02-24
from ur screenshot,it is seen that Ubuntu finds harddisks and tried to mount,but those ntfs partitions cannot be mounted due to errors in file system.you have to boot to windows xp or > and select the ntfs partitions /dev/sdf1 and those partitions which shows the same error.and select for chkdsk in windows(donno much).though u can forcibly mount those partitions,which *may* corrupt those ntfs partitions,for that reason,I am not mentioning the method ;) .you run **chkdsk** ASAP in windows.go to My Computer >disks with ntfs>right click properties>select error checking-that s all! :cool:

---

### Post by xcusmwah on 2008-02-24
Thanks, when I boot into the 7.04 live cd the drives that I have problems with work just fine.  I am using the 7.04 live cd because I upgraded to 7.10 via the package manager.  Does that help?

---

### Post by deepclutch on 2008-02-24
well,I dont use windows any more.still,I guess ubuntu gutsy by default uses ntfs-3g which is read-write enabled.while feisty uses kernel- supported ntfs readonly driver.that may be the change.

may be,if u really want,(dont get on me for non-bootable ntfs-drives and windows etc etc),I can show u how to mount:
select the partition u want to mount,let it be /dev/sdf1 :
then,
run below command:
```
mount -t ntfs-3g /dev/sdf1 /mnt -o force
```

**BE WARNED THAT,ABOVE COMMAND WILL MAKE UR WINDOW$ NOT BOOTABLE,IF U TRIED ON A WINDOW$ INSTALLED PARTITION!**

---

### Post by xcusmwah on 2008-02-24
OK I tried that and the mount disappeared entirely.  I am now booted via the live cd and all of the drives are visible and I am able to view them (as read only of course) just fine.  One interesting thing I am seeing is there are .mbr files (see below), not sure if those matter, I know the thumbs.db is for Windows but not sure what the .mbr files are.  Any how I am going to book back into Ubuntu without the live cd and see what happens with your suggestion again.

file:///media/Videos%202/Thumbs.db
file:///media/Videos%202/wubildr
file:///media/Videos%202/wubildr.mbr
file:///media/Videos%202/Thumbs.db
file:///media/Videos%202/wubildr
file:///media/Videos%202/wubildr.mbr

---

### Post by xcusmwah on 2008-02-24
I booted back to Ubuntu normally and the mount is not showing for me.  FYI, let me know if I can try anything else.  Thank you

---

### Post by polmir on 2008-02-24
type in terminal
```
sudo fdisk -l
```
```
gedit /etc/fstab
```
and post output of it

---

### Post by xcusmwah on 2008-02-24
[code]jeremy@jeremy-desktop:~$ sudo fdisk -l
[sudo] password for jeremy:

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x192f6844

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ce3c4b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05c18ccf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18513   148705641    7  HPFS/NTFS
/dev/sdc2           18514       48641   242003160    f  W95 Ext'd (LBA)
/dev/sdc5           18514       48641   242003128+   7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0d4cc13a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1     1938021   976762552+   7  HPFS/NTFS

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0eca03ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sde2   *           2       48641   390700800    f  W95 Ext'd (LBA)
/dev/sde5               2        7792    62581176    7  HPFS/NTFS
/dev/sde6            7793       13288    44146588+   7  HPFS/NTFS
/dev/sde7           13289       48641   283972941    7  HPFS/NTFS

Disk /dev/sdf: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35da35da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60800   488375968+   c  W95 FAT32 (LBA)

Disk /dev/sdh: 120.0 GB, 120034123776 bytes
255 heads, 19 sectors/track, 48388 cylinders
Units = cylinders of 4845 * 512 = 2480640 bytes
Disk identifier: 0x0a800a7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       48384   117210208+   7  HPFS/NTFS

Disk /dev/sdi: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1       91201   732572001    7  HPFS/NTFS
jeremy@jeremy-desktop:~$ gedit /etc/fstab



# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=4404e6b4-3e11-4ce5-bcf0-1937e9f50e8b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=5a62bdc4-0280-4992-9d3c-96d64fd3b082 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdh5 /media/Movies\0402 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdh1 /media/Home\040Videos ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdd1 /media/MP3 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb1 /media/Vidcasts ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda7 /media/MMA,\040Wrestling,\040Boxing ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/Our\040Documents ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Pictures ntfs-3g defaults,locale=en_US.UTF-8 0 0
[code]

---

### Post by kevmitch on 2008-02-24
It looks like the /dev/sdf1 entry disappeared from your fstab. That's kind of weird. What exactly happened when you tried to force mount the partition? Do you still have the /dev/sdf1 device file present? 

ls -l /dev/sdf1

If the above command finds something, you might try adding it back into your /etc/fstab file with a line like
/dev/sdf1 /media/Videos2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

You can also revert to mounting it read only by replacing the above line with

/dev/sdf1 /media/Videos2 ntfs defaults,locale=en_US.UTF-8 0 0

note the change ntfs-3g->ntfs.

---

### Post by polmir on 2008-02-25
xcusmwah --- do you know what is tags? Your post is not illegible.
Wrap ```
 tags around selected text. 
[SIZE="3"]Before You post your text try it ---> **Preview post**[/SIZE]
----------------------
type in terminal 
[CODE]ls -l /media 
```
```
blkid  /dev/sda
```
```
blkid  /dev/sdb
```
```
blkid  /dev/sdc
```
```
blkid  /dev/sdd
```
```
blkid  /dev/sde
```
```
blkid  /dev/sdf
```
```
blkid  /dev/sdg
```
```
blkid  /dev/sdh
```
```
blkid  /dev/sdi
```
and post output it

---

### Post by xcusmwah on 2008-02-26
Hi everyone - thank you so much for all of your assistance.  I wanted to let you know that I have been able to resolve the problem.  Here is what I did to fix it...

- I burned boot and nuke to a CD and wiped my primary hard drive
- I installed Windows XP
- I then installed Ubuntu 7.04, formatted the drive with Ubuntu, upgraded to Ubuntu 7.10

For some reason when I did a fresh install of Ubuntu it seems to have fixed the issue on all drives which is great.  I can mount, read and write to them just fine. 

Many thanks to everyone again.  You are a big reason why Ubuntu and Linux are the future and why it is becoming so successful. I cannot thank you enough.

---

