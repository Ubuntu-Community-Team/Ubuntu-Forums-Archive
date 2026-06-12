---
title: "Corrupted partition names"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by budgie9 on 2007-01-20
One of the partitions on my hard disk - hda has had a change of name.
I used a backup program simply backup, to copy files to this partition and it failed to complete the back-up.
It did however change the name of the partition from hda16 to  a o and  two squares.
How do I rename it back again. I am not able to do so from the properties of the partition.

---

### Post by Paerez on 2007-01-20
I thought I had responded to you earlier, but I could be wrong....

Can you post your /etc/fstab?

---

### Post by budgie9 on 2007-01-21
> **budgie9 said:**
> One of the partitions on my hard disk - hda has had a change of name.
I used a backup program simply backup, to copy files to this partition and it failed to complete the back-up.
It did however change the name of the partition from hda16 to  a o and  two squares.
How do I rename it back again. I am not able to do so from the properties of the partition.
As requested and thank you, If you did reply earlier I did not see it.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda12      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda13      /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda10      /media/hda10    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda11      /media/hda11    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda15      /media/hda15    reiserfs defaults        0       2
/dev/hda16      /media/hda16    vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda8       /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda9       /media/hda9     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda14      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Paerez on 2007-01-21
ok that looks fine. Where exactly does it mess up the name?

---

### Post by budgie9 on 2007-01-22
I'm sorry for the delay in the response, it has been a hectic weekend for me here.
As to your question, the bad name show up in Nautilas when the drives are dis[layed. and in the properties of the drive.itself
I did look at the fstab myself and could see nothing wrong, but then some of you guys are better at spotting an  error that I could well miss.

---

### Post by Paerez on 2007-01-22
And you tried opening Computer and right clicking on it to go to properties to change the name there?

---

### Post by budgie9 on 2007-01-22
Yes tried that and it rejects it, and any other changes. It is as if the drive name section is  locked yet accessable via normal means.

---

### Post by Paerez on 2007-01-23
try this:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

It says for usb drives, but it should work for your drives too.

---

### Post by budgie9 on 2007-01-23
I thought at first I was going to get there with your last suggestion.
However, no luck I am afraid to report.
The drive is being seen as hda16, but the label will not change. It seems it is Nautilas that is giving the corrupt label, where as fstab sees it correctly, as hda16 and for that matter XP sees no change from it's empty label. 
The mstools -mlabel commands alter the name itself,  but that is not actually shown as being altered in Nautilas.

Any further suggestions?

---

### Post by Paerez on 2007-01-24
maybe [http://ubuntuforums.org/showthread.php?t=70741](http://ubuntuforums.org/showthread.php?t=70741)

---

### Post by budgie9 on 2007-01-25
Many thanks Paerez for trying your best for me. However nothing worked. I have tried hard to resolve the issue but nothing you have suggested or I have found helped.
I did move allthe files off the drive and re-formatted it in XP that resolved the issue.
I think this is a little drastic for such a minor thing but it has been reported as a bug.

---

