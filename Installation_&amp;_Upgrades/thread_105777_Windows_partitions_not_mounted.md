---
title: "Windows partitions not mounted"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by kathymacau on 2005-12-19
Not only are they not mounted, they are not listed in fstab.  I have Ubuntu running pretty much the way I want, (and I know what I did to get it that way) so I am planning to format my hard drive.  Change from ntfs to fat32 and install win XP Home.  Then reinstall Ubuntu and set it up using Automatix.

If anyone thinks I'm going about this the wrong way could you please let me know.

Forget it.  I went looking for more help and my windows partitions are now mounted.

---

### Post by tomski on 2005-12-19
you will have to add them to fstab yourself or using the partitioner during install

To add them your self follow these steps

install ntfs tools ,ntfs progs by doing a search in synaptic for ntfs then install the the relevant packages

then open a root terminal & create the directories you require 
(i use /windows/C, /windows/D, /windows/E)
$ mkdir /windows/
$ mkdir /windows/C/  (repeat for each win drive letter you want mounted)

now you have to enter the relevant details into fstab to mount each win partition Drive C:\ in *nix is /dev/hda1 
so the line in fstab would read :

/dev/hda1 /windows/C ntfs ro,umask=0222 0 0

repeat this process for each partition that you require to be mounted,
if you do not know the linux name for each win partition try 
$ fdisk -p

---

### Post by kathymacau on 2005-12-19
Thank you Tomski.

---

### Post by axle_foley00 on 2005-12-19
Cool thanks Tomski. It worked like a charm.

---

### Post by Herman on 2005-12-19
An experience I had with my older computer (with a new hard disk) was that it did not seem able to auto-mount partitions on start-up with Breezy. 
 Then, one day, during a boot-up there was a message on the monitor something like: 'this system has been re-started 30 times without a file system check- forcing file system check. A row of '=' signs progressed across the screen, then the computer resumed its normal booting.
Ever since then this computer has always had these other partitions automatically mounted during a Breezy install and with each re-boot like the other computers we have here. (I didn't even know it was supposed to until after I installed Breezy in the others).

If the suggestions already posted work for you, then all is well. But if the problem persists, try doing a file-system check, it may solve the problem, but only if it happens to be the same problem mine had.

I am not certian about the correct way of doing this, but rather than re-starting your computer 30 times, here's what I tried after googling for a solution for this:
I ran a Ubuntu live CD, and typed:
sudo fdisk /dev/hda -l
sudo fsck /dev/hdaX
'X' being whatever partition the first command's output reveals as being my Ubuntu partition.```

```
I have tested this on my test computer, (which was the one with the problem quite a while ago now, and nothing much appeared to happen, but I got an output to say: fsck 1.35 (28-Feb-2004)
e2fsck 1.35 (28-Feb-2004)
/:clean, 75660/2285632 files, 599870/4638768 blocks

Would a more experienced Ubuntu enthusiast care to comment? Have I done this correctly, and is this the right thing to advise someone having this problem?

---

### Post by Herman on 2005-12-19
I found a better way to force a disk check from this thread, post #12:
[http://ubuntuforums.org/showthread.php?t=31937&page=2&highlight=fsck](http://ubuntuforums.org/showthread.php?t=31937&page=2&highlight=fsck)

I tried it, I typed:           sudo touch /forcefsck

Into a terminal and re-booted and it did the disk-check, the way I wanted.
I think that the previous posts are correct, but this trick is worth a try if you still have trouble after following the previous poster's advice. (Herman).

---

### Post by imranj on 2005-12-20
Second is after i installed my own custom kernel, everything works fabluously, except for i cannot mount my NTFS & Fat32 parititions as it could be done in my earlier kernels the K7 one.

>>>Issue Output<<<<
ijamadar@shj-mjz-bsr2084:~$ sudo mount /dev/hda1 /media/ntfs
Password:
mount: /dev/hda1 already mounted or /media/ntfs busy
ijamadar@shj-mjz-bsr2084:~$


ijamadar@shj-mjz-bsr2084:~$ sudo mount -a
mount: /dev/hda1 already mounted or /media/ntfs busy
mount: /dev/hda3 already mounted or /media/fat busy

/etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / reiserfs notail,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0

/dev/hda1 /media/ntfs ntfs nls=utf8,umask=0222 0 0
/dev/hda3 /media/fat vfat iocharset=utf8,umask=000 0 0


>>>>More Info<<<<
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 7139 57343986 7 HPFS/NTFS
/dev/hda2 7140 9728 20796142+ f W95 Ext'd (LBA)
/dev/hda3 9729 9729 8032+ c W95 FAT32 (LBA)
/dev/hda5 7140 9728 20796111 b W95 FAT32

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 2273 18257841 83 Linux
/dev/hdb2 2274 2434 1293232+ 5 Extended
/dev/hdb5 2274 2434 1293201 82 Linux swap / Solaris

---

### Post by imranj on 2005-12-20
ijamadar@shj-mjz-bsr2084:~$ sudo mount /dev/hda1 /media/ntfs/ -t ntfs -o nls=utf8.umask=0222
mount: /dev/hda1 already mounted or /media/ntfs/ busy
ijamadar@shj-mjz-bsr2084:~$

---

### Post by dragonfyre13 on 2005-12-20
Try this, for those of you who like graphical better than terminal commands.

pysdm is in the universe repository. download that, and then type "sudo pysdm" (minus quotes) into the terminal.

It pops up the pysdm window, and lets you edit the mounts very easily.

---

### Post by dragonfyre13 on 2006-01-25
Ok, I just found a much esier way. Go to System menu, and under administration, there is an app named Disks. You can also access it through:

sudo disks-admin

Choose your HD on the left, and click the partitions tab. Choose your mount point (must be an existing folder, so make one under /media) and click Enable.

---

