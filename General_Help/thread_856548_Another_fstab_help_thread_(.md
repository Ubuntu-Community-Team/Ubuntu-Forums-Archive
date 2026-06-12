---
title: "Another fstab help thread :("
date: 2008-07-11
forum: General Help
---

### Post by rbprogrammer on 2008-07-11
Here is my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# [file system]  [mount point]  [type]  [options]  [dump]  [pass]
proc                                        /proc           proc        defaults                                0  0  

# /dev/sda1
UUID=70CCA831CCA7F010                       /media/sda1     ntfs        ro,suid,nodev,noexec,noauto,nouser,async 0  0  
# /dev/sda5
UUID=4f67c2bf-41fd-4650-b8d9-c591a6d5e999   /               ext3        defaults,errors=remount-ro              0  1  
# /dev/sda6
UUID=3335dc66-163c-41c3-b4c0-763df8e03f66   /home           ext3        defaults                                0  2  
# /dev/sda7
UUID=6ae41720-473c-4ec4-81f1-5067a0334371   none            swap        sw                                      0  0  

/dev/hdd                                    /media/cdrom0   udf,iso9660 user,noauto,exec                        0  0  
/dev/hdc                                    /media/cdrom1   udf,iso9660 user,noauto,exec                        0  0  

# /dev/hda1
UUID=e91a3989-da08-40d9-a7a5-1f85a455a856   /media/hda1     ext3        errors=remount-ro,noauto,user,noexec    0  0  
# /dev/hdb1
UUID=fa1e5361-633c-4278-9f99-27d2abe199d6   /media/hdb1     ext2        errors=remount-ro,noauto,user,noexec    0  0  

```
Output of ls /dev/disk/bu-uuid: (with some rearranging)
```

lrwxrwxrwx 1 root root 10 2008-07-11 14:20 70CCA831CCA7F010 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-07-11 10:10 4f67c2bf-41fd-4650-b8d9-c591a6d5e999 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-07-11 10:10 3335dc66-163c-41c3-b4c0-763df8e03f66 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-07-11 10:10 6ae41720-473c-4ec4-81f1-5067a0334371 -> ../../sda7

lrwxrwxrwx 1 root root 10 2008-07-11 10:10 e91a3989-da08-40d9-a7a5-1f85a455a856 -> ../../hda1
lrwxrwxrwx 1 root root 10 2008-07-11 10:10 fa1e5361-633c-4278-9f99-27d2abe199d6 -> ../../hdb1

```
I have tried pysdm, but it made fstab not work correctly for the drives.  And the fstab that I have now (shown above) is configured by hand, but I am obviously missing something because its not working.

This is how I want to use my drives:
[LIST]
[*]sda1: read-only windows partition, mounted only by root and unmounted by anyone
[*]sda5: root partition ( ie. / )
[*]sda6: home partition ( ie. /home )
[*]sda7: swap
[*]hda1: read/write EXT3 drive, mounted/unmounted by anyone
[*]hdb1: read/write EXT2 drive, mounted/unmounted by anyone
[*]hdd/hdc: cd/dvd drives
[/LIST]
The root, home and swap partitions are all fine.  But how do I make my windows partition read-only and mounted by root and unmounted by anyone?  Then how do I make hda1 and hdb1 read/write and mounted/unmounted by anyone?

NOTE:
When I say I want the sda1 drive mounted by root, do I have to do that via command line, or could a dialog box come up asking for an admin password. Like if I were to use the gksudo command.

NOTE:
hdb1 at the moment mounts fine by anyone.  But I want to reformat it was EXT3.  First I will need to move all the files to hda1 when I get the mounting stuff in order.  Then when I reformat it, will I need to change fstab?  (except for the obvious ext2 to ext3 change)

Sorry for the long post, but I wanted to make sure I posted as much as possible to try and get an answer.  And thanks for any help.

---

### Post by rbprogrammer on 2008-07-11
[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Also, I have checked out these pages and more, but I never really going anything to work the way I wanted.

---

### Post by dracayr on 2008-07-11
generally only root can mount/unmount (or users with sudo). you could make a script that unmounts/mounts the partitions that are wanted to be able to be mounted by everyone and then give everyone sudo rights for that script using visudo. I can't explain further right now, have to go off.

dracayr

---

### Post by rbprogrammer on 2008-07-11
> **dracayr said:**
> generally only root can mount/unmount (or users with sudo)...

Well, as of right now, I can mount and unmount hdb1 and can read-write to it.  But it is EXT2.  So I want to fix hda1 like that (ie. read-write and mount/unmount by my without typing a password), move the files from hdb1 to hda1, then reformat hdb1 to EXT3.

Then with all that done, I want hda1 and hdb1 to have read-write permissions by me, and can be mounted and unmounted by me without typing a password.

Those are my first priority.  Changing sda1 (windows partition) is my second priority.

---

