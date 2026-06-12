---
title: "External Hard Drive not mounting?"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by nickb827 on 2007-11-16
I am new to Ubuntu, so this might be an easy problem to fix, but my external hard drive won't mount. When I try to mount it, I get an error that says "Cannot mount Volume" Then under that it says "Unable to mount the volume 'EXT HDD'". An attached pic shows what it says then. I tried to force mount it, but it gives me "ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb5 /media/EXT HDD -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount ."
What should I do? If I have to format, can I do it in a way so that I can recover my data? 
Thanks in advance!

---

### Post by taurus on 2007-11-16
> **nickb827 said:**
> I am new to Ubuntu, so this might be an easy problem to fix, but my external hard drive won't mount. When I try to mount it, I get an error that says "Cannot mount Volume" Then under that it says "Unable to mount the volume 'EXT HDD'". An attached pic shows what it says then. I tried to force mount it, but it gives me "ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sdb5 /media/**[COLOR="Blue"]EXT HDD[/COLOR]** -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount ."
What should I do? If I have to format, can I do it in a way so that I can recover my data? 
Thanks in advance!

Your problem is the empty space in your mount point.  Try

```
sudo mount -t ntfs-3g /dev/sdb5 /media/"EXT HDD" -o force
```

---

### Post by nickb827 on 2007-11-17
I would try this, but I cant get the applications menu to open. I have more specifics on the problem at [http://ubuntuforums.org/showthread.php?p=3786460](http://ubuntuforums.org/showthread.php?p=3786460).

---

### Post by taurus on 2007-11-17
If you need to open a terminal, try <Alt>F2 and then type in

```
gnome-terminal
```

---

### Post by nickb827 on 2007-11-17
Ok, thanks for that tip taurus. However, when I type in what you said earlier, it tells me "Failed to access '/dev/sdb5': No such file or directory" . What should I do now?

---

### Post by taurus on 2007-11-17
Can you post the output of this command from a terminal?

```
sudo fdisk -l <-- lower case letter l, not number 1
```

p.s.  Or try /dev/sdc5.

```
sudo mount -t ntfs-3g /dev/sdc5 /media/"EXT HDD" -o force
```

---

### Post by nickb827 on 2007-11-17
When I type in sudo fdisk -l i get:
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb213b213

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19928   160071628+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1da011b9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4661    37439451   83  Linux
/dev/hdb2            4662        4866     1646662+   5  Extended
/dev/hdb5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59a6f999

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       30401   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 2032 MB, 2032664576 bytes
63 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
When I try sudo mount -t ntfs-3g /dev/sdc5 /media/"EXT HDD" -o force , I get:
Failed to access '/dev/sdc5': No such file or directory.

---

### Post by taurus on 2007-11-17
> **nickb827 said:**
> 

Disk /dev/sdc: 2032 MB, 2032664576 bytes
63 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000


Looks like there is no filesystem for your external harddrive!  Boot into windows and see if you can access or write anything to that drive.

---

### Post by nickb827 on 2007-11-17
When I am in windows, it doesn't even show up. Windows restarted when I was defragging the hard drive and then I couldn't access it.

---

### Post by taurus on 2007-11-17
If you don't have gparted on Ubuntu, install it.

```
sudo apt-get update
sudo apt-get install gparted
```
Then, fire up gparted, System -> Administration, and see if gparted even detect it.  If it does, use it to create a partition, /dev/sdc1 (or whatevever gparted decides to call), and format it.

---

### Post by nickb827 on 2007-11-17
Ok, I installed gparted and formatted it to FAT32. Its not showing up under "computer" though. On gparted it says that its /dev/sda .What should I do now?

---

### Post by taurus on 2007-11-17
Can you post the output of this command again?

```
sudo fdisk -l
```

---

### Post by nickb827 on 2007-11-17
Sure, its:

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb213b213

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19928   160071628+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1da011b9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4661    37439451   83  Linux
/dev/hdb2            4662        4866     1646662+   5  Extended
/dev/hdb5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59a6f999

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       30401   244187968+   b  W95 FAT32

Disk /dev/sdc: 2032 MB, 2032664576 bytes
63 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

---

### Post by taurus on 2007-11-17
> **nickb827 said:**
> Sure, its:

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb213b213

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19928   160071628+   7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1da011b9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4661    37439451   83  Linux
/dev/hdb2            4662        4866     1646662+   5  Extended
/dev/hdb5            4662        4866     1646631   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59a6f999

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       30401   244187968+   b  W95 FAT32

Disk /dev/sdc: 2032 MB, 2032664576 bytes
63 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Okay, which harddrive are we talking here?  Are we talking about /dev/sda (/dev/sda5) or /dev/sdc because /dev/sda5 used to be ntfs and you just formatted it to vfat32 with gparted while /dev/sdc is still as dead as a nail.

---

### Post by nickb827 on 2007-11-17
I dont know. I am talking about the same one that I have been talking about for the entire time. I just took a screenshot of gparted with it on the External Hard Drive for you. Thank you so much for your help, I don't know what I would have done with out you. Sorry I can't help you more though.

---

### Post by taurus on 2007-11-17
Okay, so you want to mount /dev/sda5.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda5   /media/sda5   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then, create the new mount point and mount it.

```
sudo mkdir /media/sda5 <-- If you get a message saying that /media/sda5 already exists, just move on to the next command.
sudo mount -a
df -h <-- You should see your /dev/sda5 mounted to /media/sda5.
```

---

### Post by nickb827 on 2007-11-17
Ok, I followed your steps and I am not sure if it mounted correctly. It says:
bob@bob-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              36G  3.5G   30G  11% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  104K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1             153G  103G   50G  68% /media/C:
/dev/sda5             233G   16K  233G   1% /media/sda5
Is that supposed to show up?

---

### Post by taurus on 2007-11-17
> **nickb827 said:**
> Ok, I followed your steps and I am not sure if it mounted correctly. It says:
bob@bob-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              36G  3.5G   30G  11% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  104K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1             153G  103G   50G  68% /media/C:
**[COLOR="Blue"]/dev/sda5             233G   16K  233G   1% /media/sda5[/COLOR]**
Is that supposed to show up?

Yip.  it's mounted to /media/sda5, 233GB of it.

---

### Post by nickb827 on 2007-11-17
Ok, thanks! Your the (wo?)Man!

---

