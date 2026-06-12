---
title: "problem with mounting."
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by mikul on 2005-12-06
i just installd a new kernel(2.6.14) and it seams to work fine, exept for the mounting of the hardrives.
i get "mount: /dev/hdb1 already mounted or /home/mikul/share busy" when i try to mount and when i try to umount i get 
"umount: share: not mounted". 

and the bootlog says: 

> Wed Dec  7 03:12:32 2005:  * Checking root file system...       ^[[80G Warning: fsck.reiserfs warning: option 
Wed Dec  7 03:12:32 2005: No Implementation: Sorry, not implemented yet!

and the mtab says:
> /dev/hda1 / reiserfs rw,notail 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0

if it has anything to do with it?

fstab: 
> /dev/hdd1       /home/mikul/share2      ext3            defaults                        1       2
/dev/hdb1       /home/mikul/share       reiserfs        notail                          0       0

anyone that knows what the problem could be?

---

### Post by amohanty on 2005-12-07
>  /dev/hda1 / reiserfs rw,notail 0 0

I am assuming your /boot is also on reiserfs. What version is the reiserfs? The reason I ask is because I read somewhere (quite some time back though - so it might have changed) that GRUB has problems bootin off of some of the newer versions of ReiserFS. There was some mention of a patch, but I am guessing that would be a problematic way to go.

HTH

---

### Post by mikul on 2005-12-07
the strange thing is that the not even the ext3 hdd dosent mount.
only the root (reiserFS 3 i think).

---

### Post by amohanty on 2005-12-07
If you are getting a device busy while trying to mount /dev/hdb1, try:

```
lsof /dev/hdb1
```

This should tell you what processes are using the drive/partition. Kill those guys and proceed.

Also why this:
```
 /dev/hdd1 /home/mikul/share2 ext3 defaults 1 2
```
This tells the OS to dump the fs if it needs to be and do an fsck on it 2nd (order starts from 1) during bootup. I dont think you need this. To backup the drive use a separate cron job if possible and switch the last two numbers to 0.

Some basic details on fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

```
/dev/hdb1 /home/mikul/share reiserfs notail 0 0
```
Add a defaults before notail and see what happens

HTH

---

### Post by mikul on 2005-12-09
i've tried that now but still dosent work. 
when i run the lsof /dev/hdb command i dosent get anything.

both ext3 and reiserfs is builtin in the kernel, and the root is set to reiserfs so i cant understand why it wont mount.

any clues?

---

### Post by Vandaboy on 2005-12-13
[QUOTE=mikul]i've tried that now but still dosent work. 
when i run the lsof /dev/hdb command i dosent get anything.

both ext3 and reiserfs is builtin in the kernel, and the root is set to reiserfs so i cant understand why it wont mount.

any clues?[/QUOTE]
read here [http://ubuntuforums.org/showthread.php?t=85444&highlight=mounted+busy](http://ubuntuforums.org/showthread.php?t=85444&highlight=mounted+busy)
worked for me too using the loop option on an EXT3 drive. I don't know if this is a proper way of doing it or just a temporary workaround.

Lost the drive wich was working fine to "already mounted or busy" after a kernel update.

---

