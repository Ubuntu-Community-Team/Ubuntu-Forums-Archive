---
title: "Can not boot Windows XP after Ubuntu Install"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by metalman62 on 2009-02-19
I installed Ubuntu after Windows and had Ubuntu installer resize windows partition.  Now when select Win xp pro from Grub, it just says, "Starting up" and does nothing else.

---

### Post by norcim on 2009-02-19
post your Grub menu.lst

---

### Post by metalman62 on 2009-02-19
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		b8ec1b71-5f21-4034-806d-180fc62f47fb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b8ec1b71-5f21-4034-806d-180fc62f47fb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		b8ec1b71-5f21-4034-806d-180fc62f47fb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b8ec1b71-5f21-4034-806d-180fc62f47fb ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b8ec1b71-5f21-4034-806d-180fc62f47fb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b8ec1b71-5f21-4034-806d-180fc62f47fb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b8ec1b71-5f21-4034-806d-180fc62f47fb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b8ec1b71-5f21-4034-806d-180fc62f47fb ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b8ec1b71-5f21-4034-806d-180fc62f47fb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by metalman62 on 2009-02-19
btw, I have scsi hard drive if that makes a difference.  I am new to linux and grub.

---

### Post by Coder543 on 2009-02-19
Reboot, then select the XP entry. Instead of hitting enter, hit 'e'. Now scroll to the root (hd0,0) line. Then, change 'root' to 'rootnoverify'. Come back and tell us if that made a difference.

Edit: to change root to rootnoverify, press e once you scroll to that line. then press b to boot.

---

### Post by metalman62 on 2009-02-19
well, I tried that but its still just saying Starting up... and doing nothing.

---

### Post by Coder543 on 2009-02-19
run this command: 
ls /dev | grep sd
in a terminal
then post the results here.

---

### Post by metalman62 on 2009-02-19
ptysd
sda1
sda2
sda5
sda6
sdb
sdb1
sdc
sdd
sde
sdf
ttysd

---

### Post by caljohnsmith on 2009-02-19
It sound to me like your Windows XP boot sector probably needs to be fixed, because the file system parameters in the boot sector sometimes get corrupted after resizing the partition. So in order to find out if that might be the case, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by metalman62 on 2009-02-19
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdb

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   404,548,829   404,548,767   7 HPFS/NTFS
/dev/sda2         404,548,830   488,392,064    83,843,235   5 Extended
/dev/sda5         404,548,893   484,857,764    80,308,872  83 Linux
/dev/sda6         484,857,828   488,392,064     3,534,237  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     3,966,975     3,958,912   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="14F0DE61F0DE489E" TYPE="ntfs" 
/dev/sda5: UUID="b8ec1b71-5f21-4034-806d-180fc62f47fb" TYPE="ext3" 
/dev/sda6: UUID="616e6cd6-6415-4ef9-8de9-6c9557e37df4" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" UUID="CCF5-B945" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/joshua/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=joshua)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=5

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b8ec1b71-5f21-4034-806d-180fc62f47fb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b8ec1b71-5f21-4034-806d-180fc62f47fb

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		b8ec1b71-5f21-4034-806d-180fc62f47fb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b8ec1b71-5f21-4034-806d-180fc62f47fb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		b8ec1b71-5f21-4034-806d-180fc62f47fb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b8ec1b71-5f21-4034-806d-180fc62f47fb ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		b8ec1b71-5f21-4034-806d-180fc62f47fb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b8ec1b71-5f21-4034-806d-180fc62f47fb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=616e6cd6-6415-4ef9-8de9-6c9557e37df4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 225.5GB: boot/grub/menu.lst
 225.6GB: boot/grub/stage2
 225.5GB: boot/initrd.img-2.6.27-11-generic
 225.5GB: boot/initrd.img-2.6.27-7-generic
 225.5GB: boot/vmlinuz-2.6.27-11-generic
 225.5GB: boot/vmlinuz-2.6.27-7-generic
 225.5GB: initrd.img
 225.5GB: initrd.img.old
 225.5GB: vmlinuz
 225.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by caljohnsmith on 2009-02-19
OK, I think we should use "testdisk" to check if your Windows XP boot sector needs fixing; first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows sda1 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows XP from the Grub menu. Or if testdisk says the boot sectors are identical and doesn't give you an option to "Rebuild BS", let me know, and we can work from there.

---

### Post by metalman62 on 2009-02-19
well testdisk said it was bad.  I did everything you said and rebooted. It worked and started chkdsk.  said volume was dirty, scanned, rebooted, and now it booted right up!  Thanks alot for the help!

---

### Post by caljohnsmith on 2009-02-19
That's great news testdisk saved the day once again; cheers and enjoy your dual-boot Ubuntu/Windows setup. :)

---

### Post by etdsbastar on 2009-02-19
Tell me the partition information please, so that i can try to give you a solution.

---

### Post by flairtorc on 2009-09-19
i did everything caljohnsmith said with testdisk....and i got the note where it says the boot sectors are identical..and it alows me the option to"rebuild bs"....but from there i have no idea what to do..it would be really nice if someone could help me out..and yes...I have the same problem metalman62 started the thread for

---

### Post by flairtorc on 2009-09-19
doesn't anyone know what to do for this..?

---

