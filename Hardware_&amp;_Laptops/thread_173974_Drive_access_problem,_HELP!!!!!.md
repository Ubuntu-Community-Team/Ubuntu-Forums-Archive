---
title: "Drive access problem, HELP!!!!!"
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by jabeez on 2006-05-11
Ok, I just installed and formatted a 200GB second hard drive as a storage drive. I formatted it in ext3 and have it automounted (fstab) in /media/Storage. I can see it, and it reports the correct free space available, but I cannot write to it. I've tried all (that I know of?!?!?) options in fstab, it just won't give me write access to the drive since it is owned by root, and nothing I've tried will change that. Any help??? This is seriously driving me nuts, here I thought this should be pretty straight forward, using linux filesystem, but alas yet another ridiculous headache. I've been searching forums but any time I see that someone is having the same issue there don't seem to be many useful replies. Must walk away now, or something is going to get broken.................

---

### Post by mips on 2006-05-11
What type of drive is it, be specific ?
Post your /etc/fstab file here.

---

### Post by jabeez on 2006-05-11
It's an IDE Maxtor 200GB, set up as primary slave, all's good in the BIOS. My fstab now looks like......

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda5 /media/windows ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hdb1 /media/Storage ext3 defaults 0 0

I set up the drive using the wiki on installing a new drive, then used a link to an "fstab explained" page, and have gone through it over and over and nothing will work. I seriously can't believe adding a second hard drive is this complicated.

---

### Post by mips on 2006-05-11
Yes, it should be simple.

Have a look at [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Refer to the 4th column and try and mount it with the **user** option. the default is nouser which only gives access to root. Might also wanna look ar the **rw** option.

I'm just taking a stab at things here. Try it you have nothing to loose. Just backup your original fstab.

---

