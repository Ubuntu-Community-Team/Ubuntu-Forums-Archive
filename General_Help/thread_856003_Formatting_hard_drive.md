---
title: "Formatting hard drive"
date: 2008-07-11
forum: General Help
---

### Post by RyanfromtheShire on 2008-07-11
Here is what I'm doing:

```
ryan@ryan:~$ sudo su
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@ryan:/home/ryan# fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x8eff8eff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5168    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2383    19141416    7  HPFS/NTFS
/dev/sdb2            2384        4998    21004987+   5  Extended
/dev/sdb5            2384        4884    20089251   83  Linux
/dev/sdb6            4885        4998      915673+  82  Linux swap / Solaris
root@ryan:/home/ryan# mkfs.ext3 /dev/sda
mke2fs 1.40.8 (13-Mar-2008)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
/dev/sda is apparently in use by the system; will not make a filesystem here!
root@ryan:/home/ryan# 

```

Any ideas why it won't let me format this drive?

Also, when I mount it...it says it's only 19.6 GB, and it won't let me move files onto it, or delete anything. (Like lost+found)

[http://img514.imageshack.us/img514/6022/screenshotcp2.png](http://img514.imageshack.us/img514/6022/screenshotcp2.png)

---

### Post by dmizer on 2008-07-11
you can't format the drive because it's in use by the system.  when "mkfs" accesses the drive for formatting, hal daemon senses drive activity and automatically mounts the drive.  since you can't format with a mounted drive, mkfs errors.  to fix this, you have to kill the hal daemon.
```
sudo su
umount /dev/sda1
killall hald
mkfs.ext3 /dev/sda
/etc/init.d/dbus restart
exit
```

you may have to change "/dev/sda1" to the mountpoint (usually /media/usbdisk).

---

### Post by RyanfromtheShire on 2008-07-11
Ok I did what you said. (I mean sdb, but so my command looks different.)

Now it won't let me mount it.

This is what I shows up when I type in fdisk -l

```

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
root@ryan:/home/ryan# 

```

And here is what happens when I try and mount the harddrive through the GUI, as opposed to using the terminal.

[http://img502.imageshack.us/img502/1853/screenshotgn5.png](http://img502.imageshack.us/img502/1853/screenshotgn5.png)

---

### Post by vanadium on 2008-07-11
sda is the drive. sda1 *was* the partition on it. Nevertheless, having a file system without a partition table should work. You did not show the output of the mkfs command, so we cannot know if soemthing went wrong.

Anyway, it might be easiest to use gparted to recreate a partition on the drive, then format the newly created partition to ext3.

---

### Post by RyanfromtheShire on 2008-07-11
Oh ok, here is the log from the mkfs:

```

ryan@ryan:~$ sudo su
root@ryan:/home/ryan# fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
root@ryan:/home/ryan# mkfs.ext3 /dev/sdb
mke2fs 1.40.8 (13-Mar-2008)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
/dev/sdb is mounted; will not make a filesystem here!
root@ryan:/home/ryan# umount /dev/sdb
root@ryan:/home/ryan# killall hald
root@ryan:/home/ryan# mkfs.ext3 /dev/sdb
mke2fs 1.40.8 (13-Mar-2008)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
2449408 inodes, 9770670 blocks
488533 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
299 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 25 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@ryan:/home/ryan# /etc/init.d/dbus restart
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 
 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting network connection manager NetworkManager                    [ OK ] 
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
root@ryan:/home/ryan# 

```

Also, I installed gparted

```

sudo apt-get install gparted

```

Now I don't know what to do next. I really appreciate the help, guys.

---

### Post by dmizer on 2008-07-11
try again ...

first, create a partition table, then format.  more information here: [http://www.linuxquestions.org/questions/linux-hardware-18/not-valid-partition-table-393042/](http://www.linuxquestions.org/questions/linux-hardware-18/not-valid-partition-table-393042/)

don't forget to kill hald before you do any of this.

edit:
it's possible that this could be made easier with gparted.  it's located under system > administration > gparted.

before you open gparted, don't forget to kill hald ;)

---

### Post by vanadium on 2008-07-11
The output shows the formatting went well. In that case, you should be able to mount and access the file system fine.

What to do next? Mount the drive and set ownership and permissions. Is this an internal drive or an external USB drive?

---

### Post by RyanfromtheShire on 2008-07-11
haha ok, hang in there with me guys.

I used the mounting tutorial here:

[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_a_reiserfs_filesystem)



edit: OMG! I got it!

```


ryan@ryan:~$ sudo su
root@ryan:/home/ryan# ls -l /media
total 12
lrwxrwxrwx 1 root root    6 2008-07-11 02:22 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-07-11 02:22 cdrom0
drwxr-xr-x 2 root root 4096 2008-07-11 02:22 cdrom1
drwxr-xr-x 3 root root 4096 2008-07-11 09:40 datapartition
root@ryan:/home/ryan# chmod -R 777 /media/datapartition
root@ryan:/home/ryan# 

```

Just had to change file ownership and permissions.

I got it all from the guide I linked above.

I really wanna thank you guys for being patient and helping me through this!

---

