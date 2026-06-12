---
title: "[SOLVED] Gparted deleted grub?"
date: 2008-11-13
forum: General Help
---

### Post by skintythe1andonly on 2008-11-13
I was running a dual boot with hardy and intrepid. I managed to work out all the bugs i was encountering with intrepid so i decided to get rid of the hardy partition. During the resizing of the partition, Gparted crashed and became unusuable. I left it go for about 2 hours but still nothing. I had to power it off.

When i powered it on i got grub error 15. I booted to the lice CD and mount my hard drive. It seems to be ok. after some googling i have read a lot of posts telling me follow this post

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

The problem is the line saying 

```
grub>find /boot/grub/stage1
```

This didnt return anything....actually it returned error 15.file not found. I looked at my partition again to find that there is no /boot directory. Gparted must of deleted it...am I right. I am using 64-bit btw.

I think i can reinstall grub from the alternate CD am i right or is there a better solution?

---

### Post by grim4593 on 2008-11-13
[http://ubuntuforums.org/showthread.php?t=224351&highlight=find+uuid](http://ubuntuforums.org/showthread.php?t=224351&highlight=find+uuid)

Try the second half for the example where it can't find grub.

---

### Post by skintythe1andonly on 2008-11-13
Sorry it was very late last night when this happened as i was getting very frustrated.... i should have read the whole post. Will try tonight when im on my laptop.

---

### Post by binbash on 2008-11-13
Yes you are going to re-install grub.You can use most live cds, gentoo fedora etc to repair it.

---

### Post by skintythe1andonly on 2008-11-13
Ok so I had a sabayon disk lying about so i put that in, as i was thinking of giving it a try anyways. I gave it a 35Gb partition. And kept my "ubuntu install" about 80Gb. Sabayons default bootloader is Lilo. I thought that this may have found the ubuntu partition but it didnt. Sabayon only appears on the lilo boot list. fdisk -ls gives the following

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       14593   117218241    5  Extended
/dev/sda5           14241       14593     2835441   82  Linux swap / Solaris
/dev/sda6               1        9727    78132033   83  Linux
/dev/sda7            9728       14240    36250641   83  Linux

Partition table entries are not in disk order

```

What is the best way to fix this?

---

### Post by caljohnsmith on 2008-11-13
How about posting the output of:
```
sudo fsck -y /dev/sda6
```
And if that command completes successfully, please post the output of:
```
sudo mount /dev/sda6 /mnt
ls -lR /mnt/boot
```

---

### Post by skintythe1andonly on 2008-11-13
I get the following output

```
localhost ~ # sudo fsck -y /dev/sda6
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda6: clean, 89670/4890624 files, 3904092/19533008 blocks
localhost ~ # sudo mount /dev/sda6 /mnt
localhost ~ # ls -lR /mnt/boot
ls: cannot access /mnt/boot: No such file or directory

```

This is the problem i think. When Gparted crashed the /boot were not present. Any ideas?

---

### Post by caljohnsmith on 2008-11-13
Actually, if you don't have /boot, it might be that partition only has "lost+found". How about posting:
```
sudo mount /dev/sda6 /mnt
ls -l /mnt

```

---

### Post by skintythe1andonly on 2008-11-13
it seems to have most items including my /home directory which i was able to backup before. (i know i should have this on a separate partition... but thats for another day).

```

localhost ~ # ls -l /mnt
total 112
drwxr-xr-x   2 root root  4096 2008-11-05 02:24 bin
lrwxrwxrwx   1 root root    11 2008-11-05 01:46 cdrom -> media/cdrom
drwxr-xr-x   3 root root  4096 2008-11-05 23:03 debian
drwxr-xr-x   4 root root  4096 2008-10-29 21:18 dev
drwxr-xr-x 122 root root 12288 2008-11-12 22:34 etc
drwxr-xr-x   3 root root  4096 2008-11-05 02:01 home
lrwxrwxrwx   1 root root    27 2008-11-05 19:58 initrd.img -> boot/initrd.img-2.6.27-3-rt
lrwxrwxrwx   1 root root    32 2008-11-05 02:04 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  15 root root  4096 2008-11-11 23:28 lib
drwxr-xr-x   4 root root  4096 2008-11-05 02:44 lib32
lrwxrwxrwx   1 root root     4 2008-11-05 01:46 lib64 -> /lib
drwx------  65 root root 40960 2008-11-05 01:45 lost+found
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 mnt
drwxr-xr-x   3 root root  4096 2008-11-07 00:12 opt
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 proc
drwxr-xr-x  21 root root  4096 2008-11-11 19:50 root
drwxr-xr-x   2 root root  4096 2008-11-11 23:28 sbin
drwxr-xr-x   3 root root  4096 2008-11-06 22:17 srv
drwxr-xr-x   2 root root  4096 2008-10-14 13:02 sys
drwxrwxrwt  10 root root  4096 2008-11-12 22:33 tmp
drwxr-xr-x  12 root root  4096 2008-11-05 02:29 usr
lrwxrwxrwx   1 root root    24 2008-11-05 19:58 vmlinuz -> boot/vmlinuz-2.6.27-3-rt
lrwxrwxrwx   1 root root    29 2008-11-05 02:04 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
localhost ~ #                

```

---

### Post by caljohnsmith on 2008-11-13
The fact that gparted crashed and you now don't have a /boot nor /var directory leads makes me think that a reinstall is definitely your best bet; you really have no idea what other random files could be missing either. Actually I think you're very fortunate you can even access the partition at this point, so if I were you, I would copy over all your important files and reinstall. Good luck and let me know how it goes or what you decide to do.

---

### Post by travmon69 on 2008-11-13
try [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)     or  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by skintythe1andonly on 2008-11-13
I was afraid somebody would say that. Reinstalling is ok but i had just managed to get a linux copy of mathematica off the IT department in college... it took a while to get the disks off them. is there anyway i can preserve that install or do i have to go and annoy the monkeys at the help desk again?

---

### Post by skintythe1andonly on 2008-11-14
i had been looking at supergrub alright. i will look into it but as caljohnsmith pointed out.. which i didnt notice i am also missing my  /var directory so the more i look at this the more i think i fresh install is on cards.

---

### Post by skintythe1andonly on 2008-11-15
ok i tried supergrub and got it to sort of boot. could only get into the failsafe terminal. i have to get some work done this weekend so i just did a fresh install again, and im back up and running. Im going to keep a 25Gb partition for sabayon. I forgot what a nice distro it is. Thanks for you help

---

