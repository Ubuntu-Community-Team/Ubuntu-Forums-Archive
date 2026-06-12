---
title: "Problems with Grub Bootloader!"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by Kedaeus_Sendre on 2009-01-25
Hi!

I have 2 physical disks in my rig, one of which is split into multiple partitions.

IDE Disk 1:   /dev/sda1 37.27  GB used for BACKUP 

SATA Disk 2:  /dev/sdb1 117.19 GB NTFS Windows Partition
              /dev/sdb2 53.61  GB EXT3 Ubuntu 7.10 
              /dev/sdb3 5.0    GB SWAP 

I installed Windows first - then Ubuntu 7.10 
Windows ALWAYS Boots without the use of GRUB
I cannot overwrite the windows Bootloader. 

The odd thing is FDISK -l shows both SDA1 & SDB1 as bootable drives/partitions.

```

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b866e1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf613e97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sdb2           15299       22310    56323890   83  Linux
/dev/sdb3           22311       22947     5116702+  82  Linux swap / Solaris

```

WHERE do I need to REINSTALL GRUB in order to utilize it during boot?

I tried the following command to no avail.. 
```

sudo grub-install --root-directory=/mnt/root /dev/sdb2

```  

With previous installations (win then linux) never had this problem untill I upgraded to a 500GB SATA drive (previous installations were all IDE) what gives?

And yes, I've checked the tutorials/troubleshooting guides at help.ubuntu.com and they don't seem to help for this situation.

[COLOR="Red"]UPDATE[/COLOR]
I just attempted to boot off of a super grub disk with no success. 
SGD throws errors 
```

Error 22 No Such Partition (for LIN)
NTLDR is Missing (for WIN)

```

Everything is screaming that GRUB is installed on the wrong disk and SGD is trying to boot off the wrong disk.. 
and I got no idea what to do.

---

### Post by Kedaeus_Sendre on 2009-01-25
1. Physically removed Backup HDD and tried to boot - 
   Grub Worked, kinda.
   Threw same errors as SGD
   Edited Grub options for Linux in grub
   CHANGED root (HD1,1) to (HD0,1)
   Linux Booted sucessfully...
   Changed root parameters in /boot/grub/menu.lst

   Ubuntu works now - thank god.. 
   My wife refuses to use Linux and I've got to find the boot parameters for my windows partition. How do I find it's parameters without typing in random numbers?

---

### Post by caljohnsmith on 2009-01-25
I think it would help to get a clearer picture of your setup first, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Windows from Grub.

---

### Post by Kedaeus_Sendre on 2009-01-25
```
kedaeus@kedaeus-studio:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for kedaeus: 
bash: /home/kedaeus/Desktop/boot_info_script*.sh: No such file or directory
```

I tried to run the command you specified with no success. 

Just updated to 8.04 which reverted my menu.lst back to it's original broken-ness.. 

I've never had this much trouble dual booting before. haha.

---

### Post by caljohnsmith on 2009-01-25
Did you download the script first to your desktop? Please follow the link from my previous post to download the "boot_info_script*.sh" to your desktop, and then you should be able to run it.

---

### Post by Kedaeus_Sendre on 2009-01-25
No, because I'm an idiot and didn't notice the link and read the post wrong.
Plus I was being rushed out the house to go sledding w/ my son :D

Now that I've taken the time to read it.. the output is

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 sdb1 ntfs-3g force 0 0

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb2 and 
                       looks at sector 251169114 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Boot file info:     
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9b866e1a

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63   78,140,159   78,140,097   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdf613e97

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63  245,762,369  245,762,307   7 HPFS/NTFS
/dev/sdb2    *   245,762,370  358,410,149  112,647,780  83 Linux
/dev/sdb3        358,410,150  368,643,554   10,233,405  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="E468D0D868D0AA96" LABEL="Backup" TYPE="ntfs" 
/dev/sdb1: UUID="10B48D56B48D3F6A" TYPE="ntfs" 
/dev/sdb2: UUID="bdadfd4d-e088-46db-9be7-513047cd1109" TYPE="ext3" 
/dev/sdb3: TYPE="swap" UUID="e2bb3d0a-f60e-4032-acc7-5af9f0fbf40d" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)

=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=bdadfd4d-e088-46db-9be7-513047cd1109 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=bdadfd4d-e088-46db-9be7-513047cd1109 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=bdadfd4d-e088-46db-9be7-513047cd1109 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bdadfd4d-e088-46db-9be7-513047cd1109 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bdadfd4d-e088-46db-9be7-513047cd1109 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=bdadfd4d-e088-46db-9be7-513047cd1109 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E468D0D868D0AA96 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=10B48D56B48D3F6A /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=e2bb3d0a-f60e-4032-acc7-5af9f0fbf40d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sdb2: Location  of files loaded by Grub: ===================


 128.6GB: boot/grub/menu.lst
 128.5GB: boot/grub/stage2
 128.5GB: boot/initrd.img-2.6.22-14-generic
 128.5GB: boot/initrd.img-2.6.22-14-generic.bak
 128.5GB: boot/initrd.img-2.6.24-23-generic
 128.5GB: boot/initrd.img-2.6.24-23-generic.bak
 128.5GB: boot/vmlinuz-2.6.22-14-generic
 128.6GB: boot/vmlinuz-2.6.24-23-generic
 128.5GB: initrd.img
 128.5GB: initrd.img.old
 128.6GB: vmlinuz
 128.5GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

I'll repost once i've read it :D

---

### Post by caljohnsmith on 2009-01-25
How about doing the following:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```
Then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
Then reboot, and let me know how far you get booting Windows from Grub. We can work from there if necessary.

---

### Post by Kedaeus_Sendre on 2009-01-25
It works now, I'm not exactly sure why. 

Maybe because the following was removed from the windows boot parameters.. Dunno. 

```

map		(hd0) (hd1)
map		(hd1) (hd0)

```

I greatly appreciate all your help - I've dual booted previous systems without any problems. I don't know why this time had to be so different. 

Both Windows and Linux are booting 100%.

-Ksendre

---

### Post by blazemore on 2009-01-25
It doesn't matter which drive you install the bootloader to, **so long as your BIOS is set to boot this drive first!**

---

### Post by caljohnsmith on 2009-01-25
> **Kedaeus_Sendre said:**
> It works now, I'm not exactly sure why. 

Maybe because the following was removed from the windows boot parameters.. Dunno. 

```

map		(hd0) (hd1)
map		(hd1) (hd0)

```

I greatly appreciate all your help - I've dual booted previous systems without any problems. I don't know why this time had to be so different. 

Both Windows and Linux are booting 100%.

-Ksendre
The reason it works is because you are booting Windows from the first boot drive or (hd0), and thus you don't have to use Grub's mapping technique; you only need to use Grub's mapping technique if Windows is on a drive other than the first boot drive. Anyway, glad that worked OK, cheers and enjoy Windows and Ubuntu.

---

