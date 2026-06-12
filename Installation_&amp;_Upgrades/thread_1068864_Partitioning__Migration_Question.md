---
title: "Partitioning / Migration Question"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by OliH on 2009-02-13
Hi,

At present I have a 160 Gb HD (sda) and a 500 Gb HD (sdb). The machine originally came from Dell, with Red Hat installed on sda. A while back I installed ubuntu on sdb.

Ideally I would like to remove everything that is currently on sda and move ubuntu from sdb to sda (sda is faster). I want to create a partition that is 80 Gb in size on sda for ubuntu. I would also like another 80 Gb partition on sda so that I can install Windows Vista and make it dual boot.

I want sdb to be a backup drive so I would also like to repartition that.

Can anyone tell me the easiest way to do this? Would it be to install vista first on sda then install wubi after that, and partition sda from there?

Many thanks in advance,

Oli

PS If it helps, here is the output from sudo fdisk -l:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1053     8393962+   c  W95 FAT32 (LBA)
/dev/sda3   *        1054        1078      200812+  83  Linux
/dev/sda4            1079       19452   147589155    5  Extended
/dev/sda5            1079       19452   147589123+  8e  Linux LVM

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2            2433        7295    39062047+  82  Linux swap / Solaris
/dev/sdb3            7296       19453    97659135   83  Linux

---

### Post by Fire_Chief on 2009-02-13
Actually, could you post the outputs from the following commands?
```
df -ha
cat /boot/grub/menu.lst   <--just everything after the  ## ## End Default Options ## Line
cat /etc/fstab
blkid

```

It will be a lot of info but it will make it much easier to offer specific details on moving and reconfiguring stuff.

Cheers!

---

### Post by caljohnsmith on 2009-02-13
So you also want to install Vista to sda, and then move Ubuntu from sdb to your sda drive to have a dual-boot between Vista and Ubuntu? Or why did you mention Wubi also? Are you planning on installing Ubuntu in Vista too? Definitely I would go ahead and install Vista first to your sda drive, and then use Vista's Disk Management to shrink its partition to make room for Ubuntu. After that, I would use Ubuntu's gparted partition editor to shrink your Ubuntu partitions on your sdb drive so they will fit on your sda drive, and then you can do a simple "copy/paste" of the Ubuntu partitions from sdb to the unallocated space on sda. If you set up a new swap partition rather than copying it, it would be good to assign the same UUID to that swap partition so you won't have to modify a bunch of Ubuntu system files. I can help with that if you want. So does the scenario I just described sound like how you might want to accomplish putting all your OSes on the sda drive?

---

### Post by OliH on 2009-02-13
OK. After df -ha I get:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              19G  5.5G   12G  32% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
/proc                    0     0     0   -  /proc
sysfs                    0     0     0   -  /sys
varrun                2.0G  112K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.7M  2.0G   1% /dev
tmpfs                 2.0G  104K  2.0G   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
fusectl                  0     0     0   -  /sys/fs/fuse/connections
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdb3              92G   16G   72G  18% /home
securityfs               0     0     0   -  /sys/kernel/security
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon         0     0     0   -  /home/analysis/.gvfs

```

cat /boot/grud/menu.lst (after ## End Default):

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c6f49724-ec29-401d-9e1f-2e9358f8a3cc
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c6f49724-ec29-401d-9e1f-2e9358f8a3cc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c6f49724-ec29-401d-9e1f-2e9358f8a3cc
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c6f49724-ec29-401d-9e1f-2e9358f8a3cc ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c6f49724-ec29-401d-9e1f-2e9358f8a3cc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c6f49724-ec29-401d-9e1f-2e9358f8a3cc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		c6f49724-ec29-401d-9e1f-2e9358f8a3cc
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c6f49724-ec29-401d-9e1f-2e9358f8a3cc ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c6f49724-ec29-401d-9e1f-2e9358f8a3cc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c6f49724-ec29-401d-9e1f-2e9358f8a3cc ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c6f49724-ec29-401d-9e1f-2e9358f8a3cc
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c6f49724-ec29-401d-9e1f-2e9358f8a3cc ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c6f49724-ec29-401d-9e1f-2e9358f8a3cc
kernel		/boot/memtest86+.bin
quiet

```

cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c6f49724-ec29-401d-9e1f-2e9358f8a3cc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=39e9ccdb-410a-421b-9b23-95d666ee8e1a /home           ext3    relatime        0       2
# /dev/sdb2
UUID=4f3ac544-ec2c-417d-9955-b9532c39efee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

blkid:

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0B11" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="2A7A-E657" TYPE="vfat" 
/dev/sda3: LABEL="/boot" UUID="b6bf30ad-6905-48ca-9892-b67c3208e30d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="pAbL6L-UVYe-GpKo-HsL6-uc8A-y4mb-PsKA8y" TYPE="lvm2pv" 
/dev/sdb1: UUID="c6f49724-ec29-401d-9e1f-2e9358f8a3cc" TYPE="ext3" 
/dev/sdb2: UUID="4f3ac544-ec2c-417d-9955-b9532c39efee" TYPE="swap" 
/dev/sdb3: UUID="39e9ccdb-410a-421b-9b23-95d666ee8e1a" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

```

Does this help?? Thanks so far...

---

### Post by OliH on 2009-02-13
Re caljohnsmith

Yes I think that sounds like a good way forward. I would prefer not to use wubi unless it makes things substantially easier.

I have the following questions:

1. Will vista automatically remove the existing partitions from sda and take up all the sda space?
2. How easy is it to copy all the files over from sdb to sda?
3. How do I assign the same UUID number to the new swap file?

Please remember that I'm a relative linux newbie.

Many thanks,

Oli

---

### Post by caljohnsmith on 2009-02-13
> **OliH said:**
> 
1. Will vista automatically remove the existing partitions from sda and take up all the sda space?

It depends mainly if you have an "OEM" (Original Equipment Manufacturer) Vista Install CD that came with your computer, or if you have a genuine Microsoft Vista Install CD. If it is an OEM CD, most likely it will erase your whole HDD and install Vista to the entire HDD. If you have a Microsoft Vista CD though, you should be be able to choose which partition to install Vista to. If you deliberately want to delete all the partitions first, I would recommend booting the Ubuntu Live CD, open gparted (System > Admin > Partition Editor), select the correct drive in the drop-down list, go to "Device" > "Create Partition Table" (use the default MS-DOS partition table), and that will wipe your drive clean of all partitions. 
> **OliH said:**
> 
2. How easy is it to copy all the files over from sdb to sda?

If you decide to use the method I described, you aren't actually copying the files from one partition to another, you are copying the entire partitions from the sdb drive to the sda drive. You can do that in gparted by selecting say "sdb1", "copy" it, select your sda drive in the drop down list in the gparted main screen, then "paste" it to the free space you have on the sda drive. 
> **OliH said:**
> 
3. How do I assign the same UUID number to the new swap file?

Once you are done setting up your sda drive and know the swap partition number, you can open a terminal (Applications > Accessories > Terminal) and do:
```
sudo swapoff -a
sudo mkswap -U 4f3ac544-ec2c-417d-9955-b9532c39efee /dev/[COLOR="Blue"]sdaX[/COLOR]
```
Replace sdaX with your swap partition, and that will assign the UUID of your original swap partition to the new one. Anyway, good luck, and let me know how it goes or if you run into problems.

---

### Post by OliH on 2009-02-13
OK, that's great. Thanks very much for your help. Will reply if I have any problems with it (will do it next week).

Oli

---

### Post by Fire_Chief on 2009-02-13
Ok, So here's what it should look like. (and caljohnsmith is on the right track).

Here's a basic order of steps

1. Install Vista on sda
2. During the Vista install, delete all exisitng partitions on sda and re-partition the disk to have just the 80GB partition for Vista. Leave the rest of the disk free.
3. After Vista install completes, boot into GParted Live CD environment. [Get GParted LiveCD here.]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=269898")
5. Shrink home partition on sdb (sdb3) to small enough size that it will fit in the free space on sda (probably 59-60 GB).
6. Copy the root partition (sdb1) from sdb to sda free space. (click apply) Copy the home partition (now shrunk to 59 GB) from sdb to sda.
7. Create swap space at the end of drive using the last 1-2 GB of space. (click apply)
8. Open a terminal window and mount the root partition on sda and edit the /etc/fstab file.```
mkdir /newroot
mount /dev/sda3 /newroot
nano /newroot/etc/fstab
``` Change the mount point references for /, and /home Remove **UUID=..** and put **/dev/sda2** for / and **/dev/sda3** for /home. Save file (Ctrl-X then Y to save).
9. Edit the /boot/grub/menu.lst file ```
nano /newroot/boot/grub/menu.lst
```. Change boot menu entry line for Ubuntu to look like this```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
**root (hd0,2)**
kernel		/boot/vmlinuz-2.6.27-11-generic root=**/dev/sda3** ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
**root (hd0,2)**
kernel		/boot/vmlinuz-2.6.27-11-generic root=**/dev/sda3** ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
Save the file (CTRL-X then Y to save)
10. Now we are going to modify GRUB to boot first and offer the boot menu options.```

sudo grub
find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit

```
11. Unmount temp root we created and reboot.```
cd /
umount /newroot
reboot
```
12. Remove CD and you should get a boot menu with Ubuntu and Windows Vista boot entries.

