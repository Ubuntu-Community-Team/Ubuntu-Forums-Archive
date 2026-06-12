---
title: "Cannot boot Windows Vista via grub - I ran out of options..."
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by Bear Knuckle on 2009-08-31
Hi,

I installed an ubuntu after Windows Vista. The ubuntu is a raid installation, Vista is on a SATA drive.

First I checked fdisk -l to lookup my partitions:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6fdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648       60799   459073440    5  Extended
/dev/sda5            3648       59572   449217531   83  Linux
/dev/sda6           59573       60799     9855846   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6fdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3647    29294496   83  Linux
/dev/sdb2            3648       60799   459073440    5  Extended
/dev/sdb5            3648       59572   449217531   83  Linux
/dev/sdb6           59573       60799     9855846   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbf80c02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2        5099    40949685    f  W95 Ext'd (LBA)
/dev/sdc2            5100       38914   271607808    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdc5   *           2        5099    40949653+   7  HPFS/NTFS

```

So, my Vista is on /dev/sdc.

Then I checked /boot/grub/device.map:

```
(fd0)	/dev/fd0
(hd0)	/dev/mapper/jmicron_GRAID
(hd2)	/dev/sdc

```

The Vista hdd is mapped on hd2.

Then I tried this configuration in /boot/grub/menu.lst:

```
title           Windows Vista (loader)
rootnoverify    (hd2,x)
savedefault
makeactive
chainloader     +1

```

I replaced the 'x' with several numbers to check the result:

0: Error 21 Selected disk does not exist
1: Error 21 Selected disk does not exist
2: Error 21 Selected disk does not exist
3: Error 21 Selected disk does not exist
4: Error 12 Invalid device requested
5: Error 21 Invalid device requested

Then I tried some mapping to see, if I need to perform a virtual swap:

```
title           Windows Vista (loader)
map             (hd0) (hd2)
map             (hd2) (hd0)
rootnoverify    (hd2,x)
savedefault
makeactive
chainloader     +1

```

'x' replaced by the numbers above, which did not change any of the messages (Error 12 + Error 21).

I am totally out of options now.

What else can I do to boot the Vista partition?

---

### Post by stlsaint on 2009-08-31
i will try my best(presence) go here...[BootInfoScript]("sudo bash ~/Desktop/boot_info_script*.sh") and download the script to your destop and run this in terminal...

sudo bash ~/Desktop/boot_info_script*.sh

it will put a RESULTS.txt on your desktop...post that txt here so we can see your setup fully.

EDIT: made a mistake...here is the correct link...[BootInfoScript ]("http://sourceforge.net/projects/bootinfoscript/")
i also posted it again in the post right below this one. sorry for mishap

---

### Post by stlsaint on 2009-08-31
sorry [BootInfoScript]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by stlsaint on 2009-08-31
reading some more im curious whats your bios set to boot to?

---

### Post by Bear Knuckle on 2009-09-01
> **stlsaint said:**
> reading some more im curious whats your bios set to boot to?

Hi,

thank you for your help. I am at work right now, but I will look up my bios when I'm back home.

IIRC the bios is set to boot from CD-ROM, then hdd. The hdds are set to boot the raid first and the samsung (the Vista drive) secondly.

I think this is correct. The Vista drive is configured as primary master in bios, while the linux drives are a mirrored raid at the "It't no real hardware raid"-raid in my bios (I never got that raid stuff clearly, I have to admit).

Ok, nevertheless I can only be sure about my bios settings, if I checked them. Then I will also run the script mentioned by you.

One thing I see now is, I guess - because of the smaller size - the Vista system partition is /dev/sdc5, which is flagged as bootable but also, if I read the /dev/sdc1 entry correctly, is in an extended partition. I think I read, windows can not boot from an extended partition, but Vista ist booting, if I switch the boot order of the hdds in bios.

Let's check all this later. :-)

---

### Post by Bear Knuckle on 2009-09-01
Here is the output of the bootinfoscript:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e6fdf

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,589,054    58,588,992  83 Linux
/dev/sda2          58,589,055   976,735,934   918,146,880   5 Extended
/dev/sda5          58,589,118   957,024,179   898,435,062  83 Linux
/dev/sda6         957,024,243   976,735,934    19,711,692  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e6fdf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    58,589,054    58,588,992  83 Linux
/dev/sdb2          58,589,055   976,735,934   918,146,880   5 Extended
/dev/sdb5          58,589,118   957,024,179   898,435,062  83 Linux
/dev/sdb6         957,024,243   976,735,934    19,711,692  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbbf80c02

Partition  Boot         Start           End          Size  Id System

/dev/sdc1              16,065    81,915,434    81,899,370   f W95 Ext d (LBA)
/dev/sdc5    *         16,128    81,915,434    81,899,307   7 HPFS/NTFS
/dev/sdc2          81,922,048   625,137,663   543,215,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sdc2: UUID="EC3454993454689A" LABEL="Daten" TYPE="ntfs" 
/dev/sdc5: UUID="C6080BD4080BC283" TYPE="ntfs" 
/dev/mapper/jmicron_GRAID1: UUID="0e6f901b-9134-4503-97b1-bee4c474df37" TYPE="ext4" 
/dev/mapper/jmicron_GRAID5: UUID="18402771-1f57-4fb2-b380-970f4b2f1e1f" TYPE="ext3" 
/dev/mapper/jmicron_GRAID6: TYPE="swap" UUID="1a08a52b-914b-4e03-811e-8d3ec5dd8ec6" 

=============================== "mount" output: ===============================

/dev/mapper/jmicron_GRAID1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/mapper/jmicron_GRAID5 on /home type ext3 (rw,relatime)
/dev/sdc2 on /windows_daten type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc5 on /windows_system type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wallace/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wallace)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb5


Unknown BootLoader  on sdb6



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb6: No such file or directory
hexdump: /dev/sdb6: No such file or directory
```

So, if you ask me, the problem is, /dev/sdc2 is where the Vista bootloader is located, but the bootflag is set to /dev/sdc5.

Let me try to set the bootflag to /dev/sdc2.

What do you think?

**edit:** Nope, setting the bootflag to /dev/sdc2 didn't change anything. Still Error 12.

---

### Post by Bear Knuckle on 2009-09-03
Found the solution:

In [this german article]("http://wiki.ubuntuusers.de/GRUB#Error-nach-dem-GRUB-Bootmenue") I found the counting hint. 

In a Raid 0 configuration (Did I mention this?) the both HDDs configured as Raid 0 are recognized as one.

Even though fdisk shows
```
/dev/sdc
```
and the device.map is
```
(hd2)	/dev/sdc
```
the correct entry in menu.lst is
```
title           Windows Vista (loader)
rootnoverify    (hd1,1)
savedefault
makeactive
chainloader     +1
```

Pay attention to the fact, that /dev/sdc is mapped to (hd2), but the entry uses (hd1) as boot point!

This is something, someone should keep in mind while configuring grub in the context of a Raid 0 configuration.

---

