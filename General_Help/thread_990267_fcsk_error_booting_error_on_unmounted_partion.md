---
title: "fcsk error booting error on unmounted partion"
date: 2008-11-22
forum: General Help
---

### Post by dougggg on 2008-11-22
I had made a ext2 partion but decided to make it NTFS and unmounted and re-formated.  my mach is dual boot (win xp and ubuntu) I thought I did it right but now when I boot ubuntu it stops in the middle of booting and ask to fsck.ext error repair manually or press ctrl-d.  I press ctrl-d and all is good.  How can I get that partition out of the boot process?  Is there a file I Can edit?

Thanks:)

---

### Post by taurus on 2008-11-22
You probably have set a wrong flag in /etc/fstab for that partittion.  Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

Otherwise, make sure the last two values for your ntfs entry are 0 0.

---

### Post by dougggg on 2008-11-22
here is the result from the terminal

under fdisk the one I changed to NTFS is sda6
and based on the uuid (4f682849-edf0-4b40-977f-b8a991ce01f7 /root)  thats where the error on boot occurs
but once boot all is well I just would like to avoid the extra step on boot up

Thanks
------------------------------------------------------------------

root@doug-laptop:/home/doug# sudo fdisk -l

Disk /dev/sda: 120 GB, 120031511040 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         637     5116671   12  Compaq diag
/dev/sda2   *         638       10499    79208482    7  HPFS/NTFS
/dev/sda3           10500       14593    32877022    5  Extended
/dev/sda6           10500       11715     9759487    7  HPFS/NTFS
/dev/sda7           11716       14419    21711847   83  Linux
/dev/sda5           14420       14593     1389622   82  Linux swap
root@doug-laptop:/home/doug# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=b068f655-c844-4d13-a4e0-d1656d0a69f3 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=4f682849-edf0-4b40-977f-b8a991ce01f7 /root           ext2    relatime        0       2
# /dev/sda5
UUID=d589dd64-cb96-4d06-ab8d-50f88995dca2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
root@doug-laptop:/home/doug# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              21G  5.1G   15G  27% /
tmpfs                 499M     0  499M   0% /lib/init/rw
varrun                499M  316K  499M   1% /var/run
varlock               499M     0  499M   0% /var/lock
udev                  499M  2.8M  497M   1% /dev
tmpfs                 499M  388K  499M   1% /dev/shm
lrm                   499M  2.0M  497M   1% /lib/modules/2.6.27-7-generic/volatile
root@doug-laptop:/home/doug#

---

### Post by dougggg on 2008-11-22
in regards to the last 2 values being 0 it looks like they are 0 and 2,  how can I change that ?

---

### Post by taurus on 2008-11-22
> **dougggg said:**
> 
root@doug-laptop:/home/doug# sudo fdisk -l

Disk /dev/sda: 120 GB, 120031511040 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         637     5116671   12  Compaq diag
/dev/sda2   *         638       10499    79208482    7  HPFS/NTFS
/dev/sda3           10500       14593    32877022    5  Extended
**[COLOR="Blue"]/dev/sda6           10500       11715     9759487    7  HPFS/NTFS[/COLOR]**
/dev/sda7           11716       14419    21711847   83  Linux
/dev/sda5           14420       14593     1389622   82  Linux swap
root@doug-laptop:/home/doug# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=b068f655-c844-4d13-a4e0-d1656d0a69f3 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda6
**[COLOR="Blue"]UUID=4f682849-edf0-4b40-977f-b8a991ce01f7 /root           ext2    relatime        0       2[/COLOR]**
# /dev/sda5
UUID=d589dd64-cb96-4d06-ab8d-50f88995dca2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


You are trying to mount ntfs filesystem as /root!  Not a good idea.  However, you have it down as ext2 in /etc/fstab! 

If you want to change the last value from 2 to 0, edit /etc/fstab with

```
gksudo gedit /etc/fstab
```
Once done, save it and reboot your machine and see if you get that fsck message for /dev/sda5 again.

What's the output of this command from a terminal?

```
sudo blkid
```

---

### Post by dougggg on 2008-11-22
It booted ok changing to zero but can I remove the whole line from fstab? 

# /dev/sda6
[COLOR="RoyalBlue"]UUID=4f682849-edf0-4b40-977f-b8a991ce01f7 /root ext2 relatime 0 2
[/COLOR]

since it really doesnt exist to be thorough

Here is the results from 

root@doug-laptop:/home/doug# blkid
/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat" 
/dev/sda2: UUID="1C90EAE4F001C7B1" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="d589dd64-cb96-4d06-ab8d-50f88995dca2" 
/dev/sda6: UUID="6DA101C051A34C2D" TYPE="ntfs" LABEL="Extra" 
/dev/sda7: UUID="b068f655-c844-4d13-a4e0-d1656d0a69f3" TYPE="ext2" 
/dev/mmcblk0p1: UUID="7019-11E9" TYPE="vfat" 

when I installed ubuntu I took a message to literally and made a /root partition and actually think it meant / partition lol but since I didnt need it I figured I would make for mp3 in ntfs.  anyway thats how I got into this mess lol

but changing to 0 did get it to boot without intervention so that is good

---

