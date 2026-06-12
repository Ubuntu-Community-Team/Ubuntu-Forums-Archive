---
title: "HELP: K/Ubuntu - external HD not mounting"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by stengah on 2006-06-13
It did autodetect to begin with, but I had to change the default filesystem to fat32 to get writing permissions. I'm sure I've messed up something.

Since I've edited permissions etc. in the tfstab file some, but with little luck, and as of right now the disc doesn't show up as storage media.

When iI try to remount by fstab by doing mount -a in the terminal I get the following error:

       mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Trying this gets me:

[4296789.155000] FAT: bogus sectors per cluster 0
[4296789.156000] VFS: Can't find a valid FAT filesystem on dev sdb1.
[4297002.089000] FAT: bogus sectors per cluster 0
[4297002.089000] VFS: Can't find a valid FAT filesystem on dev sdb1.
[4297091.588000] cdrom: open failed.
[4297091.590000] cdrom: open failed.
[4297296.272000] FAT: bogus sectors per cluster 0
[4297296.272000] VFS: Can't find a valid FAT filesystem on dev sdb1.
[4298537.170000] FAT: bogus sectors per cluster 0
[4298537.170000] VFS: Can't find a valid FAT filesystem on dev sdb1.

My fstab file reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>				<dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hda5 /media/hda5 vfat umask=000,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1 /media/sdb1 vfat user,auto,rw,umask=000   0   0


I'm really lost and apparantly not to clever with linux yet (e.g. I didn't do a fstab backup to begin with. Tried searching other threads, but nothing works. 

Please, can anybody spot the error and help me out?:sad:

---

### Post by tonyr on 2006-06-13
Where did the external drive come from? How is it connected, USB? Was there anything on ti before? What do you expect to see on it?

---

### Post by stengah on 2006-06-13
Tynyr:

It is a brandnew 250 GB Maxtor Personal Storage external harddisc, hence, I don't expect to find any files on it...  It connects through USB.

Any ideas? :(

---

### Post by stengah on 2006-06-13
bumb

---

### Post by tonyr on 2006-06-13
[QUOTE=stengah]Tynyr:

It is a brandnew 250 GB Maxtor Personal Storage external harddisc, hence, I don't expect to find any files on it...  It connects through USB.

Any ideas? :([/QUOTE]

Yes. You need to partition it if you want more than one partition (which isn't really required,
just convenient), and create filesystems on it.  Actually, since it's new, you may 
need to create at least one partition on it anyway. Find out about **gparted**
(System->Administration->Gnome Partition Editor), **fdisk**, and **mke2fs**.
You can look at the Dapper guide in my signature for more information about this,

---

### Post by stengah on 2006-06-13
Tonyr: Thanks for helping!

I'm using Kubuntu. 

I've already tried formatting the drive using GTParted before anything else- I follow your point 'bout several (1+) partitions e.g. with fat3  and ext filesystems, but I could not get that option anywhere... only to format the whole disc with a desired system (tried bot ext and fat32 with little luck)

I don't know much, but I think this must be solve with fstab, or is it possible that the formatting went 'bad'? The error message in Post #1 does imply this and when I reopen GTParted it states the partion type is "unknown".

Though the disc was/is completely empty the format process did go awfully fast... can this be it?

:confused:

---

### Post by caldevil on 2006-06-13
try this:
Comment out the last line of /etc/fstab. Plug out the usb drive and plug it back in. If it doen't automount post back the output of 'dmesg|tail -10'.

---

### Post by stengah on 2006-06-13
Caldevil: First and foremost - Thanks for helping! I sure will do that if the 'besics' below doesn't make it work.

Thing is; I just discovered that it seems I simply didn't do a proper job formatting the drive in the first place (as I suspected)... simply me and GTParted being on different wavelengths. This probably has a LOT to do with it :oops: 

For now I need to hit the sack...it's 2.30 am over here and I'm kinda worn out.

Thanks for helping me... I really appreciate it. I'll let u know how it goes when I return to thois tomorrow (today)!

---

### Post by caldevil on 2006-06-13
That was my guess too. I suggest trying
sudo mkfs.vfat /dev/sdb1

Just make sure sdb1 is the correct device.

---

### Post by wislon on 2006-06-14
Another thing you might be interested in (I came across this myself): some of those external hard disks, especially the ones that take power off a USB port instead of a wall plug or something, often have problems mounting as well. They seem to come and go.

I had one plugged into the two USB slots at the front of my PC, and it caused a lot of pain and suffering when it did this, I couldn't figure out WHAT was wrong. Then one of my mates came in, and on a hunch he plugged it into some USB slots on the back of the PC, closer to the PSU. Voila, no more problems. Turns out that there was a very minor voltage difference at the front, that was just enough to fire the drive up, but not maintain.

Just my 2c :)

---

### Post by breadstic on 2007-11-29
Just thought that i would say that this helped me

>That was my guess too. I suggest trying
>sudo mkfs.vfat /dev/sdb1

I was having problems partitioning my external hard drive into a fat32 filesystem.
parted wouldn't do it. It never reported any problems, it just wouldn't work. It just never put a file system on the partition. Telling it to create a ext2 partition worked fine, so i wasn't sure what was wrong.
I used sudo mkfs.vfat and it worked perfectly first time.

Thanks guys.

---

