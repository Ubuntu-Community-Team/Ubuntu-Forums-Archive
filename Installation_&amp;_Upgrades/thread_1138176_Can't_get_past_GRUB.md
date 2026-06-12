---
title: "Can't get past GRUB"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by tourist on 2009-04-26
I just upgraded to 9.04, and after getting a new GRUB menu, choosing any of the options will get me a "Starting up... Loading, please wait..." message. Unfortunately, waiting a considerable amout of time will not get it to load.

Thanks for your help!

---

### Post by Triptol on 2009-04-26
Do you see the Ubuntu splash?

Or anything, like an error?

If you get the Ubuntu splash try pressing alt+f2 and see what the console tells you. We need more info to be able to help you out here.

---

### Post by tourist on 2009-04-26
I figured it's not really enough, but I don't really know what else I could tell you. No splash screen, just the text.

Any ideas?

---

### Post by meierfra. on 2009-04-26
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by tourist on 2009-05-14
Okay, so it's been a couple of weeks and the problem still exists, so enough is enough. Here are the contents of the results.txt file:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf17cf17

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   465,981,389   465,979,342   7 HPFS/NTFS
/dev/sda2         465,981,390   488,392,064    22,410,675   5 Extended
/dev/sda5         465,981,453   487,347,839    21,366,387  83 Linux
/dev/sda6         487,347,903   488,392,064     1,044,162  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="24DC1247DC121420" TYPE="ntfs" 
/dev/sda5: UUID="1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="3d773884-a3a2-496d-8d2d-1730b1aa3494" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/menu.lst: ===========================

default 0
timeout 10
color white/black white/brown

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
# kopt=root=UUID=1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c

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
uuid		1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=1b6a9c0a-43ed-4c89-85c4-5fbf831ad36c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=3d773884-a3a2-496d-8d2d-1730b1aa3494 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/disk ntfs-3g defaults,locale=en_US.UTF-8 0 0
//192.168.0.4/ /media/mc smbfs defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 243.6GB: boot/grub/menu.lst
 243.6GB: boot/grub/stage2
 243.7GB: boot/initrd.img-2.6.27-11-generic
 243.7GB: boot/initrd.img-2.6.28-11-generic
 243.8GB: boot/vmlinuz-2.6.27-11-generic
 243.7GB: boot/vmlinuz-2.6.28-11-generic
 243.7GB: initrd.img
 243.7GB: initrd.img.old
 243.7GB: vmlinuz
 243.8GB: vmlinuz.old
```

Thanks!

---

### Post by tourist on 2009-05-15
...anyone?

---

