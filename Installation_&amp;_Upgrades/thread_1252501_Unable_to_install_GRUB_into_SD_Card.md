---
title: "Unable to install GRUB into SD Card"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by darthnerd on 2009-08-28
Dear all, 
I am facing the problem of installing GRUB into SD Card that is placed in the Build-in slot. Here is my setup:
Lenovo x61
Win XP Pro OS and recovery OS in one same harddisk.
16 GB SD Card(That contains GRUB and ubuntu OS)

When I select sda, another different partition that belongs to my SD card or any other partitions.. i would still get this error

[IMG]http://i27.tinypic.com/nwg11z.png[/IMG]

(I took it from this forum before i knew there was a screenshot function:KS..)

Here is my partition table setup..
[IMG]http://i30.tinypic.com/2l3twn.png[/IMG]

I have the few questions on this setup:
1) Do I have to setup GRUB on the harddisk's MBR instead of the SD card.
2) why i can't install GRUB on any other partition during the setup using "advance" button?

I have been trying to setup a dual boot with ubuntu and win xp for few days but i have no luck.. I hope you guys would point me to the right direction.

Thanks:)

Regards,
DN

---

### Post by darthnerd on 2009-08-29
Dear all,

Using meierfra's boot info script..
Here are the results..
> 
============================= Boot Info Summary: ==============================

 => ThinkPad is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /NTLDR 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /NTDETECT.COM /ntdetect.com

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   303,095,519   303,095,457   7 HPFS/NTFS
/dev/sda2         303,095,520   312,575,759     9,480,240  12 Compaq diagnostics


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            249     3,967,487     3,967,239   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B268290C6828D0C1" LABEL="Preload" TYPE="ntfs" 
/dev/sda2: LABEL="SERVICEV001" UUID="C4DF-3C17" TYPE="vfat" 
/dev/sdb1: SEC_TYPE="msdos" UUID="78D6-0552" TYPE="vfat" 
/dev/mmcblk0p1: UUID="44e0778c-7005-4e23-b44f-f28b4cc4689c" TYPE="ext3" 
/dev/mmcblk0p5: TYPE="swap" UUID="3165dae1-149a-4b62-a2a5-3d6b6e3546db" 
/dev/mmcblk0p6: UUID="663585c0-e6f3-41ae-a4c9-d43a31daca78" TYPE="ext3" 

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
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/mmcblk0p6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/mmcblk0p1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect Hope this information is useful for you all.:)

Thanks.

DN

---

### Post by darthnerd on 2009-08-29
I have been looking at tutorial like [this]("http://www.ubuntu.bsd.md/?q=node/2") but i am STILL unable to install grub manually to the /boot partition... ](*,)

I have been thinking of using boot.ini or using GRUB to overwrite MBR which i can't do both of them..

i hope that someone would point me to the right direction....:frown:

I just want to install ubuntu into the SD card as a second harddrive and have a dual boot... and it seems so hard to do it......:confused:

---

### Post by darthnerd on 2009-08-29
Dear all,

I have found [this]("http://neosmart.net/blog/2007/how-to-install-the-vista-bootloader-on-a-windows-xp-machine/") to edit the boot.ini but i am still having problems with GRUB.. still now it seems that i can't get it install..

I really hope that some one really gives me some comments..:frown:

Thanks

---

### Post by darthnerd on 2009-08-29
Dear all,

I tried the following commands but it still does not work.
> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/mmcblk0p1
/dev/mmcblk0p1 does not have any corresponding BIOS drive.
ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/mmcblk0
Probing devices to guess BIOS drives. This may take a long time.
/dev/mmcblk0 does not have any corresponding BIOS drive.and here is the sudo fdisk -l
> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20046   151547728+   7  HPFS/NTFS
/dev/sda2           20047       20673     4740120   12  Compaq diagnostics

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         984     1983619+   6  FAT16

Disk /dev/mmcblk0: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004cb83

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1          12       96358+  83  Linux
/dev/mmcblk0p2              13        1936    15454530    5  Extended
/dev/mmcblk0p5              13         498     3903763+  82  Linux swap / Solaris
/dev/mmcblk0p6             499        1936    11550703+  83  Linux
ubuntu@ubuntu:~$ can someone can give me any comments on this.. Been trying past 5 days to install ubuntu into SD card and having dualboot function... but i am not successful with it..:confused:

---

### Post by darthnerd on 2009-08-29
Dear all,

Is it me who is new to ubuntu or what i am trying to do is impossible?? Installing Ubuntu into a SD card that is placed into the Built-in Slot(acting as a thumbdrive but unable to boot from BIOS) and having a dual boot capabilities...

