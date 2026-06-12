---
title: "Error 12: Invalid device request, can't boot into XP"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Support the 2nd on 2009-08-15
I can see and access my XP drive in my media folder.

So what happens when I try booting into into XP from the Grub or from the mobos boot selector, is Error 12: Invalid device request.

I just installed Ubuntu 9.04 on a drive with Ext3, and a FAT32 partion for my music.  XP was on a separate drive, ntfs.

**IMPORTANT INFO**
[I]About 2 years ago I was having problems getting both to work together, so I installed XP without my other drive, so the MBR would be there.  Then I unhooked it and had my kubuntu installed with grub.  I used my mobos boot option to have linux as the default boot and just used F11 if I needed to get into XP.  That was my work around.
[/I]

During this go round, I left the XP drive hooked up during the install.

So does XP still has the original MBR.  Is that affecting this?  What gives?

---

### Post by presence1960 on 2009-08-15
boot into Ubuntu and download the boot Info Script 0.32 from my signature line to the desktop. Once on desktop open a terminal and run this command
```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. paste the entire contents of that file back here. Once pasted here highlight all text and click # on the toolbar to place code tags around the text. This info will show us your setup & boot process. We can go from there.

---

### Post by Support the 2nd on 2009-08-15
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 104004810.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0edf0ede

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS
/dev/sda2         156,280,320   156,296,384        16,065   5 Extended
/dev/sda5         156,280,383   156,296,384        16,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x051e9de8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   104,004,809   104,004,747   5 Extended
/dev/sdb5                 126     1,992,059     1,991,934  82 Linux swap / Solaris
/dev/sdb6           1,992,123   104,004,809   102,012,687  83 Linux
/dev/sdb3         104,004,810   398,283,479   294,278,670   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0A9435B094359F5F" TYPE="ntfs" 
/dev/sdb3: LABEL="^?M-^\M-F>oM-,[M-_rM-^MM-<" UUID="47B1-1574" TYPE="vfat" 
/dev/sdb5: UUID="c03b433d-0fe8-4a98-87af-c999099bf053" TYPE="swap" 
/dev/sdb6: UUID="fd820df4-d03d-446e-8e0e-9f82105582b1" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /media/sda1 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb3 on /media/subway type vfat (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sdb6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fd820df4-d03d-446e-8e0e-9f82105582b1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fd820df4-d03d-446e-8e0e-9f82105582b1

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		fd820df4-d03d-446e-8e0e-9f82105582b1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fd820df4-d03d-446e-8e0e-9f82105582b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		fd820df4-d03d-446e-8e0e-9f82105582b1
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=fd820df4-d03d-446e-8e0e-9f82105582b1 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		fd820df4-d03d-446e-8e0e-9f82105582b1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fd820df4-d03d-446e-8e0e-9f82105582b1 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		fd820df4-d03d-446e-8e0e-9f82105582b1
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=fd820df4-d03d-446e-8e0e-9f82105582b1 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		fd820df4-d03d-446e-8e0e-9f82105582b1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sdb6 during installation
UUID=fd820df4-d03d-446e-8e0e-9f82105582b1  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sdb5 during installation
UUID=c03b433d-0fe8-4a98-87af-c999099bf053  none            swap         sw                          0  0  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,ro,umask=000  0  0  
/dev/sdb3                                  /media/subway   vfat         defaults                    0  0  

=================== sdb6: Location of files loaded by Grub: ===================


  50.1GB: boot/grub/menu.lst
  50.2GB: boot/grub/stage2
  50.1GB: boot/initrd.img-2.6.28-11-generic
  50.1GB: boot/initrd.img-2.6.28-14-generic
  50.1GB: boot/vmlinuz-2.6.28-11-generic
  50.2GB: boot/vmlinuz-2.6.28-14-generic
  50.1GB: initrd.img
  50.1GB: initrd.img.old
  50.2GB: vmlinuz
  50.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  aa aa aa aa aa aa aa aa  aa aa aa aa aa aa aa aa  |................|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by presence1960 on 2009-08-15
You no longer have the windows bootloader on sda (80 GB) as somehow you installed GRUB on MBR of both sda & sdb. This is what i would do. Boot your machine and go into BIOS. I would set sdb as first hard disk in boot order. Then continue booting and choose Ubuntu. Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
``` At the bottom of menu.lst change the windows entry to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

