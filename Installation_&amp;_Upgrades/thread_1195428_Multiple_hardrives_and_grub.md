---
title: "Multiple hardrives and grub"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by Enforcer83 on 2009-06-23
I have been having an interesting issue for a while (approx. 6 mo) when I try to dual boot my system.  Now before I get into the problem, here is my configuration, including hard disk partitions.

```
CPU: AMD Athlon X2 4000+
MOBO: ASUS Crosshair w/ nVidia 590 North Bridge
MEM: 3 GB Corsair XMS2 DDR2 800
GPU: nVidia 8600 GTS
HDD: 80 GB SATA 2.0, 1 TB SATA 2.0, 500 GB SATA 2.0, 500 GB IDE
     120 GB External, 200 GB External
  DISK 0: 35 GB (Windows C Drive)
          45 GB (Windows Program Drive)
  DISK 1: 4 GB (Pagefile Drive)
          996 GB (Data)
  DISK 2: 40 GB unused (Ususally where I put Ubuntu)
          460 GB (Data)
```

The 500 GB IDE Drive is currently un-powered do to it being a storage drive for system backups.

DISK 0 & 1 are Western Digital, DISK 2 and the IDE are Seagate

Now for the problem.  When ever I install Ubuntu I configure it for the the drive I want it stored on (DISK 2) and attempt to install grub so it installs to DISK 0.  However, when I reboot I get a screen full of the word "GRUB"  Trying to repair the MBT to its previous configuration Using Super Grub Disk fails at which point, not knowing what else to do, I force a reformat of DISK 0 which repairs the MBT.  What am I doing wrong during the installation?

---

### Post by presence1960 on 2009-06-23
To get a more clear picture of your setup and boot info why don't you boot the Ubuntu Live CD and choose "Try Ubuntu without any changes". When the desktop loads go here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
and download to your desktop the Boot Info Script. Then open a terminal and run this command : ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on your desktop. paste the entire contents of that file back here. Once pasted highlight all text and click # on the toolbar to place code tags around the text.

---

### Post by Enforcer83 on 2009-06-24
Here you go.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a557382

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    73,407,599    73,407,537   7 HPFS/NTFS
/dev/sda2          73,407,600   156,295,439    82,887,840   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006f707

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     8,385,929     8,385,867   7 HPFS/NTFS
/dev/sdb2    *      8,385,930 1,953,520,064 1,945,134,135   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x837cfee7

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *     83,891,430   976,768,064   892,876,635   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C1926E0A8D8C1AB2" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="BBFACB280BEB2FDA" LABEL="PROGRAMS" TYPE="ntfs" 
/dev/sdb1: UUID="449D0FFAA5B28921" LABEL="PAGE FILE" TYPE="ntfs" 
/dev/sdb2: UUID="54B42690B42674A0" LABEL="DOCUMENTS2" TYPE="ntfs" 
/dev/sdc1: UUID="CCC28E811785EF0F" LABEL="DOCUMENTS4" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

Also at startup I got some sort of ACPI or ATPI Error.  It went a away before I could write it down.

---

### Post by presence1960 on 2009-06-24
> **Enforcer83 said:**
> Here you go.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0a557382

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    73,407,599    73,407,537   7 HPFS/NTFS
/dev/sda2          73,407,600   156,295,439    82,887,840   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006f707

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     8,385,929     8,385,867   7 HPFS/NTFS
/dev/sdb2    *      8,385,930 1,953,520,064 1,945,134,135   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x837cfee7

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *     83,891,430   976,768,064   892,876,635   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="C1926E0A8D8C1AB2" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="BBFACB280BEB2FDA" LABEL="PROGRAMS" TYPE="ntfs" 
/dev/sdb1: UUID="449D0FFAA5B28921" LABEL="PAGE FILE" TYPE="ntfs" 
/dev/sdb2: UUID="54B42690B42674A0" LABEL="DOCUMENTS2" TYPE="ntfs" 
/dev/sdc1: UUID="CCC28E811785EF0F" LABEL="DOCUMENTS4" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

Also at startup I got some sort of ACPI or ATPI Error.  It went a away before I could write it down.

Either one of two things happened: your install is really fouled up because it isn't showing in the sudo fdisk -l output, and GRUB is not installed. I think this is the least likely scenario because you have linux mountpoints listed. You mentioned your other drive is unplugged. That would account why there is no linux partition showing up in sudo fdisk -l, why GRUB is not reported as being installed and why you are missing a bunch of information from the script that should be there. Why don't you plug in the other drive and see if ubuntu installed to that one.

---

### Post by Enforcer83 on 2009-06-24
Maybe I should have specified earlier.  I usually install to the drive with only one partition however I did a full wipe of that drive about a month ago do to some errors I was getting in reading it within windows.  I will try to install tomorrow, Wed, when I get home from work.

---

### Post by presence1960 on 2009-06-24
> **Enforcer83 said:**
> Maybe I should have specified earlier.  I usually install to the drive with only one partition however I did a full wipe of that drive about a month ago do to some errors I was getting in reading it within windows.  I will try to install tomorrow, Wed, when I get home from work.

OK good luck.

---

### Post by Enforcer83 on 2009-06-26
Well I guess I don't have any problem.  Ubuntu and Grub are working fine.

Don't you just hate when something works the way it is suppose to when you are trying to find the cause of a problem?  :)

---

### Post by presence1960 on 2009-06-26
Good to hear that! How did you solve the problem?

---

### Post by Enforcer83 on 2009-06-26
Don't know just installed it selected the direct drive I wanted the boot loader to be installed to, sda in my case, instead of hd0 and rebooted.  I am not sure if maybe there was something about my system before hand that wasn't being recognized right or if the changes I made to my hardware configuration fixed the issue without me knowing it.  Without proof I don't wanted to voice my suspicions any further.  However, presence, if you want to discuss this more in depth feel free to IM me.

---

