---
title: "External HDD mounting issue"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by vs292 on 2007-04-25
Hi guys.

I'm a relative newbie to ubuntu (and linux in general.) I recently installed Kubuntu 7.04 after a couple of months of openSuSe 10.2 . The problem is that I'm trying to mount my external hard drives. It recognises one of my drives (sdb5 'pocket' ?) and mounted it perfectly, but only recognises but does not mount the other 2. I've got 3 externals (100GB 'pocket', 200GB 'vs292', and 320GB 'maxtor')

I ran fdisk-l and got:
```

vs292@vs292:~$ fdisk -l

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       12161    97675200    f  W95 Ext'd (LBA)
/dev/sdb5               2       12161    97675168+   b  W95 FAT32

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38913   312568641    7  HPFS/NTFS



```

and then backed up and edited /etc/fstab using Kate.

This is what I added to fstab:
```

/dev/sdc1	/media/vs292	ntfs	defaults	0	1
/dev/sdd1	/media/maxtor	ntfs	defaults	0	1

```

I just added the last two lines. I want the drives to be mounted in /media as "vs292" and "maxtor". I can't seem to find an entry for sdb5 though :confused:.

I saved fstab and ctrl-atl-backspaced, logged in, and checked /media. The drives didn't mount...

I re-ran fdisk -l and got the same result as before.

I then tried to mount it using :
```

vs292@vs292:~$ sudo mount -t ntfs -o ro /dev/sdd1 /media/maxtor
```
and was told that the mount point /media/maxtor doesn't exist.

OpenSuSE recognised and mounted my drives automatically and had the nice sysinfo:// screen with a list of all media attached etc...

What should I do next? 

Thanks guys:)

---

### Post by taurus on 2007-04-25
```
sudo mkdir /media/vs292 /media/maxtor
sudo mount -a
df -h
```

---

### Post by vs292 on 2007-04-26
> **taurus said:**
> ```
sudo mkdir /media/vs292 /media/maxtor
sudo mount -a
df -h
```

Thanks:)

---

### Post by mjecha on 2007-06-21
This thread was very helpful in beginning to learn how to work in linux/ubuntu (I am using 7.0.4 Feisty Fawn), but it brings up a whole host of questions:
[INDENT]
1. Why does mount not create the mount point if umount automatically removes it?
2. How can you tell where in /dev a particular USB device is going to be without trial and error? Does it stay the same, even if you rearrange cables? How is the order determined (I am referring to /dev/sdb(1) vs /dev/sdl(1), for example, which are both external hard drives I am using).
3. Can you reserve a mount point for a specific device?
4. How do you identify a specific device after it has been disconnected and reconnected to the system? Is this related to UUID?
5. After mounting a drive, what causes it to show up on my desktop and automatically popup a file browser (and what is wrong if it doesn't do this)?
6. What determines which devices are listed in the left-pane "Places" directory of the file browser?
7. Why does my external mount read-write but say I don't have access to it?
[INDENT]```
sudo mkdir /media/Drobo
sudo mount -vwt ntfs /dev/sdb1 /media/Drobo
df -h
```
gives me:
```
/dev/sdb1             2.0T  153G  1.9T   8% /media/Drobo
```
and then ```
ls -lsa /media/Drobo
``` gives me:
```
ls: /media/Drobo: Permission denied
```
And if I run the command as root, I discover:
```

      4 dr-x------ 1 root root       4096 2007-06-17 18:23 .
      4 drwxr-xr-x 5 root root       4096 2007-06-21 04:35 ..
      4 dr-x------ 1 root root       4096 2007-06-17 21:28 dir1
      4 dr-x------ 1 root root       4096 2007-06-16 19:55 dir2
      0 dr-x------ 1 root root          0 2007-06-14 12:27 Games
      4 dr-x------ 1 root root       4096 2007-06-16 19:53 dir3
      4 dr-x------ 1 root root       4096 2007-06-16 20:17 Media
      4 dr-x------ 1 root root       4096 2007-06-16 20:10 Personal
      8 dr-x------ 1 root root       8192 2007-06-16 20:14 pictures
      4 dr-x------ 1 root root       4096 2007-06-16 19:08 dir4
      0 dr-x------ 1 root root          0 2007-06-13 04:43 System Volume Information

```
what option is causing this iteration of permissions? How do I correct it? [/INDENT]
How can I make the mount point persistent and remount itself, with all the correct options?[/INDENT]
Thank you for your help

---

### Post by mjecha on 2007-06-29
There is so much meat here, can anyone help point me in the right direction for any of my questions?

---

### Post by syaochan on 2008-03-13
> **mjecha said:**
> what option is causing this iteration of permissions? How do I correct it?  When you mount a ntfs partition (which does not support unix permissions) as root, all its content becomes property of root. If you want it to belong to another user mount it with uid=number_user_id. If you want to set the permission use "umask=". **man mount** for more info.

---