```

That should do it , reboot and try booting windows. 

If that does not work keep the menu.lst as it is. Boot again and switch the hard disk boot order back to sda as first boot. Then boot the windows XP install disk and do [this]("http://ubuntuforums.org/showthread.php?t=1014708") to restore the windows bootloader to MBR of sda. Reboot and you should boot right into windows. Then reboot one more time and switch the boot order back to sdb as first hard disk. You will be good to go now.

---

### Post by Support the 2nd on 2009-08-16
Thanks, that worked.

Can I still do that with the MBR just as a backup incase my other drive takes a dump [its getting years old] and I am left with just the XP drive?

But on a side note, that was my reason last time was because Grub got installed on both drives and ruined my XP MBR.  Don't know what I did wrong during install this time.  :(


One more thing, I have two kernals on my GRUB menu.....  2.6.28-14 and -11.

I can remove the -11 correct?  Any reason to leave it?

---

### Post by raymondh on 2009-08-16
> **Support the 2nd said:**
> 


One more thing, I have two kernals on my GRUB menu.....  2.6.28-14 and -11.

I can remove the -11 correct?  Any reason to leave it?

I keep at least 2 working kernels just in case one misfires.

If you prefer to just see one kernel in your boot up menu, you can install startupmanager and set parameters, defaults, etc there.  See attachments.

If you prefer to just have 1 kernel (at all), you can edit your menu.lst and either remove or comment the unwanted kernel.

---

### Post by presence1960 on 2009-08-16
> **Support the 2nd said:**
> Thanks, that worked.

Can I still do that with the MBR just as a backup incase my other drive takes a dump [its getting years old] and I am left with just the XP drive?

But on a side note, that was my reason last time was because Grub got installed on both drives and ruined my XP MBR.  Don't know what I did wrong during install this time.  :(


One more thing, I have two kernals on my GRUB menu.....  2.6.28-14 and -11.

I can remove the -11 correct?  Any reason to leave it?

You can restore windows bootloader to MBR of sda. just make sure you switch sda to first hard disk boot in BIOS, repair the MBR. reboot and make sure windows boots . if successful reboot again and switch sdb to first hard disk boot in BIOS. You will be good to go. or you can just wait until your other drive goes. Disconnect the bad drive, make sure the XP drive is set to first in BIOS( it should after removing other drive but check anyway) then use the windows CD to repair the MBR.

I agree with raymond- I would leave the two newest kernels in case one doesn't boot and you can't fix it. You can comment out in menu.lst the ones you don't want to show on your GRUB menu like this:
```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

[COLOR="Red"]#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		4056b016-d185-439d-b630-29449b4f5912
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		4056b016-d185-439d-b630-29449b4f5912
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=4056b016-d185-439d-b630-29449b4f5912 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic[/COLOR]

title		Ubuntu 9.04, memtest86+
uuid		4056b016-d185-439d-b630-29449b4f5912
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by presence1960 on 2009-08-16
> But on a side note, that was my reason last time was because Grub got installed on both drives and ruined my XP MBR. Don't know what I did wrong during install this time.

When you get to the ready to install window of the installer click the advanced tab and choose where you want GRUB installed, Examples:
sda = MBR of sda
sda1 = first sector of partition sda1 (useful for chainloading other distros from GRUB on MBR)

sdb = MBR of sdb
sdb1 = first sector of sdb1 (useful for chainloading other distros)

here is a screenshot of the ready to install window

---

### Post by petmoreno on 2010-02-24
Hello everybody,

