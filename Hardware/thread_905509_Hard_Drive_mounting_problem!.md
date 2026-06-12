---
title: "Hard Drive mounting problem!"
date: 2008-08-30
forum: Hardware
---

### Post by iampriteshdesai on 2008-08-30
I have a big problem in ubuntu. Ubuntu doesnt mount all my hard drives at booting. So if I fire up Rhythmbox during startup it doesn't play any songs. If I open that drive. D in this case it plays those songs. Untill that point it says media/ path of that folder/ not found. What can I do? Here is my output for sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes

255 heads, 63 sectors/track, 9733 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xeccaecca



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        3150    25302343+   7  HPFS/NTFS

/dev/sda2            3151        9732    52869915    f  W95 Ext'd (LBA)

/dev/sda5            4488        9732    42130431    7  HPFS/NTFS

/dev/sda6            3151        4424    10233342   83  Linux

/dev/sda7            4425        4487      506016   82  Linux swap / Solaris



Partition table entries are not in disk order



Disk /dev/sdb: 40.0 GB, 40060403712 bytes

255 heads, 63 sectors/track, 4870 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x5f4fd0a0



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1        4869    39110211    7  HPFS/NTFS



Here is my output for cat /etc/fstab
iampriteshdesai@Pritesh:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda6

UUID=3fd31233-56f3-4540-8ca2-8499f1e3dbda /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda7

UUID=69e94ed1-ec5f-4fa2-89f7-044371455faf none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by nicedude on 2008-08-30
These are in order I will expain why there is a gap


THIS IS A PRIMARY PARTITION ( YOU CAN HAVE UP TO 4 PRIMARIES )
/dev/sda1   *           1        3150    25302343+   7  HPFS/NTFS

THIS IS AN EXTENDED PARTITION ( WHICH IS A STORAGE CONTAINER THAT YOU CAN MAKE MORE EXTENDED PARTITIONS INSIDE OF )

/dev/sda2            3151        9732    52869915    f  W95 Ext'd (LBA)


THESE ARE ALL INSIDE OF SDA2 AND WITH THESE IT STARTS AT SDA5 AS THAT IS NEXT NUMBER AFTER 4 OR THE MAX NUMBER OF PRIMARY PARTITIONS 

/dev/sda5            4488        9732    42130431    7  HPFS/NTFS

/dev/sda6            3151        4424    10233342   83  Linux

/dev/sda7            4425        4487      506016   82  Linux swap / Solaris

I am pressed for time to explain Fstab and Mtab so I will tell you an easy way to mount your disks for now, use a utility called pysdm as it can mount your disks for you.

Command to install it

sudo apt-get install pysdm

Command to run it after install

sudo pysdm


Once it opens select the drive and then partition you want to mount on the left hand side of the GUI and then click mount and it should do it for you.

Hope that helps and when I get home later I will check here to see if it did :-)

---

### Post by iampriteshdesai on 2008-08-31
Hi!
Your solution worked! Thanx! This problem was bugging me ever since I tried Ubuntu. The same problem crept up in Kubuntu. I had even stopped using Ubuntu. You can imaging my frustration. Rhythmbox and Firefox are the two applications I start first. And when Rhythmbox couldn't play any music it used to be quite frustrating. But thanks to you the problem is solved!
Can I use this tutorial on my Linux blog? I blog at [www.helpforlinux.blogspot.com](www.helpforlinux.blogspot.com) Thanx!

---

### Post by nicedude on 2008-08-31
You can parrot anything I say if it works etc

You should also learn about your fstab and mtab files as they are what control what devices mount at boot time in Linux.

fstab is the what devices will mount at boot

&

mtab is what devices are mounted right now


So if you have a drive that doesn't mount at bootime then you could use pysdm to mount it and then open you mtab file as follows ( replacing gedit with whatever text editor you use - such as kate if in KDE )

sudo gedit /etc/mtab

Now you would copy the last line in mtab ( which is the drive you just mounted via pysdm ) and then you would paste that line into the bottom of your fstab file so that it gets done at each bootup automatically. ( once again replace gedit with whatever text editor you use )

sudo gedit /etc/fstab


Just be carefull when editing fstab and don't change anything other than adding the last line from mtab. Because if you mess around with fstab willy nilly you could have big problems with your bootup.

Hope that helps you figure out mounting of disks as it was quite a pain for me as well until I found pysdm and then later actually learned the fstab & mtab behaviors.

---

