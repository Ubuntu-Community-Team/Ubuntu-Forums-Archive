---
title: "how to mount HD"
date: 2010-02-01
forum: Hardware
---

### Post by CGZ1977 on 2010-02-01
My laptop crashed, apparently for some missing files on my Microsoft o/s. Upon recommendation of a friend who uses only Ubuntu (now i see why) I downloaded the9.10 iso Ubuntu files and have been looking on my laptop to try and access my HD to be able to extract all my files which were not completely backed up. My friend says I need to try and "mount" my hard drive to be able to access the info on my HD, but I do not know how to do it.

---

### Post by IcarusR on 2010-02-01
In a terminal run...

```
sudo fdisk -l
```

Workout which is windows drive/partition

Then in terminal run...

```
sudo mount -t vfat /dev/sd? /mount/point
```

sd? from disk
/mount/point folder to mount as
password asked for is normal user password
terminal Applications > Accessories > Terminal

---

### Post by SuperSonic4 on 2010-02-01
> **IcarusR said:**
> In a terminal run...

```
sudo fdisk -l
```

Workout which is windows drive/partition

Then in terminal run...

```
sudo mount -t vfat /dev/sd? /mount/point
```

sd? from disk
/mount/point folder to mount as
password asked for is normal user password
terminal Applications > Accessories > Terminal

Wouldn't a windows partition use ntfs rather than vfat now?

If it's an unclean mount you may have to fix the drive, you can do this most safely by booting into windows and then shutting down cleanly. If that does not work you may have to force mount the drive. **[COLOR="Red"]DO THIS AT YOUR OWN RISK[/COLOR]**, it's usually safe but not guaranteed.

```
sudo mount -t ntfs /dev/sd? /mount/point -o force
```

not too sure if it's -o or --o but the terminal output will tell you what to do



If it's specified in /etc/fstab (mounts drives on boot-the install may do this for you) then ```
sudo mount -a
``` might work

---

### Post by ajgreeny on 2010-02-01
If you can still boot into the windows install, and the ntfs partitions on disk are not locked, as if still in use, you should be able to simply use the nautilus file manager in the live CD (I'm assuming you have not yet installed ubuntu) and copy all your files to a usb disk of some sort.  In the left pane of nautilus there will be a list of places which may include Windows, or just Disk or something that you may recognise.  Just double click on that to mount and open it.  If you are having trouble booting windows try safe mode just so you can start it and then shutdown again.  This will release the "lock" on an ntfs partition that was not cleanly shutdown.

If you have already installed ubuntu in a dual boot with windows you should again be able to use nautilus file manager in the same way as above.

---

### Post by CGZ1977 on 2010-02-01
ok, answer to sudo fdisk -1 is:

fdisk invalid option - - '1'

Usage: fdisk [ -b SSZ] [ -u] DISK        Change partition table
             fdisk  -l [ -b SSZ] [ -u] DISK   List partition table ( s )
             fdisk  -s PARTITION                 Give partition size ( s ) in blocks
             fdisk  -v                                      Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and partition is something like /dev/hda7
-u: give Start and End in sector ( instead of cylinder ) units
-b 2048 : ( for certain MO disks ) use 2048-byte sectors


ANY IDEAS ANYONE????

THANKS

---

### Post by CGZ1977 on 2010-02-01
BOTH WITH sudo mount -t ntfs /dev/sd? /mount/point -o force AND --o IT GIVES ME: 

NTFS signature is missing.
Failed to mount '/dev/sda' : Invalid argument 
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a 
partition (e.g. /dev/sda, not /dev/sda1) Or the other way around?

---

### Post by CGZ1977 on 2010-02-01
WHEN I WRITE sudo mount -t vfat /dev/sd? /mount/point
IT GIVES ME: mount: mount point /mount/point does not exist

---

### Post by CGZ1977 on 2010-02-01
If i try to start the comp without the ubuntu cd in the drive it just won't let me, not in safe mode not in any way whatsoever. Is the live cd you are referring to the ubuntu one?

---

### Post by CGZ1977 on 2010-02-01
I WASN'T SURE WHETHER IT IS SUPPOSED TO BE sudo fdisk -1/-l SO I HAVE DONE THEM BOTH BELOW:

THE OUT PUT OF sudo fdisk -1 is: 

fdisk invalid option - - '1'

Usage: fdisk [ -b SSZ] [ -u] DISK Change partition table
fdisk -l [ -b SSZ] [ -u] DISK List partition table ( s )
fdisk -s PARTITION Give partition size ( s ) in blocks
fdisk -v Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and partition is something like /dev/hda7
-u: give Start and End in sector ( instead of cylinder ) units
-b 2048 : ( for certain MO disks ) use 2048-byte sectors


THE ANSWER TO sudo fdisk -l IS:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51478be6

      Device Boot        Start                   End               Blocks        Id   System
/dev/sda1                       1                1402        11261533+     12  Compaq diagnostics
/dev/sda2      *         1403             60367      473703424         7   HPFS/NTFS
/dev/sda3               60376             60802          3420160        12  Compaq diagnostics


ANY IDEAS WHAT THAT MEANS?

---

### Post by amsterdamharu on 2010-02-02
The easiest way to mount your drive is clicking on it in the file browser.
places -> ...GB file system

If that doesn't work you can try to see why by giving the following commands:


```

sudo su
mkdir /media/hd
mount -t ntfs /dev/sda2 /media/hd

```It might give you an error about windows not cleanly unmounting the drive so you have to force mount it.

```
mount -t ntfs /dev/sda2 /media/hd -o force
```

When you got it mounted could you post the boot.ini (assuming it's xp) and the error you get when you start up? It might have something todo with the boot.ini telling the startup process that windows is on the wrong partition so no wonder it's complaining about files missing.

---

### Post by pkm4o93 on 2010-02-02
Hi. Ive used Puppylinux for recovering files from broken windows installations many times. While ubuntu will do it, I needed speed.

---

### Post by CGZ1977 on 2010-02-02
Sorry for the capital letters, didn't mean to come across as shouting, it was purely to differentiate from the computer stuff. 

I worked it out, thanks for your help.

---

