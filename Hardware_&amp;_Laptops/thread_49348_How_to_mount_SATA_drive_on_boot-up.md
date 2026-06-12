---
title: "How to mount SATA drive on boot-up"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by Umbra on 2005-07-15
I added the correct lines to the fstab file and my IDE partitions are mounted correctly, but i receive error messages like: "/dev/sda1/ does not exist" or something like that on the boot process. 

sda1 to sda6 are my SATA partitions, if i mount them via command line once the entire system is running everything goes ok, but in boot up they seems not to be there, not to be detected. What can i do?

---

### Post by jeremy on 2005-07-16
If you post your fstab maybe someone can help.

---

### Post by Umbra on 2005-07-16
Here it is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# Windows partitions

/dev/sda5       /windows/games  ntfs    nls=utf8,umask=0222 0       0
/dev/sda6       /windows/audio  ntfs    nls=utf8,umask=0222 0       0
/dev/sda7       /windows/files  ntfs    nls=utf8,umask=0222 0       0
/dev/hda1       /windows/system ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /windows/video  ntfs    nls=utf8,umask=0222 0       0

---

### Post by fig_jam_uk on 2005-07-16
i have the same problem too.

my fstab looks like this...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/windows	ntfs	ro,user,umask=002
/dev/sda1	/mp3s		ntfs	ro,user,umask=002
/dev/sda2	/downloads	ntfs	ro,user,umask=002
/dev/sda3	/backup		ntfs	ro,user,umask=002
/dev/sda4	/linuxftp	vfat	rw,user,umask=002


all help greatly appreciated

---

### Post by mo_x on 2005-07-17
Post the output of the following command to chek your partitions:
sudo fdisk -l /dev/sda

---

### Post by fig_jam_uk on 2005-07-17
[QUOTE=mo_x]Post the output of the following command to chek your partitions:
sudo fdisk -l /dev/sda[/QUOTE]


here you go

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101       10200    40965750    7  HPFS/NTFS
/dev/sda3   *       10201       13388    25607610    7  HPFS/NTFS
/dev/sda4           13389       14596     9703260    c  W95 FAT32 (LBA)


thanks in advance

---

### Post by fig_jam_uk on 2005-07-17
ALL SORTED JOBS A GOOD`EN

goto console

cd /etc/rcS.d      <enter>

sudo ln -s ../init.d/mountall.sh          <enter>

enter password         <enter>

reboot

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

what it does is try to remount the drives after hotplug has loaded its modules, just like my machine
when you login you should be presented with all your drives mounted..

p.s. still have your fstab file edited b4 running this

let me know if it works

---

### Post by Umbra on 2005-07-17
Here's my result:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sda6            5101        7650    20482843+   7  HPFS/NTFS
/dev/sda7            7651        9729    16699536    7  HPFS/NTFS 

Now, what do i do?

---

### Post by fig_jam_uk on 2005-07-18
[QUOTE=Umbra]Here's my result:

 

Now, what do i do?[/QUOTE]


Hi umbra if you run the commands in my last post b4 your last post it should work providing your fsatb file is ok.

---

### Post by mo_x on 2005-07-18
I'm not sure about this. My sata partitions mount automatically by it also contains the root / partition. I have a /etc/rcS.d/S35mountall.sh that mounts all partitions on boot, but I guess that is also the case for you.
If the mounting depens om some modules being loaded you can put them in /etc/modules so they get loaded at boot time. Maybe the modules for the chipset and sata drive, amd74xx and sata_nv in my case. Try the command "sudo lsmod" to see what modules are loaded. If you post the output of "sudo lsmod" and the contents of /etc/modules maybe I can say something about it.
Here is the contents of my /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

amd74xx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod

---

### Post by Umbra on 2005-07-18
yes mo_x, if you have your linux system your sata drive, that could be the key. But fig_jam_uk and i have our system in another drive, and our satas are secondary.

---

### Post by Umbra on 2005-07-18
Didnt work for me, i used the commands above with no errors in the process then i reboot but still partitions are not being mounted.  :|

---

### Post by fig_jam_uk on 2005-07-19
[QUOTE=Umbra]yes mo_x, if you have your linux system your sata drive, that could be the key. But fig_jam_uk and i have our system in another drive, and our satas are secondary.[/QUOTE]


Yes that could be it just to confirm my linux install is on a normal ATA drive at the moment and my SATA is just for storage, at least until SATA support grows up a bit more in linux thats all it will be used for.

---

