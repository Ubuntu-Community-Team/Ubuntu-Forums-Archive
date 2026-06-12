---
title: "External HD help needed."
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by RizingDamp on 2008-02-10
Helo,

Well I have posted this problem before, about 1 week ago and did achieve a response but it didnt solve the issue, so hence I am trying again.  I installed Feisty onto a dual boot, dual hard drive system.  Everything went fine, been using it for 1 week, enjoying it so far....in fact havent been back to windows since, as I am doing all what I need to on Feisty :)  But I have a external hard drive connected but when I switch it on I can`t seem to see it anywhere, desktop icon, filesystem or computer etc.  I have tried so far going through the safely remove option in windows and then booting up Feisty then connecting the drive, but still no success.  I have also tried booting up Feisty with it switched on and still nothing.  Here is my lsusb output and the drive I have bolded out.

**Bus 002 Device 005: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter**
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 003: ID 046d:c051 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  


Also this is the section of my lshw output that identifies it.

 *-usb:1
                description: Mass storage device
                product: Cypress AT2LP      RC7
                physical id: 2
                bus info: usb@2:2
                version: 2.40
                serial: DEF10B4886F0
                capabilities: usb-2.00 scsi
                configuration: driver=usb-storage maxpower=2mA speed=480.0MB/s

Im not sure where to go with this problem.....its soo frustrating as all my films are on that drive.

Ps if I plug a flash drive it gets picked up and places an icon on the desktop straight away.



I hope you can help :)

---

### Post by misfitpierce on 2008-02-10
How is the external partitioned? Is it NTFS windows format? If so I believe you may need ntfs read packages in Ubuntu to read a NTFS drive. Is it NTFS or Fat32 formatted?

---

### Post by vanadium on 2008-02-10
To see what could be the reason why it does not mount, try mounting it manually in the terminal. The error message may give a hint on the issue. If you want help, make sure the drive is attached and  post the output here of following commands

sudo fdisk -l
mount

This shows the drives and partitions your system recognizes along with their format. mount tells what is actually mounted and where.

---

### Post by lukem on 2008-02-10
I am having the same problem.  A Seagate external USB drive that used to automount ok with Dapper does not automount and or show up on the desktop since I upgraded to Feisty.  Thumb drives and an IPOD automount and show up on the desktop just as they should.  It's just this Seagate.  The Seagate does the same thing on another pc that also was upgraded to Feisty.  The drive still mounts ok on an xp pc however.    When plugged into the ubuntu PCs it does show up in System>>Preferences>>Hardware Information>>Device Manager.

With the drive connected
**This is sudo fdisk -l**
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000556ed

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe81da79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19455   156272256    c  W95 FAT32 (LBA)

**This is lsusb**
Bus 004 Device 005: ID 0bc2:0500 Seagate RSS LLC 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

**This is mount**
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

**Here is cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=c3b5c9af-3b47-4132-819e-7bc55b591ea8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d352d71b-6665-4ab6-8da4-052bd3bdf6e5 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


Any help would be greatly appreciated.

---

### Post by RizingDamp on 2008-02-10
Helo,

Thanks for the replies guys.  I have just got home its 9.45pm so I wil ltry what u suggested tommorow.   Just thought i would post as I appreciate your help and dont want you thinking it was falling on deaf ears.


Thanks,

Andy :)

---

### Post by RizingDamp on 2008-02-11
Helo again,

Ok heres the results of the fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sda2           25497       60800   283579380    f  W95 Ext'd (LBA)
/dev/sda5           25497       50992   204796588+   7  HPFS/NTFS

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)


Well as you can see its there  /dev/sdb1

And here is the output of mount....


/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


Hope this helps guys.


Once again thanks for your help.


Andy :)

---

### Post by vanadium on 2008-02-11
Your /dev/sdb1 partition is a fat32 partition. The first thing I would think of if it does not mount automatically is a problem with the file system. You should try checking and correcting the drive, either with the Windows tools (chkdsk /f or the graphical tools) or with "fsck.vfat" under Linux (perfectly safe because the fat filesystem has no secrets).

If you are sure the file system is OK, but it still does not mount, then try mounting it manually and eventually post the error message you get here:

mkdir test
sudo mount /dev/sdb1 test

This should give a hint as of why the file system does not mount. If you do not see any output, then your drive will be mounted on test. (for lukem, it will be /dev/sda1 and, yes, it looks like a similar problem! fat32 drive as well!)

---

### Post by lukem on 2008-02-11
Thank you Vanadium. I will give this a try this evening.

---

### Post by lukem on 2008-02-11
I was able to mount the drive with:
luke@luke-desktop:~$ sudo mount -t vfat /dev/sda1 /home/luke/test

I tried fsck.vfat as follows:

luke@luke-desktop:~$ fsck.vfat /dev/sda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:53/44, 72:45/53, 73:41/4b, 74:47/32, 75:41/5f, 76:54/56, 77:45/4f
  , 78:00/4c, 79:00/31
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
No FSINFO sector
1) Create one
2) Do without FSINFO
? 2
Leaving file system unchanged.
/dev/sda1: 28760 files, 3224852/4882315 clusters

Now I want to unmount it and see if the changes made any difference, but I'm not quite sure how to unmount it

---

### Post by lukem on 2008-02-11
I was able to unmount it, but it still does not automount.  :(

---

### Post by vanadium on 2008-02-12
fsck.vfat indicates a problem with the boot sector.Although there is no problem with the file system itself, I guess it it this boot sector problem that is preventing the drive from mounting automatically. You can fix this by running fsck.vfat with certain options (I guess the -a option or the -r option) to effectively perform the repair, and you will have to answer the questions that you have seen now in the output of fsck.vfat. I am not experiences with that myself and not sure how you best answer the questions (perhaps it doesn't even matter too much). Maybe do a quick search before on the error message to see what people usually do in these circumstances.

---

### Post by RizingDamp on 2008-02-12
Hi,

Well I did as you said,

mkdir test
sudo mount/dev/sdb1 test

 sudo mount/dev/sdb1 test
sudo: mount/dev/sdb1: command not found


It looks like I have done something wrong.....sorry I am VERY new to this.


Andy :)

Update.

I tried a few things having submitted my last post.  I typed this into the terminal

 **sudo mount /dev/sdb1 test**

And got this reply......mount: you must specify the filesystem type

So I then tried this having read Lukem`s post

