---
title: "Boot drive problem"
date: 2009-08-18
forum: Hardware
---

### Post by XicoXperto on 2009-08-18
Hi there all
I'm a real newbie on this, but I'm enjoying very much...
I made my home/ folder on another drive, so i could format the ubuntu drive and it would stay with same appearance. But got some problem in the middle, I cant figure out what it is, can anyone help me? (but I can skip it)

boot prob log: checkfs

> Log of fsck -C3 -R -A -a 
Tue Aug 18 15:33:33 2009

fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
/dev/sdb5: 6351 files, 1932729/2066854 clusters
/dev/sdb8: clean, 10663/394352 files, 154483/1576362 blocks
fsck.ext4: Unable to resolve 'UUID=52201ea5-ed47-4d69-a32f-afe68cdf4fa8'

fsck died with exit status 8

Tue Aug 18 15:33:38 2009
----------------

my: fstab
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=8ceb35c7-fe35-4704-891f-9939f44fbec9 /               ext4    relatime,errors=remount-ro 0       1
# /home/ was on /dev/sdb8 during installation
UUID=31e2abc2-6121-4196-95e4-2af515ee9646 /home/          ext4    relatime        0       2
# /media/Fat was on /dev/sdb5 during installation
UUID=BC0E-CFA2  /media/Fat      vfat    utf8,umask=007,gid=46 0       1
# /media/Outros was on /dev/sda1 during installation
UUID=A894CFA994CF77F8 /media/Outros   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /media/WinVir was on /dev/sdb6 during installation
UUID=52201ea5-ed47-4d69-a32f-afe68cdf4fa8 /media/WinVir   ext4    relatime        0       2
# swap was on /dev/sdb7 during installation
UUID=048426e1-a17e-4706-8de3-10503698c510 none            swap    sw              0       0
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

## Hand made ##
#DISCO Virtual
UUID=3F7282C429352938	/media/WinVir	ntfs	defaults	0	1
#DISCO SERIES
UUID=BEB8F265B8F21B99	/media/Series	ntfs	defaults	0	1
#DISCO Tralha
UUID=789C68369C67ED56	/media/Tralha	ntfs	defaults	0	1
#DISCO BigBoy
UUID=6620AA3C20AA12DB	/media/BigBoy	ntfs	defaults	0	1
##########


ty in advance

---

### Post by SoftwareExplorer on 2009-08-19
What's the output of ```
sudo blkid
```?

---

### Post by SoftwareExplorer on 2009-08-19
Welcome to the Ubuntu forums by the way.

---

### Post by XicoXperto on 2009-08-19
sudo blkid output:
> /dev/sda1: UUID="A894CFA994CF77F8" LABEL="Outros" TYPE="ntfs" 
/dev/sda2: UUID="BEB8F265B8F21B99" LABEL="Series" TYPE="ntfs" 
/dev/sda3: UUID="789C68369C67ED56" LABEL="Tralha" TYPE="ntfs" 
/dev/sda4: UUID="6620AA3C20AA12DB" LABEL="BigBoy" TYPE="ntfs" 
/dev/sdb1: UUID="8ceb35c7-fe35-4704-891f-9939f44fbec9" TYPE="ext4" 
/dev/sdb5: LABEL="FAT" UUID="BC0E-CFA2" TYPE="vfat" 
/dev/sdb6: UUID="3F7282C429352938" LABEL="Virtual" TYPE="ntfs" 
/dev/sdb7: TYPE="swap" UUID="048426e1-a17e-4706-8de3-10503698c510" 
/dev/sdb8: UUID="31e2abc2-6121-4196-95e4-2af515ee9646" TYPE="ext4" 
/dev/sdg1: LABEL="LaCie" UUID="6853-5BA9" TYPE="vfat" 


and thx
\\:D/

---

### Post by louieb on 2009-08-19
Unless you copied /home somewhere else  its on the the same drive different partiton as / (root)

```

#[COLOR=Red] / [/COLOR]was on /dev/[COLOR=Red]sdb[/COLOR]1 during installation
UUID=8ceb35c7-fe35-4704-891f-9939f44fbec9 /               ext4    relatime,errors=remount-ro 0       1
#[COLOR=Red] /home/[/COLOR] was on /dev/[COLOR=Red]sdb[/COLOR]8 during installation
UUID=31e2abc2-6121-4196-95e4-2af515ee9646 /home/          ext4    relatime        0       2

```

---

### Post by XicoXperto on 2009-08-19
yeap, i put the /home/ folder on another partion.
Is that the boot problem?

---

### Post by SoftwareExplorer on 2009-08-19
From your fstab, it looks like a separate /home was set up during the installation. 
I think this will fix the startup check problem.
run ```
sudo cp /etc/fstab /etc/fstab.backup
sudo gedit /etc/fstab
```
and change 
```
# /media/WinVir was on /dev/sdb6 during installation
UUID=52201ea5-ed47-4d69-a32f-afe68cdf4fa8 /media/WinVir   ext4    relatime        0       2
```
to:
```
# /media/WinVir was on /dev/sdb6 during installation
UUID=3F7282C429352938 /media/WinVir ntfs-3g    relatime        0       2
```
And save.

---

### Post by SoftwareExplorer on 2009-08-19
> **XicoXperto said:**
> yeap, i put the /home/ folder on another partion.
Is that the boot problem?
No, I think that worked alright. I think your WinVirtual partition wasn't listed right, so the filesystem checker couldn't find it.

---

### Post by louieb on 2009-08-19
> **XicoXperto said:**
> yeap, i put the /home/ folder on another partion.
Is that the boot problem?

Probably not. SoftwareExplorer seems to have found a real problem - and a fix

BTW: blkid has a bug - sometimes it cache does not get updated - to get around it - make blkid ignore its cache. (see man blkid)

```
sudo blkid -c /dev/null
```

---

### Post by XicoXperto on 2009-08-20
it's working now! muwahahah! :cool:

ty all!

---

### Post by SoftwareExplorer on 2009-08-20
Your welcome. Glad you got it working. :)

---

