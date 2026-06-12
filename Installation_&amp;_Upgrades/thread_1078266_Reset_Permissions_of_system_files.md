---
title: "Reset Permissions of system files"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by agnimidhun on 2009-02-23
Hi All,

I am running Ubuntu 8.10. For some software testing, I have soft links of gcc, ar, ld etc in my home folder. While testing for and error, I changed the permissions of the links to 666 using sudo. I think it changed the permissions of the main files too. I was not able to open any application (error: permission denied). 

After I rebooted, it would not recognize the keyboard or the mouse. So I cant even login. 

I preferably do not want to reinstall Ubuntu again. Is there a way to reset the permissions on the system files ? (May be after booting from the Live CD ?)

---

### Post by spiderbatdad on 2009-02-23
directories, not files, need at least execute permission by the owner in order to viewable, however I dont understand what happened in your case. You should be able to boot into recovery. Or boot from the live cd...open a terminal and try something like:
```
sudo fdisk -l
```Locate Ubuntu:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris
Mon Feb 23
Accepting commands: ~$ 

```sda1 in the above example.
```
sudo mount -t ext3 /dev/sda1 /mnt
cd /mnt
ls -l
# find directories. edit permissions
```
Lazy umount:
```
 sudo umount -l /mnt 
```

---