**sudo mount -t vfat /dev/sdb1 test**

I think this worked because I had a look at the test folder it now has a small padlock on it and also I can see the contents of my external hard drive.  But I still did not get an icon on my desktop!

I also unmounted with this command **sudo umount /dev/sdb1**  I hope this is ok....I never received any warnings when I turned off the external hard drive.

---

### Post by vanadium on 2008-02-13
This shows that your drive can mount normally. I guess it is the boot sector issue that prevents the drive from mounting automatically. I would try to fix it using "fsck.vfat -r /dev/sda1" to have the corrections written to disk. You will need to answer the questions. I probably would answer 1 and 1 in both cases.

---

### Post by RizingDamp on 2008-02-15
Sorry for the delay Vanaduim,

Ok so if I try the **fsck.vfat -r /dev/sda1** command will the changes that are made to the boot sector cause any conflicts when using the external hard drive with windows?


Thanks.

---

### Post by vanadium on 2008-02-15
I don know but I really do not think it would cause problems.

---

### Post by RizingDamp on 2008-02-16
Ok Vanadium,

When I manually mount the external hardrive I can read from it but cant seem to write to it.  Any ideas??

---

### Post by tastefulasever on 2008-02-21
Do you have write permission? Try running any commands on the USB drive using sudo.
```
sudo fsck.vfat -r /dev/sda1
```

---

### Post by RizingDamp on 2008-02-23
Ok well I have good news I used the **fsck.vfat -r /dev/sdb1** command and not only can I now write to the drive but when I switch the drive on it now auto-mounts.  So I now get the drive icon on my desktop.

Thanks very much for all your help.

Ps Im sure I will be back with other problems!!

---

