---
title: "linking 2 drives  together"
date: 2009-02-02
forum: Hardware
---

### Post by Silvernail on 2009-02-02
This is a new post about an old subject. I recently  installed 8.04 on a desktop with 2 drives. I did not allow installation to partition any of the drives.

80 gig drive for installation
200 gig as second drive.

Nautilus recognizes the 200 drive so I can access it that way. I would like to be able to access it from the command line. Another thread suggested I link to it. What do I link to?

The BIOS reconizes both drives.

Dmesg shows both drives. 
> 
[   20.166372] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   .............
[   .........
[   20.192091] sd 0:0:1:0: [sdb] 398297088 512-byte hardware sectors (203928 MB


Both are reconized in /dev/disk/by-id
```

 ata-Maxtor_6L200R0_L50A0GGH                   scsi-1ATA_Maxtor_6L200R0_L50A0GGH                   usb-Generic_STORAGE_DEVICE_00054-0:0
ata-Maxtor_6L200R0_L50A0GGH-part1             scsi-1ATA_Maxtor_6L200R0_L50A0GGH-part1             usb-Generic_STORAGE_DEVICE_00054-0:1
ata-WDC_WD800JB-00JJC0_WD-WMAM9CJR4065        scsi-1ATA_WDC_WD800JB-00JJC0_WD-WMAM9CJR4065        usb-Generic_STORAGE_DEVICE_00054-0:2
ata-WDC_WD800JB-00JJC0_WD-WMAM9CJR4065-part1  scsi-1ATA_WDC_WD800JB-00JJC0_WD-WMAM9CJR4065-part1  usb-Generic_STORAGE_DEVICE_00054-0:3
ata-WDC_WD800JB-00JJC0_WD-WMAM9CJR4065-part2  scsi-1ATA_WDC_WD800JB-00JJC0_WD-WMAM9CJR4065-part2  usb-Generic_STORAGE_DEVICE_00054-0:4
ata-WDC_WD800JB-00JJC0_WD-WMAM9CJR4065-part5  scsi-1ATA_WDC_WD800JB-00JJC0_WD-WMAM9CJR4065-part5

```


Is going to be as simple as linking 'sda' to 'sdb'?

---

### Post by sedawk on 2009-02-02
I'm not sure what you want to achieve by "linking both drives together" !
Try to describe what are you expecting to happen/to see?

There are some ways to combine two hard drives to look like one, at
least for the user - is this what you are looking for?
(keywords: Raid-0, logical volumes).

What you can do (without repartitioning?) is to put Ubuntu
to the 80 GB disk (or a partition on that disk), that is "/" is
located on the 80 GB disk. To store your stuff to the second
disk you can mount the 200 GB disk to "/home".
(manual configuration in the installer without changing partition
table by changing mount points).

---

### Post by cariboo on 2009-02-02
When mounting a drive via nautilus, it will show a drive icon on the desktop. If you right-click on the icon and select properties, next click the Volume tab and it will tell you where the disk is mounted, see screenshot. In my case you can see that the drive is mounted in /media/storage. If you haven't set up any specific directory to mount the the drive to, the default is  usually /media/disk. To access the drive from the command line in the terminal type:

```
cd /media/disk
```

the above command will change directory to /media/disk.

Jim

---

### Post by Silvernail on 2009-02-02
> **sedawk said:**
> I'm not sure what you want to achieve by "linking both drives together" !
Try to describe what are you expecting to happen/to see?



I have the 80 gig to hold the boot system. I would like the 200 to be a data drive. The 200 is from an older computer that had a 'Linspire' OS. I would like to remove root, sbin, bin, usr, share, etc and etc, to clear  up all the storage room I can.

Use the 80 to install what apts I chose. 

Example of what I need to do now. I am in the process of ripping some cassette tape to burn to disk. I would like to be able to do something like this example

```
cd /sdb
mkdir -m 777 placetostoremovies
cd placetostoremovies
cat /dev/video0 > testmsg.mpg

```

Or 'cat /sdb/something.txt'
Or:
when I  do 'sudo updatedb', it will read the /sdb drive and then when I do 'locate something' it will show which drive it is on.

When all is  said  and done, I would much rather do these things from the command line.

Thanks for replying
Dave

---

### Post by Yashiro on 2009-02-03
> Nautilus recognizes the 200 drive so I can access it that way. I would like to be able to access it from the command line. Another thread suggested I link to it. What do I link to?You link to the mount point. Which for an internal drive you should set up in /etc/fstab.

> sudo blkid
Make a note of your 200gb drives label and UUID.

In fstab
'storage' is the disks label. You can change it with e2fslabel if you want.
> # /dev/sdb1
UUID=*ba636202-3275-45ed-b485-da35aa659c61 *    /mnt/storage               ext3        defaults,errors=remount-ro,noatime,users    0   2
cd ./mnt/storage
touch ./mnt/storage/afile.txt
etc.


To be honest it may already be mounted. Look in /mnt or /media after you boot up.
Just remember that in Linux a drive is not a 'C drive' like windows, it is a filesystem. And all filesystems are mounted in much the same way; in fstab at boot or by using the mount command

---

### Post by bhaverkamp on 2009-02-03
Yashiro below is giving good directions for setting up fstab. This is a common configuration. I have a second drive setup and mounted as /home so that my personal files survive OS upgrades and such even if I have to reformat by boot and system drives. I definitely recommend this configuration. You can test this out from the command line with the mount command

mount /dev/sdb1 /{mount directory}

---

### Post by Silvernail on 2009-02-10
OK, guys, I'm in. Thanks to all of you for your time and knowledge.

A couple of last questions. I would like to write a script file and make it accessible with an icon from the panel at the top of my screen.

Do I read it correctly in the 'sudo' manual that using the '-p' option I can pass the required password in a script file?

Where do I put that script so that it shows up in the panel and is executable? Actually is there some place I can put  it or a reference to it so it is automatically run at boot up?

Lastly, in the majority of the cases when I come to ya'll for help, I am referred back to an 'Ubuntu Howto'. I usually search for these before I post here but do not find them. Is there a 'index' I could reference?

Again THANKS.
Dave

---