I've a problem related to this issue. I have three S.O. (windows7, windowsXP and ubuntu 8.10). I'd like to access any of these from GRUB but I can't access to windowsXP getting the famous error12.

I leave the result.txt from boot info script. Can anybody help me?

Thanks in advance

Regards

**************************************************************************



   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/bcd

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x80d2f3ee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   246,886,919   246,886,857   7 HPFS/NTFS
/dev/sda2         246,886,920   467,411,174   220,524,255   f W95 Ext d (LBA)
/dev/sda5         246,886,983   359,550,764   112,663,782   7 HPFS/NTFS
/dev/sda6         359,550,828   423,023,579    63,472,752   7 HPFS/NTFS
/dev/sda7         423,023,643   466,640,054    43,616,412  83 Linux
/dev/sda8         466,640,118   467,411,174       771,057  82 Linux swap / Solaris
/dev/sda3         467,419,136   469,518,335     2,099,200   c W95 FAT32 (LBA)
/dev/sda4         469,518,704   488,397,167    18,878,464   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3A7AACD27AAC8C67                       ntfs                                     
/dev/sda3        3E21-FA72                              vfat       HP_TOOLS                      
/dev/sda4        3CD45BFDD45BB83A                       ntfs       HP_RECOVERY                   
/dev/sda5        01CA85B643171A10                       ntfs       DATA                          
/dev/sda6        C204FE4C04FE4349                       ntfs                                     
/dev/sda7        d4ca313a-5206-4eb9-b2ba-c566eb9d8140   ext3                                     
/dev/sda8        fe04cd8e-8d26-4ae2-a49f-987db0dbea5a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(7)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d4ca313a-5206-4eb9-b2ba-c566eb9d8140 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d4ca313a-5206-4eb9-b2ba-c566eb9d8140

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d4ca313a-5206-4eb9-b2ba-c566eb9d8140
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d4ca313a-5206-4eb9-b2ba-c566eb9d8140 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d4ca313a-5206-4eb9-b2ba-c566eb9d8140
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d4ca313a-5206-4eb9-b2ba-c566eb9d8140 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d4ca313a-5206-4eb9-b2ba-c566eb9d8140
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7 (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Windows XP (loader)
rootnoverify	(hd0,5)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista tools (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d4ca313a-5206-4eb9-b2ba-c566eb9d8140 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=fe04cd8e-8d26-4ae2-a49f-987db0dbea5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 235.3GB: boot/grub/menu.lst
 235.4GB: boot/grub/stage2
 235.4GB: boot/initrd.img-2.6.28-11-generic
 235.4GB: boot/initrd.img-2.6.28-18-generic
 235.4GB: boot/vmlinuz-2.6.28-11-generic
 235.4GB: boot/vmlinuz-2.6.28-18-generic
 235.4GB: initrd.img
 235.4GB: initrd.img.old
 235.4GB: vmlinuz
 235.4GB: vmlinuz.old

---

### Post by meierfra. on 2010-02-24
> I'd like to access any of these from GRUB
I'm assuming that  are you currently able  boot Windows XP via Window 7 Boot menu. If this is not correct,  let me know.

If you want to be able to boot XP directly from the Grub menu you need to:

[list=1]
[*]Move the XP boot files from the Win 7 partition to the XP partition
[*] Remove "makeactive" from the XP item in the Grub menu.
[*] Fix the boot sector of the XP partition.
[*] Clean up the XP boot menu.
[*] Set the timeout on the  Windows 7 boot menu to 0.
[/list]

Here are the details:

**Step 1 Move the XP boot files from the Win 7 partition to the XP partition**

```

cd /mnt
sudo mkdir 1 6
sudo mount /dev/sda1 1
sudo mount /dev/sda6 6
cd 1
sudo mv ntldr NTDETECT.COM boot.ini /mnt/6

```


**Step 2 Remove "makeactive" from the XP item in the Grub menu.**

```
 gksudo gedit /boot/grub/menu.lst
```

Change

title Windows XP (loader)
rootnoverify (hd0,5)
savedefault
makeactive
chainloader +1


to 

title Windows XP 
rootnoverify (hd0,5)
chainloader +1

Save the file.

**Step 3 Fix the boot sector of the XP partition.**

```
sudo apt-get install testdisk

```
(if apt-get cannot find "testdisk" you have to  enable the universe  repository via "System->Administration->Software Sources)
 
 ```
 sudo testdisk /dev/sda

```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the XP  partition  and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk.

[B]Step 4 Clean up the XP boot menu.
[/B]

```
sudo nano /mnt/6/boot.ini
```
(don't use gedit for "boot.ini", it doesn't handle dos line-breaks as well as nano)

Remove the line

multi(0)disk(0)rdisk(0)partition(7)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

Follow the instruction on the bottom  of the screen to save the file.( "^" means "Ctrl")


Before proceeding to step 5, reboot and see whether you can boot into XP using the "Window XP" entry on the Grub menu.

If this worked:

**Step 5 Set the timeout on the  Windows 7 boot menu to 0.**

Boot into Window 7. Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a command line as an administrator. (If this did not open the command line: Go to Start->Program Files->Accessories, Right Click "Command Prompt", Choose "Run as administrator")

```
bcdedit /set {bootmgr} timeout 0
```

Reboot and choose "Window 7" at the Grub menu. You should boot directly into Window 7 (without the Win 7 boot menu showing up)

---

### Post by petmoreno on 2010-02-25
Hi,
I'm sorry to tell you that I can access directly to my Windows7, but anyway I can access to my Windows XP.
Does this changes all steps I should follow? If not, I'll try to take all steps you mention and I'll give you a feedback

---

### Post by meierfra. on 2010-02-25
> Does this changes all steps I should follow?
Carry out Step1 to  Step 4, but you don't have to do step 5.

---

### Post by petmoreno on 2010-02-26
Hello,

I try to carry out the step 1, but when I can't set the following instruction ""sudo mv ntdlr NTDETEC.Com boot. ini /mnt/6"". I get the following error (It's something like that because I have the spanish version):

mv:can't make `stat' over <<ntldr>>:Doesn't exist file or directory
mv:can't make `stat' over <<NTDETECT.COM>>:Doesn't exist file or directory
mv:can't make `stat' over <<boot.>>:Doesn't exist file or directory
mv:can't make `stat' over <<ini.>>:Doesn't exist file or directory 

Any suggestion??

Thanks in advance and Regards

---

### Post by meierfra. on 2010-02-26
There was a typo in my instruction: it is supposed to be "boot.ini" (not " boot .ini". But that does not explain the missing "ntldr" and "NTDETECT.COM")

 I think that some of the earlier commands have gone  wrong. Please try Step 1 again and  post  the whole content of the terminal (use copy and paste)

---

### Post by petmoreno on 2010-02-26
I still have the same problem, that is:
mv:can't make `stat' over <<ntldr>> doesn't exist file or directory
mv:can't make `stat' over <<NTDETECT.COM>> doesn't exist file or directory
mv:can't make `stat' over <<boot.ini>> doesn't exist file or directory
What is happening??

---

### Post by meierfra. on 2010-02-26
> What is happening?? 
I don't know. Please  post  the content of the whole terminal, as I already asked you to do in my last post.

---

### Post by petmoreno on 2010-02-26
Hi,
I've got to take all steps, but when I choose Windows XP in the grub it appears a black screen. It seems to be hung.
What should I do??

---

### Post by meierfra. on 2010-02-26
Could you run the boot info script again and post the new RESULTS.txt (it might be called RESULTS1.txt)?

When  was last time your were able to boot XP?  
In which order did you install your operating systems?

---

### Post by petmoreno on 2010-02-27
Hi,

The last time I was able to boot XP was after reinstalling in my XP partition one more time. The order I installed my operating system was: 1st: Windows7, 2nd:Ubuntu, 3rd: WindowsXP

After that, I take all steps you post, I've to say that in step 4 I've found this line:

multi(0)disk(0)rdisk(0)partition(7)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

Instead of : multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

It was the only line there was in the archive, so I delete them.

I've run the boot scrip, and my results1.txt says that:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/bcd

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x80d2f3ee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   246,886,919   246,886,857   7 HPFS/NTFS
/dev/sda2         246,886,920   467,411,174   220,524,255   f W95 Ext d (LBA)
/dev/sda5         246,886,983   359,550,764   112,663,782   7 HPFS/NTFS
/dev/sda6         359,550,828   423,023,579    63,472,752   7 HPFS/NTFS
/dev/sda7         423,023,643   466,640,054    43,616,412  83 Linux
/dev/sda8         466,640,118   467,411,174       771,057  82 Linux swap / Solaris
/dev/sda3         467,419,136   469,518,335     2,099,200   c W95 FAT32 (LBA)
/dev/sda4         469,518,704   488,397,167    18,878,464   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3A7AACD27AAC8C67                       ntfs                                     
/dev/sda3        3E21-FA72                              vfat       HP_TOOLS                      
/dev/sda4        3CD45BFDD45BB83A                       ntfs       HP_RECOVERY                   
/dev/sda5        01CA85B643171A10                       ntfs       DATA                          
/dev/sda6        B0746E37746E0108                       ntfs                                     
/dev/sda7        d4ca313a-5206-4eb9-b2ba-c566eb9d8140   ext3                                     
/dev/sda8        fe04cd8e-8d26-4ae2-a49f-987db0dbea5a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda6/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS 
[operating systems] 
 

=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d4ca313a-5206-4eb9-b2ba-c566eb9d8140 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d4ca313a-5206-4eb9-b2ba-c566eb9d8140

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d4ca313a-5206-4eb9-b2ba-c566eb9d8140
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d4ca313a-5206-4eb9-b2ba-c566eb9d8140 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d4ca313a-5206-4eb9-b2ba-c566eb9d8140
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d4ca313a-5206-4eb9-b2ba-c566eb9d8140 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d4ca313a-5206-4eb9-b2ba-c566eb9d8140
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title        Windows XP 
rootnoverify    (hd0,5)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista tools (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d4ca313a-5206-4eb9-b2ba-c566eb9d8140 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=fe04cd8e-8d26-4ae2-a49f-987db0dbea5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 235.4GB: boot/grub/menu.lst
 235.4GB: boot/grub/stage2
 235.4GB: boot/initrd.img-2.6.28-11-generic
 235.4GB: boot/initrd.img-2.6.28-18-generic
 235.4GB: boot/vmlinuz-2.6.28-11-generic
 235.4GB: boot/vmlinuz-2.6.28-18-generic
 235.4GB: initrd.img
 235.4GB: initrd.img.old
 235.4GB: vmlinuz
 235.4GB: vmlinuz.old

---

### Post by meierfra. on 2010-02-27
> After that, I take all steps you post, I've to say that in step 4 I've found this line:

multi(0)disk(0)rdisk(0)partition(7)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

Instead of : multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

It was the only line there was in the archive, so I delete them.


I'm not exactly  sure what happened, but you are now missing a line in boot.ini. Edit boot.ini again:


```
sudo mount /dev/sda6 /mnt/6
sudo nano /mnt/6/boot.ini
```
and add  one line to boot.ini  so that  the whole file looks like


[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(5)[noparse]\WINDOWS[/noparse]
[operating systems]
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect


Everything else looks good.

---

### Post by petmoreno on 2010-02-27
Ey!
I've changed the boot.ini and I've fixed it!!!
Thanks a lot and regards

---

### Post by meierfra. on 2010-02-27
```
I've fixed it!!!
```
Great. Have fun with XP, Win 7 and Ubuntu.

---