Cheers!

*Edit: Yes I know using the /dev/sdaX method is not as pretty as keeping the UUIDs but I'm not well versed in UUID stuff.

---

### Post by caljohnsmith on 2009-02-13
> **Fire_Chief said:**
> 
8. Open a terminal window and mount the root partition on sda and edit the /etc/fstab file.```
mkdir /newroot
mount /dev/sda3 /newroot
nano /newroot/etc/fstab
``` Change the mount point references for /, and swap Remove **UUID=..** and put **/dev/sda2** for / and **/dev/sda3** for /home.
You don't have to modify the /etc/fstab file nor the /boot/grub/menu.lst when you copy the partitions over using gparted; both those files use UUIDs, and the UUIDs are preserved when you copy the partitions.

---

### Post by Fire_Chief on 2009-02-13
> **caljohnsmith said:**
> You don't have to modify the /etc/fstab file nor the /boot/grub/menu.lst when you copy the partitions over using gparted; both those files use UUIDs, and the UUIDs are preserved when you copy the partitions.

Nice! I was not aware of that. Most of my partition moving days were before UUIDs were used. That saves a good bit then. :D

Thanks!

---

### Post by OliH on 2009-02-13
Many thanks for the replies so far. 

I also have in mind an alternative configuration, which is to have Ubuntu alone on sda, and Vista on a partition on sdb. 

What I need to do, then, is delete all the partitions that currently reside on sda (essentially wipe the drive), create the partitions on sda from Ubuntu, copy the files over as you have described, then install Vista on sdb. Is that plausible?

If so, can you just give me some advice on the first part? How do I remove all the existing data and partitions and set up new partitions?

Thanks,

Oli

---

### Post by Taemojitsu on 2009-02-13
You actually probably want to install Vista on sdb first, before changing sda at all. That's the hardest part. Migrating data you'll probably have to do all by hand (copy/paste onto an external hard drive would be perfect!, otherwise just copy from your untouched sda after Vista is installed on sdb), since you're reformating everything. The 'migrate data' feature in Ubuntu's installation, if i understand it only works from EXISTING partitions that will not be reformated.

note, i haven't read all of this thread

---

### Post by OliH on 2009-02-14
Thanks,

Have you got any advice on how I would move the stuff over to sda? I basically want to wipe it, create partitions on it then move the partitions that are on sdb on to sda similar to the way the posters have suggested on here.

How do I wipe it and create the new partitions?

Oli

---

### Post by Fire_Chief on 2009-02-16
The GParted LiveCD would make this super easy. I just did a similar thing this weekend to migrate my Mythbuntu installation to a bigger and faster drive.

In GParted, go to /dev/sda and delete all the partitions. Select the /dev/sdb drive and pick the first partition. Choose Copy, then go to /dev/sda and Paste in into the free space, then do the same for the other partitions.  Oh...you can resize it as desired after pasting the partition onto /dev/sda. When it looks good to you, click the Apply button and it will then perform all of the queued operations. When it's finished, the data has been moved.

All you have to do then is reinitialize GRUB on /dev/sda which was covered here eariler but I'll repost ```
sudo grub
find /boot/grub/stage1
root (hd0,X)  <-- where X is the number found from the above command
setup (hd0)
quit
```

Cheers!

---

