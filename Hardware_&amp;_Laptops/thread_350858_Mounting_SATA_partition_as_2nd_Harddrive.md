---
title: "Mounting SATA partition as 2nd Harddrive"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by bothebobo on 2007-02-01
Its a little complicated so bear with me.
[COLOR="Red"]CURRENT CONFIGURATION:[/COLOR]
Have DEBIAN installed on hdb where during installation the grub/lilo was installed on the hda. Meanwhile on sda i have ubuntu installed with its respective grub installed on the same drive.
[COLOR="Red"]PROBLEM:[/COLOR] 
Everything works fine with my Ubuntu installed on a SATA drive, its also my everyday linux. Now i just installed Debain on my 80GB IDE hdb and blindly followed the installation steps (i installed debian for the music applications: Agnula Project). [COLOR="Blue"]Now i want to be able to access the files on my sda drive from debian but having troubles mounting.[/COLOR]

Hopefully the fdisk from debian will clear things up a little:  
```
bo@bo:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9541    76638051   83  Linux
/dev/hdb2            9542        9729     1510110    5  Extended
/dev/hdb5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       24792   198892732+   5  Extended
/dev/sda5              32       24792   198892701   8e  Linux LVM
```
Notice there's a boot on each drive, and the boot on hdb doesn't work even though Debian is installed there.
[COLOR="Blue"]So here's a quick summary:
hda = mp3's and grub for debian
hdb = debian and boot that doesn't work
sda = ubuntu  and ubuntu's grub[/COLOR]
Now here's the relavent portion of fstab from debian:
[HTML]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda1	/home/bo/1uno	ext3	defaults,errors=remount-ro	0	2
/dev/sda2       /home/bo/3tres	ext3	noatime,nosuid	0	2[/HTML]
Now it will let me mount sda1, but that's just the grub portion of sda and is useless to me.
So when I run mount with the above fstab i recieve:
```
bo@bo:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
and the following dmesg is:
```
sda2: rw=0, want=4, limit=2
EXT3-fs: unable to read superblock
```
Hopefully You can understand i'm in quite of a pickle. 
It might be valuable to know that I can reinstall DEBIAN if need be. Also that my user name and psswd is the same on both systems so I can edit anyfile on either system (didn't think that would work).
I have a followup question: Can I install debian and ubuntu together on the same partition and let a log-on manager decide which to log on to. As-in using the same fstab files and so on, just have the kernal files seperate or is that reserved only for desktop manager and totally insane.
Thanks everybody in advance.

---

### Post by Nik_Doof on 2007-02-01
Its not the Grub portion thats useless, it looks like the remainder of the drive is managed via LVM. Try referencing /dev/sda5 instead of 2.

---

### Post by bothebobo on 2007-02-01
Unfortunetly, still no luck:
[HTML]/dev/sda5       /home/bo/3tres	ext3	noatime,nosuid	0	2[/HTML]
```
bo@bo:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by bothebobo on 2007-02-01
does it have anything to do with it's not ext3 and maybe something called lvm, i dont know that much about the fs types so please help me out

---

### Post by ububaba on 2007-02-05
> **bothebobo said:**
> Unfortunetly, still no luck:
[HTML]/dev/sda5       /home/bo/3tres	ext3	noatime,nosuid	0	2[/HTML]
```
bo@bo:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I have exactly the same situation as you. I waited to see if some one had helped you in 
solving the problem. Probably not. In case you got lucky and things are under control now,
can you please post the right solution. Thanks. :mad:

---

### Post by bothebobo on 2007-02-13
hey ububaba,
ive been on vacation and was hoping for a mess of solutions when i got back. NO luck though. I think i will repost the thread under a new title unless you have a result
later

---

### Post by ububaba on 2007-02-13
> **bothebobo said:**
> hey ububaba,
ive been on vacation and was hoping for a mess of solutions when i got back. NO luck though. I think i will repost the thread under a new title unless you have a result
later

I solved it yesterday the fstab looks like this:
```

Ubu@Ubu-:$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

/dev/sda2 /media/drive2 ntfs nls=utf8,umask=0222 0 0
/dev/sda4 /media/drive4 ntfs nls=utf8,umask=0222 0 0
/dev/sdb5 /media/drive5 ext3 defaults 0 2
/dev/sdb1 /media/drive6 ext3 defaults 0 2


```

Earlier the line with /dev/sda4 looked like this:
/dev/sda4 /media/drive4 [COLOR="Red"]ext3 defaults 0 2[/COLOR]
which is wrong, as my xp2000 is mounted on this partition. 
The correct expression should look like:
/dev/sda4 /media/drive4 [COLOR="Blue"]ntfs nls=utf8,umask=0222 0 0[/COLOR]
Hope your problem is similar and can be solved the way I did.

---

