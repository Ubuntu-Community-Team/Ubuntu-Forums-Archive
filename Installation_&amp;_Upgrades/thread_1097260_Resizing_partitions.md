---
title: "Resizing partitions"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by rp181 on 2009-03-15
Right now, i am dual boot with Windows XP Home Edition and the latest Ubuntu, but i have ran out of memory on the ubuntu partition. Is there a way to resize the partitions without formatting the disk?

---

### Post by upchucky on 2009-03-15
yes, but it depends on how much room you have, post the drive geometry so we know how to advise.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by miegiel on 2009-03-15
I suggest the GParted Live CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by eli_d on 2009-03-16
I would second using GParted.  I've always used [SysrescCD Live CD]("http://www.sysresccd.org/Main_Page") ... it has always worked well for me...

there are a couple things you'll need to know, if you use GParted in SysRescueCD ...

1) it will start you at a command prompt.  You can load a gui by typing "startx"  if that doesn't work, there is another command you can enter (can't remember right now) that is printed on the screen after booting.  It'll give you the option to choose the resolution manually before the gui (graphic user interface) loads.

2) you will probably need to resize your windows partition first... and then use the space you free up from that partition to resize your ubuntu partition.  GParted let's you do all of this at once... BUT it's VERY important to let Windows XP load after you resize your windows partition.  When Windows XP does load it'll see that something is wrong with the disk and will run "chkdsk" on a light blue screen at startup.  You really need to let chkdsk run entirely for your Windows XP partition to work with the new partition size.  After you let windows do this, you can restart the PC and load back into ubuntu.  your new space should be ready for use.

3) if you need to use the internet in SysrescueCD live environment, you'll have to type something like "dhcpc" (can't remember the exact command) to get an IP address from your server for internet access.

---

### Post by rp181 on 2009-03-16
ok, before i do anything, here is what came when i did what you said:

phani@phani-desktop:~$ sudo fdisk -l
[sudo] password for phani: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        7928    63649530    7  HPFS/NTFS
/dev/sda3            9367        9725     2883667+  db  CP/M / CTOS / ...
/dev/sda4            7929        9366    11550735    5  Extended
/dev/sda5            7929        9299    11012526   83  Linux
/dev/sda6            9300        9366      538146   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         984      991747+   6  FAT16
phani@phani-desktop:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D4-0C02" TYPE="vfat" 
/dev/sda2: UUID="7ED8CA3BD8C9F187" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda5: UUID="544dd0b5-206a-40e3-8bd3-77685021ab90" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="21789cd1-3eac-4c65-a7e2-6a10b5f2712b" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="KODAK" UUID="0000-0000" TYPE="vfat" 
phani@phani-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=544dd0b5-206a-40e3-8bd3-77685021ab90 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=21789cd1-3eac-4c65-a7e2-6a10b5f2712b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
phani@phani-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              11G  9.6G  304M  97% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  304K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  498M   1% /dev
tmpfs                 500M  144K  500M   1% /dev/shm
lrm                   500M  2.0M  498M   1% /lib/modules/2.6.27-11-generic/volatile
phani@phani-desktop:~$

---

### Post by PenguinsFan on 2009-03-16
Another good option is [Parted Magic]("http://www.partedmagic.com") - its essentially GParted with a few other options like Web Surfing.

Just be careful! If your not careful you can do some damage and lose data by partitioning. If your totally new to GParted / PartedMagic check out the tutorials here: [http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")

Good Luck!

---

### Post by rp181 on 2009-03-16
ok, i downloaded GParted, but now i cant burn it on a CD. My computer has 2 CD drives, 1 read only and 1 RW drive. The R only drive opens fine, but i cant get the tray open for the RW drive ;(. How do i get it to open? Pressing the button on the computer doesnt work.

EDIT: Ubuntu installed GParted, and it runs fine, can i resize from inside ubuntu?

---

### Post by upchucky on 2009-03-17
yup drives r full.

to do partitioning you need to be able to boot from the cd drive, preferably the one that writes so you can burn a cd. the rw needs to be the first drive on the cable set as master. this is so u can write to the drive while using the live cd.

burn gparted to a cd, then boot the cd, you cant partition a mounted drive this is why u need either a live cd or the partitioner on a bootable cd.

you are gonna probably need advanced super grub to set up everything that needs to boot.

and knoppix is a great live cd for troubleshooting/editing and fixing pcs
knoppix comes with both partitioners which is handy if and when one or the other partitioner fails.

---

### Post by rp181 on 2009-03-17
I tried the partitioner on the Ubuntu 8.10 CD, but the partitioner said it failed. I remember this happening on my first install too, what should i do? Also, will this keep all my data?

---

### Post by upchucky on 2009-03-17
you really should back up all precious data first.
with that said, partitioning usually preserves all data, but there are instances where it screws a drive, powerfail, user error.

see my post about knoppix and failed partitioning. back up all important stuff and then it don't matter what happens.

---

### Post by rp181 on 2009-03-17
Im just asking because i dont really have anything to back up too, but ile see what i can do.

---

