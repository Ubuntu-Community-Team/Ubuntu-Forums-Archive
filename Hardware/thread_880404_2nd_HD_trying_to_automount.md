---
title: "2nd HD: trying to automount"
date: 2008-08-05
forum: Hardware
---

### Post by zaine_ridling on 2008-08-05
While I am able to format and partition my 2nd drive using GParted, and I can mount it manually, **I cannot get it to automount**. :confused: My goal is to use the 2nd drive as a backup device. [This similar post]("http://ubuntuforums.org/showthread.php?t=768400&highlight=2nd+drive") helped, but did not solve the problem. Here's the **fdisk -l** result:
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001793f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120124   964895998+  83  Linux
/dev/sda2          120125      121601    11864002+   5  Extended
/dev/sda5          120125      121601    11863971   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7d9ec69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

and here's the **cat /etc/fstab** result:
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=74f8afb2-b1cc-4909-b598-1014eeef8229 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e23ed4d9-d618-498d-820d-a3a0e513b5ce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/bak	ext3	defaults 	0 	0

Thank you if you have the time to futz with this.

---

### Post by GrnFrag on 2008-08-05
I'm not sure, but if your talking about your 500.1gb disk, it appears to be mounted in your FSTAB file, last line.   I think you need the UUID of the drive in there, 
try this.
```
sudo blkid /dev/sdb1
```
to get the UUID of the 500g drive and add it to this line of your FSTAB file, just before /media/bak:
> /dev/sdb1 /media/bak ext3 defaults 0 0 
so this line is telling you that its mounted to /media/bak. To access it, just browse to that location.   things i mount to media usually wind up on the desktop, so look for /bak there too.

hope this helps

---

### Post by zaine_ridling on 2008-08-05
Almost! When I navigate to the drive it reads:
> An error occurred while accessing  'Volume (ext3)', the system responded: mount: only root can mount /dev/sdb1 on UUID=0a5da23d-ae38-488d-8c43-79ab643ef32f/media/bak

Thanks, though!

---

### Post by GrnFrag on 2008-08-05
Well i was hoping someone else would post here.   I'm not sure what the heck is going on.   did you  sudo to edit your fstab file?   like

```
sudo gedit /etc/fstab
```

also, Run
```
sudo blkid -c /dev/null
```
Include the -c /dev/null bit. If you run blkid without options it reads from its cache file. just verify the UUID in the fslab
  

Oh, and please post the fstab file again.

---

### Post by zaine_ridling on 2008-08-06
Actually, you fixed it before. I had a stupid spacing error. My apologies. :KS Thank you! Here's the fstab for future reference:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=74f8afb2-b1cc-4909-b598-1014eeef8229 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e23ed4d9-d618-498d-820d-a3a0e513b5ce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1       
UUID=0a5da23d-ae38-488d-8c43-79ab643ef32f/media/bak	ext3	defaults 	0 	0

---

