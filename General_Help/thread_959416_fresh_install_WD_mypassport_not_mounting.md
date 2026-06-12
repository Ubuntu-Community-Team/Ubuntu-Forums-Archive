---
title: "fresh install WD mypassport not mounting"
date: 2008-10-26
forum: General Help
---

### Post by yon2501 on 2008-10-26
i just installed ubuntu 8.04 on my familys dell diminsion 4600c and beforehand i backed up all their pictures + music on my external harddrive but for some reason or another it wont mount my hd its a 250gb western digital my passport. whenever i plug it in i get the error message

```
Invalid mount option when attempting to mount the volume 'My Passport'.
``` 

how do i change the mount point of this drive, it shows up on the list as an unmounted drive but wont mount. help as quickly as possible or them might make me switch it back to windows xp after 2 years of convincing them to make the switch. thanks in advance

---

### Post by CorntoeGoblin on 2008-10-26
when you get that error is it in a message box or is that console output??

have you tried manually mounting the drive with the mount command?

i have that exact hd... perfect for a laptop works with the ps3 to

---

### Post by yon2501 on 2008-10-26
it comes up as a window not console, its not showing up under /media thats where it mounts on my laptop. so i dont know what path to use to mount manually

---

### Post by lionheartxxi on 2008-10-26
i had a problem with mounting my WD 1TB external hard drive, after trying all the commands like pmount and mount, i got annoyed so i formatted it again, i lost every thing ofc, but its now mounted and working.

---

### Post by yon2501 on 2008-10-26
well thats not an option i store allot of stuff on mine that took me months to get also all of my familys data is on there from the windows install

---

### Post by TransitMan on 2008-10-26
Have you treid ntfsconfig, available in the repos?
It may help get the drive mounted.

---

### Post by CorntoeGoblin on 2008-10-26
you wouldn't happen to know the file system on the drive? if i'm not mistaken the drive comes formatted to fat32 and 8.04 comes with the support for that file system...

ok why dont you try attaching the drive and then open up a terminal and type lsusb and paste the output here

---

### Post by yon2501 on 2008-10-26
i believe i left it as fat32 also heres the output lsusb 
```
Bus 005 Device 005: ID 1058:0702 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by CorntoeGoblin on 2008-10-26
ok thats good the usb bus recognizes the drive, ok now do sudo fdisk -l and paste output

---

### Post by yon2501 on 2008-10-26
ok heres the ressult
```
Disk /dev/sda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd63d36af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4982     1686825    5  Extended
/dev/sda5            4773        4982     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)

```

---

### Post by CorntoeGoblin on 2008-10-26
ok.... this is strange

ok try this in console

monski@mon-lin:~$ sudo -s
root@mon-lin:~# mkdir /media/wd
root@mon-lin:~# mount -t vfat  /dev/sdb1 /media/wd

tell me what happens

---

### Post by yon2501 on 2008-10-26
HUZZA you sir are awesome it mounted as it should now.

---

### Post by CorntoeGoblin on 2008-10-26
> **yon2501 said:**
> HUZZA you sir are awesome it mounted as it should now.

it's kinda strange that it doesn't mount automatically reboot your computer and try it and maybe it'll mount automatically if not you could create a script that you just double click after attaching the drive and it'll mount it. not very familiar with the auto mount programming so i can't help you there. glad to see another family using gnu/linux :)

have you installed compiz?

---

### Post by yon2501 on 2008-10-26
yeah i use compiz on my laptop but this thing is to old to use any of its more complex features, so ive just got it running desktop wall with 4 desktops.

---

### Post by CorntoeGoblin on 2008-10-26
nice

glad to have helped you

---

