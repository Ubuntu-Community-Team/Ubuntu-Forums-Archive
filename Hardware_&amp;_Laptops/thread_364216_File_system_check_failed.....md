---
title: "File system check failed...."
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by rami on 2007-02-18
I get the following error when booting up (see attached picture). I am running Kubuntu Edgy and the output of /var/log/fsck/checkfs gives me this:

```
Log of fsck -C -R -A -a
Sun Feb 18 07:49:06 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=ed1ccc32-485b-4b4f-9548-776a9b94d723'
/dev/hda4: clean, 1723/6602752 files, 767185/13199405 blocks
fsck died with exit status 8

Sun Feb 18 07:49:06 2007

```

Invoking CTRL-D successfully boots up my system. But such error seems troublesome! Whats wrong?

---

### Post by rsambuca on 2007-02-18
Easy fix.  What has happened is that one of the drive partition's UUID has changed, so Edgy can't figure things out.  Did you try a different install or something?

In any event, open a terminal and enter this command to see all of your UUID's```
ls /dev/disk/by-uuid/ -alh
```
Leave that terminal open so you can refer to the UUID's.

Open another terminal and edit your /etc/fstab:```
gksudo kate /etc/fstab
```

The kate text editor should now open your fstab file which lists your partitions and their UUID's.  Find the one in the fstab file which doesn't match the first terminal's listings and correct it.

Save the new fstab and your problem will be gone!

---

### Post by rami on 2007-02-18
Thanx rsambuca much appreciated. Will do that as soon as I get back home (at work now)

What I did is play around with Partimage. I backed up my current main system using partimage (Kubuntu). And just out of curiosity I copied that image to another partition (hda3). This rendered this error. Of course all this was on livecd.

---

### Post by rsambuca on 2007-02-18
I am a gnome guy for the most part, but rather than gksudo, it might actually be gksu.  Everything else should be correct, though.

---

### Post by rami on 2007-02-18
Ya I know, but still it worked to my bewilderment....

---

### Post by kamilek_snk on 2007-05-04
I have some problem, but i have different  log:
> 
/dev/hda7: 1257 files, 907329/1061776 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda8: 6278 files, 726001/1061776 clusters
/dev/hda10 contains a file system with errors, check forced.
/dev/hda10: Inode 561468 has imagic flag set.  

/dev/hda10: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Fri May  4 12:01:23 2007
----------------

I enter this command > fsck
But terminal tell me 
orginal message (polish)
> krzaku@krzaku-desktop:~$ fsck
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hda11 jest podmontowany.  

UWAGA!!! Uruchamianie e2fsck na podmontowanym systemie plików
mo&#380;e spowodowa&#263; POWA&#379;NE uszkodzenie systemu plików.

Naprawd&#281; kontynuowa&#263;? (t/n)? nie


English version (translted)

> krzaku@krzaku- board fsck fsck WIP Nov -2006) WIP Nov -2006) dev /hda11 is undermount. note!! Debugging e2fsck to undermount arrangement file may produce Breakdown arrangement file. Verily continuation? (y/n)? not

---

### Post by kamilek_snk on 2007-05-05
It is ok now. I repair all :) , I use LiveCD end umount hda11 end made FSCK

---

### Post by njkillian on 2007-08-21
Sam
I have ubuntu 7.04 and this is my error:
Log of fsck -C -R -A -a 
Tue Aug 21 18:40:55 2007

fsck 1.40-WIP (14-Nov-2006)
/home: clean, 114025/5128192 files, 7008223/10239429 blocks
/dev/sda: clean, 10348/24428544 files, 41250079/48840246 blocks
/dev/sdb: clean, 3287/24428544 files, 37555924/48840246 blocks
fsck.ext3: Unable to resolve 'UUID=a9cdbf61-bc17-4997-9c62-a74fc91fd5c3'

fsck died with exit status 8

Tue Aug 21 18:40:55 2007
----------------

I did the steps outlined here, but the UUIDs look the same to me...some other problem?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1fe26a70-b862-4887-adeb-d84f3f22fb4f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=9a281aee-4b48-4eeb-881b-39c81a7f89d0 /media/hda2     ext3    defaults        0       2
# /dev/hdb1
UUID=a9cdbf61-bc17-4997-9c62-a74fc91fd5c3 /media/hdb1     ext3    defaults        0       2
# /dev/sda
UUID=0c1734aa-b01c-4b8b-9bd4-77e48a60cf6c /media/sda      ext3    defaults        0       2
# /dev/sdb
UUID=c0575518-8674-4e2b-a9ec-df519a757703 /media/sdb      ext3    defaults        0       2
# /dev/hda3
UUID=440c88e4-4555-4380-91e3-6a0121042259 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1fe26a70-b862-4887-adeb-d84f3f22fb4f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=9a281aee-4b48-4eeb-881b-39c81a7f89d0 /media/hda2     ext3    defaults        0       2
# /dev/hdb1
UUID=a9cdbf61-bc17-4997-9c62-a74fc91fd5c3 /media/hdb1     ext3    defaults        0       2
# /dev/sda
UUID=0c1734aa-b01c-4b8b-9bd4-77e48a60cf6c /media/sda      ext3    defaults        0       2
# /dev/sdb
UUID=c0575518-8674-4e2b-a9ec-df519a757703 /media/sdb      ext3    defaults        0       2
# /dev/hda3
UUID=440c88e4-4555-4380-91e3-6a0121042259 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by bharkins on 2008-04-10
> **rsambuca said:**
> Easy fix.  What has happened is that one of the drive partition's UUID has changed, so Edgy can't figure things out.  Did you try a different install or something?

In any event, open a terminal and enter this command to see all of your UUID's```
ls /dev/disk/by-uuid/ -alh
```
Leave that terminal open so you can refer to the UUID's.

Open another terminal and edit your /etc/fstab:```
gksudo kate /etc/fstab
```

The kate text editor should now open your fstab file which lists your partitions and their UUID's.  Find the one in the fstab file which doesn't match the first terminal's listings and correct it.

Save the new fstab and your problem will be gone!

I have the same problem. I ran the kate editor and then looked at the fstab file. The UUID on the error partition does not look like the number in the error file when booting Hardy. In the same line under options, states "errors=remount-ro"

What now - does remount mean reinstall? (I hope not!)

---

### Post by rsambuca on 2008-04-11
No, you don't have to re-install.  Just correct the UUID and you will be fine.

---

### Post by bharkins on 2008-04-11
> **rsambuca said:**
> No, you don't have to re-install.  Just correct the UUID and you will be fine.

How? Correct the UUID to what? I need a step by step solution. I am a total noob on terminal commands.

---

### Post by rsambuca on 2008-04-12
If you copy and paste the output of these two commands, we can tell you how to fix this.```
ls /dev/disk/by-uuid/ -alh
``````
cat /etc/fstab
```

---

