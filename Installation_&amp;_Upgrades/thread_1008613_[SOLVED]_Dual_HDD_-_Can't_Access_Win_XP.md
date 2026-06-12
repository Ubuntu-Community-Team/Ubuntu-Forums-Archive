---
title: "[SOLVED] Dual HDD - Can't Access Win XP"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by Sierra_Dave on 2008-12-11
Hi,

I installed 8.10 on a machine with dual HDD [ Ubuntu on a sata 320gb and prexisting Win XP on 120GB IDE.  I want to access the windows hdd under "places" which lists it as "120gb media" but it will not mount the drive.  I need to change some drivers on the Win XP HDD to get it to launch with the new system/motherboard.

Thanks for your help!
Dave

---

### Post by taurus on 2008-12-11
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Sierra_Dave on 2008-12-11
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005af5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37684   302696698+  83  Linux
/dev/sda2           37685       38913     9871942+   5  Extended
/dev/sda5           37685       38913     9871911   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae706b65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS

---

### Post by Sierra_Dave on 2008-12-12
I now see that the XP drive was formatted NTFS, I thought it was fat32.  Can Ubuntu read NTFS if I loaded it as fat 32?:confused:

I found this in Wiki:
"Full and safe read/write of NTFS is provided by the NTFS-3G driver. It is included in most Linux distributions. Other outdated and mostly read-only solutions exist as well:

    * Linux kernel 2.2: NTFS partitions can be read by the kernel since version 2.2.0.
    * Linux kernel 2.6: contains a driver written by Anton Altaparmakov (University of Cambridge) and Richard Russon. It supports file read, overwrite and resize, in some cases.
    * NTFSMount: A userspace driver with limited file and directory read/write support is available using ntfsmount[23]
    * NTFS for Linux: A commercial driver with full read/write support available from Paragon.
    * Captive NTFS: A 'wrapping' driver which uses Windows' own driver, ntfs.sys.

Note that all three userspace drivers, namely NTFSMount, NTFS-3G and Captive NTFS, are built on the Filesystem in Userspace (FUSE), a Linux kernel module tasked with bridging userspace and kernel code to save and retrieve data. Almost all drivers listed above (except Paragon NTFS for Linux) are open source (GPL). Due to the complexity of internal NTFS structures, both the built-in 2.6.14 kernel driver and the FUSE drivers disallow changes to the volume that are considered unsafe, to avoid corruption."

Which, naturally, makes for more questions.  Are any of the open drivers listed in 8.10?  What's the airspeed of a swallow?  What's yer quest? Doh!

---

### Post by Partyboi2 on 2008-12-12
Ubuntu can read/write to ntfs and to fat32.

---

### Post by Sierra_Dave on 2008-12-13
I still cannot get this drive to mount, in order to read/write to it.  

Ubuntu sees the drive:

"Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae706b65

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 14593 117218241 7 HPFS/NTFS "

Any Ideas?

---

### Post by taurus on 2008-12-13
What happens when you run these commands from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by Sierra_Dave on 2008-12-14
Taurus,

I got this:

-desktop:~sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g force 0 0

........

 -desktop:~df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             285G  2.8G  267G   2% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  100K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.8M  1.7G   1% /dev
tmpfs                 1.7G  104K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-9-generic/volatile
......

 -desktop:~mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
mount: only root can do that

.........

When I used the boot menu to try to launch from the IDE HDD w/ Win xp, it ran the win boot loading sequence from the old system MB and then crashed and rebooted.  

[ I built this system w/ new MB/ram and old Sata HDD and old IDE HDD.  I have not been able to get old IDE to boot to Win XP since and I cant get new mb drivers installed on it.]

I also didn't get the option to partition the Sata on 8.10 despite trying several times on loading my live [checked] Ubuntu cd.

So  I guess I would like to change the root and force the mount of the IDE HDD.  Thanks for your help so far!
Dave

---

### Post by albinootje on 2008-12-14
Make this :
-desktop:~mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

into this :
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

and let us know whether that worked or not.

---

### Post by Sierra_Dave on 2008-12-14
Hey albinootje

I got this $LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

And the IDE mounted and is reading. 

Thanks
Dave

---

### Post by taurus on 2008-12-14
You can fix that with ntfsfix.  First, install ntfsprogs from a terminal and use ntfsfix to fix your ntfs partition, /dev/sdb1.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```
Now, you should be able to mount it with no problem.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```
Next time you use that drive in windows, make sure you go to the Safely Remove Hardware (little icon on the bottom right) to unmount it first before you unplug it.

---

### Post by Sierra_Dave on 2008-12-14
Thanks Taurus

---

