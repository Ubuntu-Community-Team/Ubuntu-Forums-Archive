---
title: "No ntfs"
date: 2008-08-20
forum: General Help
---

### Post by Ahmed Amr on 2008-08-20
hi there everyone
i am here new to ubuntu i have just installed it yesterday migrating from win xp and i cant find my other 3 partitions in the computer although i found them before i install the ubuntu and it always tells me that i can't mount this drive due to 2 reasons. but now after i installed it i cant find any of the partitions i had. They were NTFS. can anyone help me please?

Thanks A lot

---

### Post by coffeecat on 2008-08-20
We need to make sure you haven't inadvertently reformatted the NTFS partitions, or whether this is just a problem in finding them.

Go to Places > Computer and see if there are any icons corresponding to your NTFS partitions. They won't be called D:, E: or anything like that - that's a Windows nonsense. Try double-clicking on any you might find and see if they contain what you are looking for.

If that doesn't reveal anything, go to Applications > Accessories > Terminal. In the terminal type:

```
sudo fdisk -l
```That's a lower-case L, not one. Post the output. You can copy and paste from a terminal into the firefox message field. In the terminal add shift to the normal keyboard shortcuts or look in the terminal edit menu.

---

### Post by Ahmed Amr on 2008-08-20
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fc69d74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1593    12795741   83  Linux
/dev/sda2            1959        3824    14988645    7  HPFS/NTFS
/dev/sda3            3825       14946    89337465    f  W95 Ext'd (LBA)
/dev/sda4            1594        1958     2931862+  82  Linux swap / Solaris
/dev/sda5            3825        8923    40957686    7  HPFS/NTFS
/dev/sda6            8924       14946    48379716    7  HPFS/NTFS

Partition table entries are not in disk order

```

---

### Post by coffeecat on 2008-08-20
The output of fdisk is fine. You've got three NTFS partitions still. What happened when you looked in Places > Computer? I realised after I posted that you will only be able to automount NTFS partitions with full read-write in the latest Ubuntu (8.04 = Hardy). Possibly Gutsy as well, but I can't remember exactly. Earlier versions either gave you read only or wouldn't automount NTFS partitions from the GUI. Again, I can't remember exactly; it was too long ago. Which version of Ubuntu are you using and can you confirm you are using Ubuntu/Gnome?

---

### Post by Ahmed Amr on 2008-08-20
ok now i saw my partitions but everytime it tells me "You are not privileged to mount the volume 'Moviez'."
and i am using ubuntu 8.04

---

### Post by coffeecat on 2008-08-20
That's odd. I need a bit of thinking time.

**Edit:** OK - first thought. With 8.04, if you are the first created user, you should be able to mount NTFS partitions without that error message. Are you doing this from your first created account, or from a subsequent account? The first account gets administrative privileges, but subsequent ones do not, unless an administrative account grants those privileges.

---

### Post by Ahmed Amr on 2008-08-20
tyt

---

### Post by Ahmed Amr on 2008-08-20
offcourse i am the first created user any hints?

---

### Post by Uchiha_madara on 2008-08-20
Install The NTFS Configuration tool

from Add/Remove Applications then System and tools 

check on NTFS Configuration tool

Then you can Configure The ntfs Drives and choose the Kind of access
Read/write  and so on

---

### Post by Ahmed Amr on 2008-08-20
i did but thats not the problem. even though the application tells me that it cannot mount the drive  :confused:

---

### Post by Ahmed Amr on 2008-08-21
ok so can anybody help me i always get msg:
 "could not mount Drive
you are not privileged to mount volume 'music' "

---

### Post by SuperSonic4 on 2008-08-21
```
gksudo nautilus
```

then type in ```
/media
``` and then select the drives you want mounted (such as music) and right click and press mount. I think you can change the permissions too since you'll be using nautilus as root

---

### Post by Ahmed Amr on 2008-08-21
> **SuperSonic4 said:**
> ```
gksudo nautilus
```

then type in ```
/media
``` and then select the drives you want mounted (such as music) and right click and press mount. I think you can change the permissions too since you'll be using nautilus as root

here is what i get:
```

Initializing nautilus-share extension

** (nautilus:16313): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned
error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error 
No such file or directory
Please ask your system administrator to enable user sharing.
```

so can anyone help?

---

### Post by jerome1232 on 2008-08-21
Lets try it from the cli from fdisk sda2 was an ntfs partition so lets try that one. You can change /mnt/sda2 to whatever you want.

```
sudo mkdir /mnt/sda2
sudo mount -t ntfs-3g /dev/sda2 /mnt/sda2
sudo chown $USER:$USER /mnt/sda2
```

now try and navigate to it, go places>>computer>>filesystem>>mnt>>sda2>> you should now be in your drive.


edit: Seeing as this is a ntfs disk, and ntfs doesn't support permissions, I'm not sure if chowning it will do anything.

---

### Post by Ahmed Amr on 2008-08-21
thanks but it didnt work here is what i get
```

ahmed@ahmed-desktop:~$ sudo mount -t ntfs-3g /dev/sda2 /mnt/sda2
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /mnt/sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /mnt/sda2 ntfs-3g force 0 0

```

ps. i dont have windows any more and when i try the forced thats what i get
```
mount: only root can do that
```

---

### Post by jerome1232 on 2008-08-21
Try mounting it as read only, unmounting it and then remounting it

```
sudo mount -t ntfs-3g /dev/sda2 /mnt/sda2 -o ro
sudo umount /dev/sda2
sudo mount -t ntfs-3g /dev/sda2 /mnt/sda2
```

If that doesnt' work you might try ntfsfix

```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2
sudo mount -t ntfs-3g /dev/sda2 /mnt/sda2
```

btw when using mount, you have to run as root, by prepending the command with sudo, so if all of the above doesn't work try the force command with sudo

```
sudo mount -t ntfs-3g /dev/sda2 /mnt/sda2 -o force
```

---

### Post by Ahmed Amr on 2008-08-21
it has worked i dont know how but the forced mount worked :D
THANKS To all who participated and helped me
Loads of Thanks

---

