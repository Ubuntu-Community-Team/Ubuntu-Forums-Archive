---
title: "Newbie Permissions /etc/fstab"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by barryp3uk on 2006-01-15
Hi

I wrote a while back in previous incarnation & was very grateful for the response. My set up has changed now & I'm grappling with the old 

root = owner=> permissions=> rw thing.

I've read the FAQs & I've read a lot of messages on this forum too but I can't get my head around it. It seems that there is more than one way to skin this cat!

So...

I'm dual booting. Ubuntu is in a partition of the same HDD as Win XP. All the partitions which I'm trying to write to are FAT32.

Here's what my fstab looks like:

=-=-=-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults	        0	0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda5       /media/sda5     vfat    defaults        0       0
/dev/sda6       /media/sda6     vfat    defaults        0       0
/dev/sda7       /media/sda7     vfat    defaults        0       0
/dev/sda8       /media/sda8     vfat    defaults        0       0
/dev/sda9       /media/sda9     vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


=-=-=-

hda is the main drive.
sda is an external storage drive on USB

The problem is exactly the same with both of them as far as I can see.

OK? So  I get myself root permissions & the little check boxes in the properties window aren't greyed out any more. I got to click on the "write" box & the tick mark appears but then immediately vanishes. I can't write to any of my other partitions at all. I'm frustrated because I've tried lots of solutions which I've read & feel that editing this fstab is possibly the simplest wayof putting this right. But all the things have changed made the drive in question disappear altogether!

BTW obviously I had to do a manual partition job when installing. I don't know if I might have screwed that up as I couldn't find anywhere that explained the many options available.

Grateful for clarity & simplicity & a little grumpy .:?: 

Cheers!
Barry.

---

### Post by lha on 2006-01-15
The reason you can't use super-user to change owner or permissions of files is fat doesn't have those properties at all! So you'll have to apply the same ownership and permission on a per partition basis opposed to per file basis as you are used to. To do this, replace "default" with "uid=barryp3uk,umask=077" on vfat lines, eg
```
/dev/hda1 /media/hda1 vfat **defaults** 0 0
```
will become
```
/dev/hda1 /media/hda1 vfat **uid=barryp3uk,umask=077** 0 0
```. This makes you the owner of files on hda1 (uid=barryp3uk) and gives you rwx, all others have no permissions at all. (x is needed to give you access to directories.) If you use "gid=admin,umask=002", files are owned by root and have admin as their group identifier. Root and members of admin group will have unrestricted access to all files, others cannot write to files.

If you want only one user to have rw access, former is simpler. If access is needed by more than one user, easiest thing to do is create a new group that will be used in a similar way as admin in the latter example.

---

### Post by lha on 2006-01-15
I forgot to mention dmask and fmask. They are like umask, but dmask sets permissions for directories and fmask for ordinary files. You can find further info with
```
man fstab
```
and
```
man mount
```.

---

### Post by barryp3uk on 2006-01-15
Hi Lha!

Many thanks, that worked a charm!

Out of interest, if I had managed to work that out for myself - I was trying various things in that column of fstab - where would I have found that fix or information that could have lead a noob like me to work it out?

Cheers!
Barry.:D

---

### Post by lha on 2006-01-15
[QUOTE=barryp3uk]Hi Lha!

Many thanks, that worked a charm!

Out of interest, if I had managed to work that out for myself - I was trying various things in that column of fstab - where would I have found that fix or information that could have lead a noob like me to work it out?

Cheers!
Barry.:D[/QUOTE]
Glad to hear it works.

As I mentioned in my previous post, command "man fstab" gives you info on /etc/fstab and suggests that you might want to take a look at mount's man page. Again man, this time for mount: "man mount". There's a section on fat and its options. I have to admit that man pages are not always the easiest source of information so googling around is a good idea, too. Simple search for [fstab fat write]("http://www.google.fi/search?hl=fi&q=fstab+fat+write&meta=&btnG=Google-haku") provides you with relevant info.

---

