---
title: "Connot Install Ubuntu 9.04 ...GRUB not installed"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by transit on 2009-08-28
To All,

I am trying to install Ubuntu int a PC with RAID 1 (mirroring) (2 SATA identically HDD's) and I am able to do partitions and install all the way trough , but after rebooting the PC I get the following message on the screen " Reboot and Select proper Boot device or Insert Boot media in selected boot device and press a key ". If I try to put the Ubuntu CD and use the option to try Ubuntu w/o any changes and then go to Application ->Terminal I am not seeing GRUB under /boot  partition?  All I see are 5 files in this partition.
Does anyone had this issue and what was the fix?

Thanks a lot in advance,

transit

---

### Post by stlsaint on 2009-08-28
based off what you are saying and what i get it looks like you installed ubuntu to your second drive but your bios is set to look at your other drives MBR for booting...where did you install ubuntu to?

---

### Post by transit on 2009-08-28
The Ubuntu has been installed in only one HDD in my case is dev/**sda** and the **GRUB** should be under dev/sda1 /boot .The second HDD is dev/**sdb** and I did not install anything on it.

Thanks,

transit

---

### Post by presence1960 on 2009-08-28
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by transit on 2009-08-30
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00054019

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       305,234       305,172  83 Linux
/dev/sda2             305,235    24,884,684    24,579,450  83 Linux
/dev/sda3          24,884,685   137,532,464   112,647,780   7 HPFS/NTFS
/dev/sda4         137,532,465   976,768,064   839,235,600   5 Extended
/dev/sda5         137,532,528   145,725,614     8,193,087  82 Linux swap / Solaris
/dev/sda6         145,725,678   170,305,064    24,579,387  83 Linux
/dev/sda7         170,305,128   186,691,364    16,386,237  83 Linux
/dev/sda8         186,691,428   575,817,794   389,126,367  83 Linux
/dev/sda9         575,817,858   976,768,064   400,950,207   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="a101107e-5e92-4ef1-8097-97297affb2e7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="71c548b3-ea2b-4ef4-a9d1-982a743cbb70" TYPE="ext4" 
/dev/sda3: UUID="33D33122300290ED" TYPE="ntfs" 
/dev/sda5: UUID="e112b775-d5da-4aeb-b35e-e4ac3e2cd67a" TYPE="swap" 
/dev/sda6: UUID="f2f95b50-9aae-455c-a17a-2082e124cb1a" TYPE="ext4" 
/dev/sda7: UUID="80b86193-32f8-4d02-b0dc-00c3c5b84f25" TYPE="ext4" 
/dev/sda8: UUID="b76926b5-8bf5-4f6d-84a4-16e1f15236b0" TYPE="ext4" 
/dev/sda9: UUID="0E2AC2B1623E2FF9" TYPE="ntfs" 

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


============================= sda1/grub/menu.lst: =============================

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
timeout        3

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
# kopt=root=UUID=71c548b3-ea2b-4ef4-a9d1-982a743cbb70 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a101107e-5e92-4ef1-8097-97297affb2e7

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
uuid        a101107e-5e92-4ef1-8097-97297affb2e7
kernel        /vmlinuz-2.6.28-11-generic root=UUID=71c548b3-ea2b-4ef4-a9d1-982a743cbb70 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a101107e-5e92-4ef1-8097-97297affb2e7
kernel        /vmlinuz-2.6.28-11-generic root=UUID=71c548b3-ea2b-4ef4-a9d1-982a743cbb70 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a101107e-5e92-4ef1-8097-97297affb2e7
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/menu.lst
    .1GB: grub/stage2
    .0GB: initrd.img-2.6.28-11-generic
    .0GB: vmlinuz-2.6.28-11-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=71c548b3-ea2b-4ef4-a9d1-982a743cbb70 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=a101107e-5e92-4ef1-8097-97297affb2e7 /boot           ext3    relatime        0       2
# /home was on /dev/sda7 during installation
UUID=80b86193-32f8-4d02-b0dc-00c3c5b84f25 /home           ext4    relatime        0       2
# /opt was on /dev/sda8 during installation
UUID=b76926b5-8bf5-4f6d-84a4-16e1f15236b0 /opt            ext4    relatime        0       2
# /usr was on /dev/sda6 during installation
UUID=f2f95b50-9aae-455c-a17a-2082e124cb1a /usr            ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=e112b775-d5da-4aeb-b35e-e4ac3e2cd67a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by transit on 2009-08-30
Thanks Presence 1960 , for your help. As you can see per your suggestion  I fallow your directions  and post the  command output you requested. 
Also, what is puzzle me is that this time I can see that GRUB is on MBR  under /dev/sda/  but I think b/c of booting from Live CD and option " try Ubunto w/o any changes" . W/o Live CD there is not GRUB in /BOOT partition.

Please, let me know if you need more info or outputs.

Thanks,

transit

---

### Post by transit on 2009-08-30
More info:

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop
ubuntu@ubuntu:~$ SUDO I
bash: SUDO: command not found
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# cd /boot
root@ubuntu:/boot# ls
abi-2.6.28-11-generic     System.map-2.6.28-11-generic
config-2.6.28-11-generic  vmcoreinfo-2.6.28-11-generic
memtest86+.bin
root@ubuntu:/boot#

---

### Post by presence1960 on 2009-08-30
here is a problem:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

[COLOR="Red"]sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

[/COLOR]

did you create a separate /boot partition when you did the install? If not then this is a problem because menu.lst and /etc/fstab should both be on the same partition. 

I will be right up front- I am not versed in RAID. Maybe someone who is will step in here.

---

### Post by transit on 2009-08-30
Hi,

Thank you for the help. Yes I did create a separate partition called /boot .
Also , does anyone know how to install RAID "Intel SATA RAID Controller (ICH10R) into Ubuntu? For instance in Win XP or Vista during OS installation it will ask you to load RAID Driver . During UBUNTU installation it was not any menu which could ask about installing RAID Driver? Neither latter So. this might be an answer to my issue here.

Thanks again,

transit

---

### Post by presence1960 on 2009-08-30
I believe the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") has RAID support

---

### Post by transit on 2009-08-31
Presence1960 thank you for your help. After doing more research I didn't find a workaround for my M/B RAID ICH10 R  issue with UBUNTU as well Win 7 RC so I even contacted manufacture of M/B and they said that at this moment they don't have drivers for Ubunto nor Win7 , and advised me to wait. Anyway I manage to install dual-boot Ubuntu and win7 RC but setting BIOS to see HDDs' as IDE /SATA. Also , while trying to replay to your messge I found another post who hasa fix for RAID 1  but with pitfalls . So here are the links I found which addrEss the installation using RAID (HARWARE AND SOFTWARE) which I would like it to try it sometime soon.

[FONT=courier][https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

[/FONT]

       



Thanks,

transit

---

