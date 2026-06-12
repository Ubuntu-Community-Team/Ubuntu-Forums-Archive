---
title: "scratch the dual boot, expand linux partitions"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by factotum218 on 2005-10-28
Hey everyone, long time no post. 

Got a question about the method of doing the following:

I have been running a dual boot system since Hoary's realease with windowsXP. Since the release of Breezy I find myself not having a need for the windows partition anymore.
I've but a lot of stock in configuring Breezy the way I like and was curious about if I could somehow remove NTFS partition and expand my existing /home over what was previously used with NTFS. In a nutshell I want to get XP off the hard drive and dedicate the entire system to Ubuntu without having to do a reinstall.
Anyone have a way to go about doing this?
Thanks in advance.

---

### Post by SickTwist on 2005-10-28
The least painful way to do this is to simply reformat the NTFS partition with a native Linux filesystem (EXT3/ReiserFS/etc.) and mount it wherever you want it. There is a GNOME utility to format partitions under System-->Administration-->Disks.

You can make it mount automatically every time you boot by adding a line to /etc/fstab. If you need help, post the contents of /etc/fstab for us and we'll tell you how to do it.

I wouldn't bother with resizing the partitions unless you have a specific reason to do it.

---

### Post by factotum218 on 2005-10-29
I had thought of that as well, here is my fstab at the moment:

proc            /proc           proc    defaults        0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda6       /               reiserfs notail          0       1
/dev/hda7       /home           reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


it goes pretty much like /windows (60GB),  / (4GB), /home (15GB) right now.
Ive already backed up all my files from hda1 to a couple DVD's so Im not worried about anything happening to that partition, as far as the rest of the system I dont have a whole lot to worry about backing up yet. Its still a pretty fresh install and I already included any config files that I might want to keep.

---

### Post by bionnaki on 2005-10-29
[http://www.ubuntuforums.org/showthread.php?t=79095](http://www.ubuntuforums.org/showthread.php?t=79095)

---

### Post by SickTwist on 2005-10-29
/dev/hda1 would be better place to mount /home since it would give you more space to store your data (again, this is all under the assumption that you are not going to re-partition your drive. Otherwise you could just repartition it however you'd like if you want to reinstall Ubuntu):

1. format /dev/hda1 as resierfs
2. mount /dev/hda1 temporarily:
```
sudo mkdir /mnt/temp
sudo mount -t reiserfs /dev/hda1 /mnt/temp
```
3. copy the data from the old home partition to the new one:
```
cd /home
sudo cp -a . /mnt/temp
```
4. change /etc/fstab to this:
```
proc /proc proc defaults 0 0
/dev/hda1 /home reiserfs defaults 0 2
/dev/hda6 / reiserfs notail 0 1
#/dev/hda7 /home reiserfs defaults 0 2
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```
5. restart to use the new /home partition. If everything works, you can mount /dev/hda7 somewhere else and wipe it clean.

There is one thing I'm not sure about: I do not know if reformatting /dev/hda1 will alter the MBR causing GRUB to fail during the next boot. If anyone could comment on this that would be great. To be extra careful, you could just re-install grub after formatting /dev/hda1 to make sure your computer will be able to boot:
```
sudo grub-install
```

---

### Post by factotum218 on 2005-10-30
Alright, I see how it would work. That is one issue I have kind of wondered about with formating hda1. The whole issue with mbr and grub. If it comes down to it I can always reinstall if things go down the tubes. 
I'd rather reconfigure than have to deal with complete data loss any day.
And I never thought i would have a use for my DVD burner. Although some day it would be nice to have one of those GB pen drives some day.

---

