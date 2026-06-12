---
title: "Partition mix up ..."
date: 2008-08-02
forum: General Help
---

### Post by Bucky Ball on 2008-08-02
Hi all. Not desperate but getting there ...

Had a 10GB partition and wanted to use that to share with Windoze, so deleted and created new logical drive, format FAT32.

Before it would let me delete, it asked me to umount any partitions with ids above sda7 (which was the id of the drive I was about to reformat. I have another 25GB partition which was labelled sda8, to right clicked on icon on desktop and unmounted that through the menu. Reformated my 10GB to FAT32 fine, and when I did, it changed the id of that drive to sda8 and the untouched 25GB drive is now sda7!

Thus, my fstab and mstab etc must be real confused and I can't access the 25GB drive at all - that is dire. Uni student, all my work (and life!) is on that drive and really need to get on with it asap.

I'm not a complete noob so have screwed around and researched this but for the moment, can find no solutions. I did back up everything to external drive before I started but there is, I am sure, an easy way to rearrange permissions and links and clean up my directories. Any offers gratefully accepted ... ;)

HP dv6000 series laptop, 64 bit, 2 GB RAM, Ubuntu Hardy 8.04 running Gnome (when this happened).

---

### Post by cdtech on 2008-08-02
First we need to see the:
```
sudo fdisk -l
```

And then the:
```
sudo gedit /etc/fstab
```

Thanks........

---

### Post by Bucky Ball on 2008-08-02
> skulker@HPLappy:/dev$ sudo fdisk -l
[sudo] password for skulker: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fa94dae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3814    30630880+   7  HPFS/NTFS
/dev/sda2            3815        9729    47512237+   5  Extended
/dev/sda5            9365        9729     2931862+  82  Linux swap / Solaris
/dev/sda6            3815        5029     9759424+  83  Linux
/dev/sda7            6246        9363    25045303+  83  Linux
/dev/sda8            5030        6245     9767488+   b  W95 FAT32

Partition table entries are not in disk order

I suppose the last line about partition tables not being in order is a clue! How to rearrange. Below is the result of 'sudo gedit /etc/fstab'

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=36bd7710-ca84-48c9-9011-e96d336ba192 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=653d41d1-f3d8-4e3c-8fdd-a298084b754c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda4
UUID=4317640b-79fe-4ee4-a761-84f84991256e /media/disk	  ext3    relatime,errors=remount-ro 0       1

And I reckon I somehow had the 25GB partition mounted as /dev/sda4 before the switch, even though gparted was telling me it was 8. Meant to post some of this info first up, cheers ...

Update: think I'm getting it. That sda4 really needs to be sda7 and I need to add sda8 to the /etc/fstab file, right? The sda4 maybe needs to be installed and I need to put correct details for the two 'new' partitions instead ...

---

### Post by cdtech on 2008-08-02
You just need to create an entry within your fstab file to include the partitions you want mounted at boot.

To get the correct block id use:
```
blkid
```
This will list all of the block id's for each partition. Replace the ones currently in your fstab list with the correct one's. 

This is how I have mine set up for instance.

```
proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=41d95d32-e6bf-418b-b3fe-278d0c7ba5e1 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=9ad5f7dd-63ac-46f2-8ddc-24ccafdcaa46 /boot ext3 defaults 0 1
# Entry for /dev/sda6 :
UUID=aed3efe3-53d1-4b88-9c36-c87678436f45 /home ext3 defaults 0 1
# Entry for /dev/sdb1 :
UUID=1D8FD5F25AC0301F /media/Vista ntfs defaults,umask=007,gid=46 0 0
# Entry for /dev/sdb2 :
UUID=2C88743C8874071C /media/HP-Recovery ntfs defaults,umask=007,gid=46 0 0
# Entry for /dev/sda3 :
UUID=C6AAD33AAAD325A9 /media/Storage ntfs defaults,umask=002,gid=46 0 2
# Entry for /dev/sda5 :
UUID=895c93de-63d5-468f-99b7-d0f70696928b none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

Hope this helps.......

**P.S.**
You can view the space with "df -H" from the command line

---

### Post by Bucky Ball on 2008-08-02
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=36bd7710-ca84-48c9-9011-e96d336ba192 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=653d41d1-f3d8-4e3c-8fdd-a298084b754c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda7
UUID=4317640b-79fe-4ee4-a761-84f84991256e /media/bigboy	  ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=4893-E3A6				  /media/fatso	  vfat

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fa94dae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3814    30630880+   7  HPFS/NTFS
/dev/sda2            3815        9729    47512237+   5  Extended
/dev/sda5            9365        9729     2931862+  82  Linux swap / Solaris
/dev/sda6            3815        5029     9759424+  83  Linux
/dev/sda7            6246        9363    25045303+  83  Linux
/dev/sda8            5030        6245     9767488+   b  W95 FAT32

Partition table entries are not in disk order


Okay, thanks lots for that. I have deleted sda4 and added sda7 and sda8. I think I need to create mount points/directories? called 'bigboy' and 'fatso', yes???

Still can't access ...

---

### Post by Bucky Ball on 2008-08-02
Hey, cdtech, thanks for everything. With your help and the aid of the page below, some 'deep' thinking, a little copying, pasting and tweaking, and I seem to have successfully mounted my 10gb drive and the 25gb also. At least I can get to the info. Will investigate further. One thing, they are mounted but not as 'fatso' and 'bigboy' as I thought I had managed to do ...

> [http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

This is what I did after deleting /dev/sda4 ...

> 
skulker@HPLappy:~$ ls /media
cdrom  cdrom0  disk
skulker@HPLappy:~$ sudo mkdir /media/bigboy
skulker@HPLappy:~$ sudo mkdir /media/fatso
skulker@HPLappy:~$ sudo mount /dev/sda8 /media/fatso -t vfat -o umask=000
skulker@HPLappy:~$ sudo mount -t ext3 /dev/sda7 /media/bigboy

The drives are on the desktop and accessable, but still named 10GB and 25GB respectively. ?

My current /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=36bd7710-ca84-48c9-9011-e96d336ba192 /               ext3    relatime,erro$
# /dev/sda5
UUID=653d41d1-f3d8-4e3c-8fdd-a298084b754c none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda7
UUID=4317640b-79fe-4ee4-a761-84f84991256e /media/bigboy   ext3    relatime,erro$
# /dev/sda8
UUID=4893-E3A6                            /media/fatso    vfat

Should I go for a restart and see what happens?? Also, although I can read and write to both partitions no problems, can't figure out how to rename the vfat one, and can't unmount either (right click style that is). Telling me need to be root and don't have permissions. ? Checked permission and they seem to be fine ... :(

---

