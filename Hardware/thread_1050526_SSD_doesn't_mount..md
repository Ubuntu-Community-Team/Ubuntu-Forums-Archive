---
title: "SSD doesn't mount."
date: 2009-01-25
forum: Hardware
---

### Post by alexjean on 2009-01-25
Hi guys, 
I'm running Ubuntu 8.10 on my Eee PC 901 and it has 2 SSDs. My problem is that they don't mount (they don't appear on the desktop) until I open them to browse them. For example: my wallpaper doesn't appear until until I open the SSD it is saved on.

How can I fix this ?

Lots of cowbell for anyone who knows.. !
[IMG]http://img.photobucket.com/albums/v304/xanderz/morecowbell5ri.gif[/IMG]

---

### Post by martinbaselier on 2009-01-25
Open a terminal and type:
```

sudo gedit /etc/fstab

```
and add auto, in the 4th column for the appropriate drive. 
If you don't know what to change post your fstab here. 

And make sure to make a back-up, before changing your file.

---

### Post by alexjean on 2009-01-25
Where do I put 'auto' ?
Also, sdb5 and sdb6 are the partitions I made for Ubuntu... I'm missing sdb1 which is for my files on that drive and I don't see my other drive which is "sda(#)'...

My fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=5d1e5af5-0d13-4e86-94a3-be608ecaa13f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=3232f049-f712-4b06-9c01-63cfad4cf0c0 none            swap    sw              0       0

---

### Post by Hobgoblin on 2009-01-25
I don't think it's anything to do with fstab.

When the drive does appear, where is it mounted (right click - properties - volume)

Also, what do you get if you do **df** in the console?

---

### Post by alexjean on 2009-01-25
/dev/sdb1 is mounted on /media/disk
/dev/sda1 is mounted on /media/disk-1
/dev/sda6 is mounted on /   (it is the Ubuntu partition)

'df' in console: same info

---

### Post by alexjean on 2009-01-26
Anyone ?:-k

---

### Post by alexjean on 2009-01-27
Bump.. !

---

### Post by martinbaselier on 2009-01-28
Adding this should do the trick, assuming they have the fat/fat32 filesystem on them:
Otherwise you can change vfat to ext2, ext3, NTFS or NTFS-3G depending on the filesystem they use.
For /dev/sda1 it's the same.
```

/dev/sdb1 /media/disk vfat auto,user,rw 0 0

```
explanation:
/dev/sdb1 -> device you want to mount
/media/disk -> mountpoint (location where they will be mounted)
vfat -> filesystem
auto -> mount automatically
user -> give all users rights to mount/unmount
rw -> read/write access
first 0: dump will assume file system doesn't need to be dumped
2nd 0: fsck will assume that the filesystem does not  need  to be checked. (for checking use 2; 1 is checking for rootdrive)
for more info: man fstab and man mount

---

### Post by alexjean on 2009-01-29
Thank you martinbaselier, I will check it out during the weekende.. I am so busy otherwise in school. Not using my Ubuntu running laptop sadly. :-({|=

---