Hope to get answer on this question from you all..

Thanks

---

### Post by presence1960 on 2009-08-29
> **darthnerd said:**
> Dear all,

Is it me who is new to ubuntu or what i am trying to do is impossible?? Installing Ubuntu into a SD card that is placed into the Built-in Slot(acting as a thumbdrive but unable to boot from BIOS) and having a dual boot capabilities...

Hope to get answer on this question from you all..

Thanks
If your Sd card is unable to boot from BIOS then you can not install an OS there. Your BIOS must support booting from whatever medium you are trying to run an OS or a bootable disk from.

Another problem is your device name for that SD card. here is my 2 Gb Sd card in my fdisk output:
```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85858585

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2350    18876343+  83  Linux
/dev/sda2   *        2351        8877    52427776    7  HPFS/NTFS
/dev/sda3            8878        9399     4192965    5  Extended
/dev/sda5            8878        9399     4192933+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d562f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48301   387977751   83  Linux
/dev/sdb3           48302       60801   100406250    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       17107   137411946   83  Linux
/dev/sdc2           17108       19457    18876375   83  Linux

[COLOR="Red"]Disk /dev/sdd: 1967 MB, 1967128576 bytes
40 heads, 56 sectors/track, 1715 cylinders
Units = cylinders of 2240 * 512 = 1146880 bytes
Disk identifier: 0x000bad43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1716     1921023+   6  FAT16[/COLOR]
raz@raz-desktop:~$ 
```

something is amiss there, your system is not naming the device in order like the other media on your system. Did you try formatting the SD card and starting over. I would format it and create partitions prior to the installation.

**_But are you positive your machine can boot from an SD card?_**

---

### Post by darthnerd on 2009-08-29
hi [presence1960,]("http://ubuntuforums.org/member.php?u=657448")

Thanks alot for coming in here, really appreciate it..

currently my laptop can't boot off from the SD card but it can for a USB(Refer to [here]("http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/Boot-from-SD-card/m-p/5939") for more info)

Without having the feature to boot straight from the SD Card.. I have thought of 2 possible solutions...

1) Install GRUB on the harddisk or SD card and using GRUB to select the 2 different OS..
2) Install GRUB on the harddisk or SD card and using EasyBCD to edit boot.ini to select the 2 different OS..(I am looking at this)

But i have problem installing GRUB to the harddisk and the SD card... which you all can refer to [URL="http://ubuntuforums.org/showpost.php?p=7868241&postcount=5"]post 5
[/URL]
> something is amiss there, your system is not naming the device in order like the other media on your system. Did you try formatting the SD card and starting over. I would format it and create partitions prior to the installation.As for formatting.. I using the gpartition during the ubuntu installation that i booted off from the USB flash disk..

Any comments would be great!!

---

### Post by presence1960 on 2009-08-29
> Problem: The computer does not start from a device you want. Solution: See the Startup menu of the BIOS Setup Utility. Make sure that the startup sequence in the BIOS Setup Utility is set so that the computer starts from the device you want. Also make sure that the device from which the computer starts is enabled. In the startup menu in the BIOS Setup Utility, make sure that the device is included in the &#8243;Boot priority order&#8243; list. If it is included in the &#8243;Excluded from boot order&#8243; list, it is disabled. Select the entry for it in the list and press the x key. This moves the entry to the &#8243;Boot priority order&#8243; list.

This is from the documentation for your machine from the Lenovo web site. You must be able to set that SD card to boot. if you can not your machine will not be able to boot an OS or a boootable SD such as gparted Live Cd, Ubuntu Live Cd from an SD card.

---

### Post by presence1960 on 2009-08-29
> **darthnerd said:**
> hi [presence1960,]("http://ubuntuforums.org/member.php?u=657448")

Thanks alot for coming in here, really appreciate it..

currently my laptop can't boot off from the SD card but it can for a USB(Refer to [here]("http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/Boot-from-SD-card/m-p/5939") for more info)

Without having the feature to boot straight from the SD Card.. I have thought of 2 possible solutions...

1) Install GRUB on the harddisk or SD card and using GRUB to select the 2 different OS..
2) Install GRUB on the harddisk or SD card and using EasyBCD to edit boot.ini to select the 2 different OS..(I am looking at this)

But i have problem installing GRUB to the harddisk and the SD card... which you all can refer to [URL="http://ubuntuforums.org/showpost.php?p=7868241&postcount=5"]post 5
[/URL]
As for formatting.. I using the gpartition during the ubuntu installation that i booted off from the USB flash disk..

Any comments would be great!!
You can try all that, but wouldn't it be easier and a sure bet to put Ubuntu onto an USB flash drive? You know for sure that will work.

