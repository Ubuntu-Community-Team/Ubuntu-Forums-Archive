---
title: "Installed on new partition but not vista boot option at reboot"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by notuo on 2009-04-29
Hi all.
I am brand new here but many years in computing (burroughs machines and PC) Never unix/linux

Today I decided to try ubuntu (as per references) and made a new partition on my disk. I installed and seems to go OK but when Boot loader screen appeared, I have no way to verify (there is no help in the process)  and deselect the option. I think this can overwrite my windows boot configuration.  

I am sure this was the problem beccause when I reboot, no OS choice appeared and booted directly to windows.

I want to mantain my vista boot manager and have ubuntu as a choice. I understand I maybe to reinstall it again, but:

1) Any help on this is appreciated
2) Somebody can explain (or direct to any documentation) where boot loader options / configuration is?

Thanks in advance,
Notuo

---

### Post by fdrake on 2009-04-29
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

in the partition section you choose to resize your old partion(vista) to leave some free space, then you select the free space to install ubuntu keeping your vista partition

---

### Post by fornix on 2009-04-29
Do you mean to say, during installation when it asked you to install grub to your MBR, you declined?
And now grub is not installed and it straight away takes you to windows?

---

### Post by Sef on 2009-04-30
>  I want to mantain my vista boot manager and have ubuntu as a choice. I understand I maybe to reinstall it again, but:What is your reason for keeping the Vista bootloader?   Windows bootloaders can only see Windows oses.  If you want to have grub boot into Windows as the default option, then that is possible.

Thead on making [Windows boot first]("http://ubuntuforums.org/showthread.php?t=1143218").

---

### Post by notuo on 2009-04-30
Hi.  Lets go one by one... but first, thank you all for your help

sef:  Ok, let me read and try later today... I'll be back.  My only question is this. What IF I decide to remove ubuntu. What about the windows boot loader?  Is there a procedure to do this?

Fornix:  Do you mean in this part?, yes, I declined to do this. I saw /hd0 and freaked that something can mess with my vista boot. See this picture:
[IMG]http://news.softpedia.com/images/extra/LINUX/small/ubuntu804installationguide-small_009.png[/IMG]

fdrake: I am taking a look at that page now.

Regards,

---

### Post by Sef on 2009-04-30
> sef: Ok, let me read and try later today... I'll be back. My only question is this. What IF I decide to remove ubuntu. What about the windows boot loader? Is there a procedure to do this?

Yes, but I will have to find it.   You have to do fixmbr or something like that.

As for booting without grub, look at [EasyBCD]("http://neosmart.net/dl.php?id=1").

---

### Post by caljohnsmith on 2009-04-30
Notuo, I think it would help to first get a clearer picture of your setup related to booting so we can give recommendations tailored to your particular setup and needs. If that sounds good to you, how about downloading the **Boot Info Script** to your Ubuntu desktop (can be the Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup so we can best help you. 

Cheers,
John

---

### Post by notuo on 2009-05-01
Hi again.

As per sef recommendation, I went to EasyBCD and also I found this page:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

I followed those instructions and now I have my vista in control of the boot and I have the chance to boot to ubuntu as well. Now I am answering this from ubuntu. :P

Now from caljohnsmith, Here is my results to share. 
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024    21,100,543    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,100,592   125,949,599   104,849,008   7 HPFS/NTFS
/dev/sda4         125,949,724   234,438,655   108,488,932   5 Extended
/dev/sda5         166,272,813   229,183,289    62,910,477   7 HPFS/NTFS
/dev/sda6         229,197,824   234,438,655     5,240,832  dd 
/dev/sda7         125,949,726   166,272,749    40,323,024  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c9f81ae

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         16,065   625,137,344   625,121,280   5 Extended
/dev/sdb5              16,128   209,728,574   209,712,447   7 HPFS/NTFS
/dev/sdb6         209,728,638   419,457,149   209,728,512   7 HPFS/NTFS
/dev/sdb7         419,457,213   625,137,344   205,680,132   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-081F" TYPE="vfat" 
/dev/sda2: UUID="64C2C3EFC2C3C390" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="A2EE4D46EE4D13C7" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="1007423112D331AC" LABEL="sw" TYPE="ntfs" 
/dev/sda6: LABEL="MEDIADIRECT" UUID="CCCB-9587" TYPE="vfat" 
/dev/sda7: UUID="ececa544-896b-480f-9d53-2e406da3f2fe" TYPE="ext3" 
/dev/sdb5: UUID="53CA3E8692858700" LABEL="IMS" TYPE="ntfs" 
/dev/sdb6: UUID="4A4BB6FBB618044E" LABEL="AOM" TYPE="ntfs" 
/dev/sdb7: UUID="8861DDE00E798C27" LABEL="Othersville" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/angel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=angel)
/dev/sdb7 on /media/Othersville type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda2 on /media/RECOVERY type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


============================== sda3/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD 
 
## ## End Default Options ## 
 
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic 
root        (hd0,6) 
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro quiet splash 
initrd        /boot/initrd.img-2.6.24-23-generic 
quiet 
 
title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode) 
root        (hd0,6) 
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro single 
initrd        /boot/initrd.img-2.6.24-23-generic 
 
title        Ubuntu 8.04.2, kernel 2.6.24-16-generic 
root        (hd0,6) 
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-generic 
quiet 
 
title        Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode) 
root        (hd0,6) 
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro single 
initrd        /boot/initrd.img-2.6.24-16-generic 
 
title        Ubuntu 8.04.2, memtest86+ 
root        (hd0,6) 
kernel        /boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST
================================ sda6/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 /usepmtimer 

================================ sda6/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 /usepmtimer 

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
# kopt=root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, kernel 2.6.24-16-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=ececa544-896b-480f-9d53-2e406da3f2fe ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,6)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title        Microsoft Windows XP Embedded
root        (hd0,5)
savedefault
makeactive
chainloader    +1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=ececa544-896b-480f-9d53-2e406da3f2fe /               ext3    relatime,errors=remount-ro 0       1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  67.0GB: boot/grub/menu.lst
  67.1GB: boot/grub/stage2
  67.1GB: boot/initrd.img-2.6.24-16-generic
  67.1GB: boot/initrd.img-2.6.24-16-generic.bak
  67.1GB: boot/initrd.img-2.6.24-23-generic
  67.1GB: boot/initrd.img-2.6.24-23-generic.bak
  67.1GB: boot/vmlinuz-2.6.24-16-generic
  67.0GB: boot/vmlinuz-2.6.24-23-generic
  67.1GB: initrd.img
  67.1GB: initrd.img.old
  67.0GB: vmlinuz
  67.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

hda 

```

If you have any comments, please let mem know.


I also installed VLC (kind of tricky the process) But I am now trying to install some other stuff and see what happens.

See you here later on.

Thanks to all again.

---

### Post by caljohnsmith on 2009-05-01
That's great news you have Ubuntu and Vista dual-booting now with the help of EasyBCD. If you are happy using Vista's boot loader to dual boot in that way, then obviously there's no need to change anything about your booting process. Cheers and enjoy your dual-boot setup. :)

Best Wishes,
John

---

### Post by notuo on 2009-05-01
Thank you all.

Maybe somebody wants to marked SOLVED.

---

