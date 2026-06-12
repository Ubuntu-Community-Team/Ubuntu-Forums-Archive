---
title: "GRUB cannot find stage1 even though it's right there"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Redsandro on 2009-04-02
The scenario is rather simple. I have XP and Ubuntu. I restored an image of XP from before Ubuntu, and the GRUB loader is gone. It was in MBR.

Now I want to restore GRUB from a live CD, but it sais it cannot find stage1 or whatever I try and search. Doesn't matter whether I mount or unmount the drive. Here I mounted it to sdb3 just to show it's there:

> root@ubuntu:/media# ls -lah /media/sdb3/boot/grub/
total 216K
drwxr-xr-x 2 root root 4.0K 2009-03-31 20:08 .
drwxr-xr-x 3 root root 4.0K 2009-03-30 12:00 ..
-rw-r--r-- 1 root root  197 2009-03-30 12:00 default
-rw-r--r-- 1 root root   45 2009-03-30 12:00 device.map
-rw-r--r-- 1 root root 8.0K 2009-03-30 12:00 e2fs_stage1_5
-rw-r--r-- 1 root root 7.7K 2009-03-30 12:00 fat_stage1_5
-rw-r--r-- 1 root root   16 2009-03-30 12:00 installed-version
-rw-r--r-- 1 root root 8.6K 2009-03-30 12:00 jfs_stage1_5
-rw-r--r-- 1 root root 4.0K 2009-03-31 21:11 menu.lst
-rw-r--r-- 1 root root 4.0K 2009-03-31 19:51 menu.lst~
-rw-r--r-- 1 root root 7.2K 2009-03-30 12:00 minix_stage1_5
-rw-r--r-- 1 root root 9.6K 2009-03-30 12:00 reiserfs_stage1_5
-rw-r--r-- 1 root root  512 2009-03-30 12:00 stage1
-rw-r--r-- 1 root root 119K 2009-03-30 12:00 stage2
-rw-r--r-- 1 root root 9.4K 2009-03-30 12:00 xfs_stage1_5
root@ubuntu:/media# 

> grub> find /boot/grub/menu.lst
Error 15: File not found
grub> find /media/sdb3/boot/grub/menu.lst
Error 15: File not found
grub> root (hd1,2)
grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no
Error 2: Bad file or directory type
grub> quit

What's up?

---

### Post by ajgreeny on 2009-04-02
I don't know if it will make any difference, but normally the first command in the grub terminal is ```
find /boot/grub/stage1
```not ```
find /boot/grub/menu.lst
```Give that a try to see if it finds anything and then continue with the commands:
   ```
 root (hd?,?)
```
This is the output from the "find" command, like : root (hd0,1).
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```

---

