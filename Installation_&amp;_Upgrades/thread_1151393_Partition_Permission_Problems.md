---
title: "Partition Permission Problems"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Elssha on 2009-05-06
I just installed 9.04 on a laptop with 2 extra partitions (one for storage, one for XP) after getting it back from bestbuy. Both are fat32 (ntfs wasn't an option), created during the install. Now they are called by their size and restricted to root mounting/etc.
I only want one of them to automount, and I want to change their names to something other than their size. Anyone know how to change the restrictions to let reg user mount/unmount/rename/etc the partition drives and treat them like other 'removable' media as they were back when I ran Hardy? Thanks, and much appreciated ^_^

---

### Post by logos34 on 2009-05-06
> sudo apt-get install mtools

ex.:

> mlabel /dev/sda1:[new_label]

(source: mtools manpage)

Or use [this method]("https://help.ubuntu.com/community/RenameUSBDrive#FAT16%20and%20FAT32").

To keep from mounting at boot, you can insert a 'noauto' option in the relevant line in /etc/fstab

---

### Post by Elssha on 2009-05-06
I tried mlabel, but it keeps telling me my format for renaming is off 
( Usage: mlabel [-vscVn] [-N serial] drive: )
and nothing happens
I set the mountpoints of the two partitions that I'm having problems with as 
media/[name of partition]
in media/ they show up with the right names, but on the desktop they are named as 
70gb Media and 25gb Media
sudo umount gets rid of them, but they show right back up next reboot

---

### Post by logos34 on 2009-05-07
> 70gb Media and 25gb Media

that's how ubuntu mounts them by default

Like i said above you need to add '[noauto]("http://www.tuxfiles.org/linuxhelp/fstab.html#four")' option to fstab for them not to mount

Try the other method (link I posted above).  

i.e.:

> 
FAT16 and FAT32

...

Change the label

For Ubuntu 8.10 and up, edit mtools.conf as sudo

sudo nano /etc/mtools.conf 

add something like for each drive:

    *

       drive p: file="/dev/sdb1"
       drive q: file="/dev/sdb2"

etc.

Then use

sudo mlabel p:new_label

ex:

    *

       sudo mlabel p:30GB_FAT32

(note the underscore _ should be used, as spaces are not allowed)

[http://ubuntuforums.org/showpost.php?p=6356016&postcount=9](http://ubuntuforums.org/showpost.php?p=6356016&postcount=9)

any luck?

---

### Post by Elssha on 2009-05-07
I edited the mtools file; i checked in my fstab what the original locations were 
```
# /media/Cerberus was on /dev/sda6 during installation
UUID=24EA-BF4E  /media/Cerberus vfat    utf8,umask=007,gid=46 0       1
# /media/Lycan was on /dev/sda3 during installation
UUID=929B-5265  /media/Lycan    vfat    utf8,umask=007,gid=46 0       1
```
the two partitions i'm interested in
so i added the following into mtools.conf
```
# # Cerberus hard disk partition
# drive k: file="/dev/sda6"

# # Lycan hard disk partition
# drive l: file="/dev/sda3"
```
but when i try to edit the name the following error pops up
```
dia@Phoenix:~$ sudo mlabel l:Lycan
Drive 'L:' not supported
Cannot initialize 'L:'
mlabel: Cannot initialize drive

```
sorry to keep bugging you with this... i'll admit it's been a long while since i've had to jump into terminal to fix things >_<

---

### Post by logos34 on 2009-05-07
no, remove the comment ('#'):

> # # Cerberus hard disk partition
drive k: file="/dev/sda6"

# # Lycan hard disk partition
drive l: file="/dev/sda3"

and 

> UUID=929B-5265  /media/Lycan    vfat    [COLOR="Red"]noauto,[/COLOR]utf8,umask=007,gid=46 0 1

---

### Post by Elssha on 2009-05-07
It's still giving me errors >_<
 I did find a way to mask it though (killing all the vol icons on the desktop), which more or less accomplishes the same thing, though now i can't see when an external or dvd mounts... 
Thanks for your help though!

---

### Post by logos34 on 2009-05-07
> **Elssha said:**
> I did find a way to mask it though (killing all the vol icons on the desktop)

shouldn't have to do that, though.  Did a quick search and pulled up [this bug]("http://ubuntuforums.org/showthread.php?t=428224") (->post #4), but it's 2 yrs old, and thus hard to believe it hasn't been resolved...

As for labeling the volumes, you might try booting into xp>my computer>right-click on drive icon>add a custom label.  Maybe linux will see it.

Here are some sample fat32 fstab entries you could try (obviously replace drive and mount with yours):

> /dev/hda1 /media/windows vfat noauto,users,rw,exec 0 0
/dev/hdb1 /media/win1 vfat noauto,users,rw,owner,umask=000 0 0
/dev/hdb1 /fat_files vfat noauto,iocharset=utf8,umask=000 0 0
/dev/hda5 /media/D vfat defaults,noauto,umask=0000 0 0
/dev/hdb1 /fat_files vfat noauto,user,auto,fmask=0111,dmask=0000 0 0
/dev/hda1 /media/windows vfat noauto,user,fmask=0111,dmask=0000 0 0   
/dev/hda1 /media/windows vfat noauto,iocharset=utf8,rw,users,gid=users,umask=000, 0 0

hope that helps

---

