---
title: "Dual Boot Ubuntu + Windows XP, two hard drives"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by AirKevlon1 on 2009-02-21
I can't boot to my IDE harddrive (OS=WindowsXP), but I can boot to my SATA drive (OS=Ubuntu). I just got a new PC with an empty SATA drive and wanted to add my old IDE drive.

My old setup was:
First hard drive (IDE), one partition, with Windows 98 installed.
Second hard drive (IDE), three partitions, with Windows XP installed on the third partition. I only had a boot.ini on the first drive (c:), from where I booted to XP by default (rdisk=1, partition=2).

New setup, I wish to have:
First hard drive (SATA), one partition, with Ubuntu installed.
Second hard drive (IDE), three partitions, with XP on the third.

Now my questions are:
- Do I need a boot.ini on the XP-partition to make it able to boot from Grub (chainloader +1)?
- During Ubuntu installation I chose to install Grub to hd0, which at this point seems to be the SATA drive. Is that the correct choice, or should I install it to the XP partition?


Thanks,
Raffi

---

### Post by caljohnsmith on 2009-02-21
> **AirKevlon1 said:**
> 
Now my questions are:
- Do I need a boot.ini on the XP-partition to make it able to boot from Grub (chainloader +1)?

Yes, you will need a boot.ini file in your XP partition. You could copy over the old boot.ini and just change "rdisk(1)" to "rdisk(0)" and that should work if I understood your post correctly.
> **AirKevlon1 said:**
> 
- During Ubuntu installation I chose to install Grub to hd0, which at this point seems to be the SATA drive. Is that the correct choice, or should I install it to the XP partition?

Yes, choose (hd0) or "/dev/sda" (or whichever is the the Ubuntu drive) to install Grub to. I would not recommend choosing the XP partition, because that installs Grub to the boot sector of the XP partition which corrupts the boot sector; then you won't be able to boot/mount/read the Windows partition until you fix the boot sector. Anyway, good luck with installing Ubuntu and let me know how it goes.

---

### Post by AirKevlon1 on 2009-02-21
Thanks for the quick reply.

Below is my boot info script output.I'm still wondering about a) I read somewhere in these forums, that Windows only boots when it considers itself the first hard drive. Thuerefore, do I keep the map commands in the menu.lst, as to make the second drive become the first (and the root cammand would then be (hd0,2), or do I delete the map coammands and use root (hd1,2)?
b) Does my boot.ini look correct? Does it recognize the SATA drive, thus rdisk is 1, or not (which would mean rdisk should be 0)?



============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000946f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   306,584,459   306,584,397  83 Linux
/dev/sda2         306,584,460   312,576,704     5,992,245   5 Extended
/dev/sda5         306,584,523   312,576,704     5,992,182  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98384d2b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    96,743,429    96,743,367   c W95 FAT32 (LBA)
/dev/sdb2          96,743,430   234,436,544   137,693,115   f W95 Ext d (LBA)
/dev/sdb5          96,743,493   132,022,169    35,278,677   7 HPFS/NTFS
/dev/sdb6         132,022,233   234,436,544   102,414,312   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a54f32b8-b96a-4814-9e7c-f1171abc6685" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a18c3a69-85de-462f-a4dc-60b5bf9abb4c" 
/dev/sdb1: LABEL="MISC" UUID="42A1-A11D" TYPE="vfat" 
/dev/sdb5: UUID="2880F81180F7E2EC" LABEL="XP" TYPE="ntfs" 
/dev/sdb6: LABEL="MISC 2" UUID="4403-7389" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raffi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raffi)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout		8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
title		Windows XP 0-2
rootnoverify	(hd0,2)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1


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
# kopt=root=UUID=a54f32b8-b96a-4814-9e7c-f1171abc6685 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a54f32b8-b96a-4814-9e7c-f1171abc6685

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a54f32b8-b96a-4814-9e7c-f1171abc6685
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a54f32b8-b96a-4814-9e7c-f1171abc6685 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		a54f32b8-b96a-4814-9e7c-f1171abc6685
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a54f32b8-b96a-4814-9e7c-f1171abc6685 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		a54f32b8-b96a-4814-9e7c-f1171abc6685
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a54f32b8-b96a-4814-9e7c-f1171abc6685 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a18c3a69-85de-462f-a4dc-60b5bf9abb4c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  49.6GB: boot/grub/menu.lst
  49.5GB: boot/grub/stage2
  49.5GB: boot/initrd.img-2.6.27-7-generic
  49.6GB: boot/vmlinuz-2.6.27-7-generic
  49.5GB: initrd.img
  49.6GB: vmlinuz

================================ sdb5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Windows XP" /fastdetect /NoExecute=OptIn /noguiboot

---

### Post by caljohnsmith on 2009-02-21
Yes, you will need the map commands when booting Windows from Grub, and also your Windows is installed on sdb5 which is a logical partition; you have to take a few extra steps to boot Windows from a logical partition. To start with, the correct Grub entry should be:
```
title Windows XP
rootnoverify (hd1,4)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Also, the Windows sdb5 partition is missing its other boot files, "ntldr" and "NTDETECT.COM", so you will need to copy those over from the same partition where you got the boot.ini file. Also make sure to use "rdisk(0)" in your boot.ini file. And lastly, your Windows sdb5 boot sector needs to be fixed before you will be able to boot Windows directly from its logical partition. To fix the boot sector, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct sdb HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sdb5 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu.

---

### Post by AirKevlon1 on 2009-02-21
Ok, so I did everything you suggested. What I now get is a blue screen, which tells me to do a virus check on my hd, remove all recently added hd's and their drivers, to check the hd's assembly and "terminator". I should do a CHKDSK /F and do a restart. The error message is: STOP:0x0000007B.

That's strange, because it certainly works in my old machine. How could I fix this?

---

### Post by caljohnsmith on 2009-02-21
> **AirKevlon1 said:**
> Ok, so I did everything you suggested. What I now get is a blue screen, which tells me to do a virus check on my hd, remove all recently added hd's and their drivers, to check the hd's assembly and "terminator". I should do a CHKDSK /F and do a restart. The error message is: STOP:0x0000007B.

That's strange, because it certainly works in my old machine. How could I fix this?
I think that type of error is typical when you try to swap Windows on a HDD from one computer to another, because obviously the hardware changes. To try and fix it, I would start by booting your Windows Install CD, go to the "recovery console" and do:
```
map
```
That will show you the drive letters of all the partitions; find the drive letter for the XP partition and do:
```
chkdsk /r X:
```
Replace "X" with the XP drive letter, and run the command as many times as it takes until it reports no errors. I'm fairly certain that won't be enough to fix your Windows problem, but it the best place to start I think. If that doesn't work to fix Windows, I would suggest doing a "Windows Repair" from the Windows CD. Good luck and let me know how it goes.

---

### Post by AirKevlon1 on 2009-02-21
Ok, I'll try this later. I just analyzed the hd with testdisk and I noticed, that the first partition (data storage) is classified as type * (Primary Bootable), while the second (data storage) and third (XP) partitions are L (=Logical). What do you think would happen, if I'd set the XP partition to "primary bootable" and the first partition to P (=Primary)?

Thanks,
Raffi

---

### Post by caljohnsmith on 2009-02-21
> **AirKevlon1 said:**
>  What do you think would happen, if I'd set the XP partition to "primary bootable" and the first partition to P (=Primary)?

Unfortunately, changing the boot flag to the XP partition won't help you boot XP from Grub. Grub doesn't care which partition has the boot flag since Grub can boot a partition regardless of whether it has the boot flag set or not.

---

