---
title: "Corrupted: boot/grub/menu.lst"
date: 2008-10-29
forum: General Help
---

### Post by ChurroLoco on 2008-10-29
In an effort to take away some of the ubuntu boot options.  (I had like six option to boot Ubuntu that all seemed to be the same)  I went in to edit my boot/grub/menu.lst.

I was an idiot and I deleted the parts that appeared to be the extra duplicate options, and now the one the two options I have during boot don't work.

The section I edited looks like this:

```
## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=08b880fe-7281-46bd-88a7-ddf9f65314e2 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=08b880fe-7281-46bd-88a7-ddf9f65314e2 ro single
initrd /boot/initrd.img-2.6.24-21-generic

 
title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
```

Could someone post this section of their boot/grub/menu.lst file so I can  fix mine?  Thanks!  MUST COMMENT OUT NEXT TIME!

---

### Post by caljohnsmith on 2008-10-29
When you say the entries "don't work", what error do you get? Also please post:
```
sudo fdisk -lu
```
Figure which is your Ubuntu partition in the form sdXY (like sda1 if your menu.lst isn't too far off) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -l /mnt/boot
sudo blkid
```

---

### Post by ChurroLoco on 2008-10-29
Few, OK in windows I was able to find a backup of the original so fixed that menu.lst file, but I think a good part of my problem comes from another issue I have been ignoring.

Recently ubuntu did a disk check and an error popped up. I just restarted and skiped the disk check because I was in a rush and everything seemed to worked.  For days I would just skip the check so this error would not appear.

Should I try running the disk check after I skip inside ubuntu?

```
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.

fsck died with exit status 4
Checking drive /dev/sda1: 42% (stage 1/5, 1402/2310)

*An automatic file system check (fsck) of the root filesystem failed.  A manual fsck must be performed, then the system restarted the fsck should be perform in maintenance mode with the root filesystem mounted in read-only mode.

*The root filesystem is currently mounted in read-only mode.  A maintenece shell will now be started.  After performing system maintnence, press CONTROL-D to terminate the maintnance shell and restart the system.

BASH: no job control in this shell
BASH: groups: command not found
BASH: lesspip: command not found
BASH: Command: comand not found
BASH: The: Command not found
BASH: dircolors: command not found
BASH: Command: command not found
BASH: The: command not found
root@MyUserName-desktop:~#
```

---

### Post by caljohnsmith on 2008-10-29
Yes, I would run the fsck, and I think you can do it safely if you boot into recovery mode. But first do:
```
mount | grep sda1
```
And make sure that command doesn't return anything, because if it returns a line about sda1, it means sda1 is mounted; and one should never run fsck on a mounted file system. If it doesn't return anything, you can proceed with:
```
sudo fsck -y /dev/sda1
```
Or you can boot your Live CD and run the fsck on sda1 from a terminal.

---

### Post by ajgreeny on 2008-10-29
Another good way to check your file system is to use the command ```
sudo touch /forcefsck
``` before you restart or shutdown.  At the next boot the file system check, fsck, will be run.

---