My PC boots from SD cards as I have gparted Live and Linux Backtrack on SD cards.

---

### Post by darthnerd on 2009-08-29
> **presence1960 said:**
> This is from the documentation for your machine from the Lenovo web site. You must be able to set that SD card to boot. if you can not your machine will not be able to boot an OS or a boootable SD such as gparted Live Cd, Ubuntu Live Cd from an SD card.

Thanks for the tip but i have shifted up the devices in excluded list to the enabled list.. But it's the same..

---

### Post by darthnerd on 2009-08-29
> **presence1960 said:**
> You can try all that, but wouldn't it be easier and a sure bet to put Ubuntu onto an USB flash drive? You know for sure that will work.

My PC boots from SD cards as I have gparted Live and Linux Backtrack on SD cards.

I have tried doing those but i can't get GRUB to be installed manually.. 

I believed that ubuntu can be booted off from the SD card with the help of the bootloader..
:P

as from using USB.. i prefer not too.. if i want to do it, i would prefer using the LIVE CD on USB..

once again, thanks for your comments

---

### Post by presence1960 on 2009-08-29
> **darthnerd said:**
> Thanks for the tip but i have shifted up the devices in excluded list to the enabled list.. But it's the same..

According to the thread from the Lenovo support forum you linked to your model is not capable of booting from an SD card. So no matter where you install GRUB it must still point to the files on your SD card necessary to boot Ubuntu. Unfortunately that will not work because your machine does not support booting from an SD card. All GRUB does is point to or hand off to the files necessary to boot an OS. In your case those files reside on a disk that cannot boot from your machine. Get a USB flash drive or an external hard disk to put Ubuntu on if you don't want it on the internal disk

---

### Post by presence1960 on 2009-08-29
[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)

this should help you understand why you can't boot from that SD card even if you put GRUB or any other bootloader on a different disk.

---

### Post by darthnerd on 2009-08-30
mmm.. after reading it... The bottom line is that as long BIOS does not detect the 16GB SD Card Built-in reader no way that can be booted off because of the reason showed below.
> 
Once the BIOS has found a bootable device it loads the [boot sector]("http://en.wikipedia.org/wiki/Boot_sector") to hexadecimal [Segment]("http://en.wikipedia.org/wiki/X86_memory_segmentation"):[Offset]("http://en.wikipedia.org/wiki/Offset_%28computer_science%29") address 0000:7C00 or 07C0:0000 (maps to the same ultimate address) and transfers execution to the [boot code]("http://en.wikipedia.org/wiki/Boot_sector"). In the case of a hard disk, this is referred to as the [master boot record]("http://en.wikipedia.org/wiki/Master_boot_record") (*MBR*) and is often not operating system specific. The conventional MBR code checks the MBR's [partition table]("http://en.wikipedia.org/wiki/Partition_table") for a partition set as *bootable* (the one with *active* flag set)[[12]]("http://en.wikipedia.org/wiki/Booting#cite_note-11"). If an active partition is found, the MBR code loads the [boot sector]("http://en.wikipedia.org/wiki/Boot_sector") code from that partition and executes it. The boot sector is often operating system specific, however in most operating systems its main function is to load and execute the operating system [kernel]("http://en.wikipedia.org/wiki/Kernel_%28computer_science%29"), which continues startup.

It seems that the only solution is that lenovo updates x61's BIOS to allow boot feature for the built-in card reader..

I decided to create another partition for ubuntu on the same harddisk that win xp pro is installed. However i worry that the recovery OS might be affected.. so i have to get the recovery CD ready if anything happen... :)  

presence1960, I really appreciate your time and help on this. Thanks alot!!

---

### Post by presence1960 on 2009-08-30
You are welcome, unfortunately we couldn't help you do what you wanted to do. But that is a BIOS/hardware issue beyond our control.

---

### Post by darthnerd on 2009-08-30
Dear all, 

Now I am installing ubuntu using wubi installer. It can detect my 16GB SD Card and chose to install it here(it is a FAT partition) 

For now this is the better workaround than  installing it into the same drive if you do not wish to risk losing your information. However, i understand the speed is not as "fast" as a clean installation and it is recommend to do it.
EDITED: I got stuck at "creating the virtual disk" because 1 created the FAT partition instead of NTFS..  any install is more than 4GB.., the partition has to be NTFS.

For now, I would just give any updates on this.

Thanks! :)

---

### Post by darthnerd on 2009-08-30
Dear all,

it is still the same problem that i have encountered earlier on. It requires the built-in SD carder to be bootable in order to work.

Now i am just installing into the same hard drive using wubi.

Thanks.

---

