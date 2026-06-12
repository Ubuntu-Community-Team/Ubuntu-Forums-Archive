---
title: "Grub Error 2 after clean install of 9.04"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by tneal on 2009-07-28
I am encountering a grub error after a clean install of Ubuntu 9.04. The install completed successfully but when I rebooted, Grub Error 2, was displayed.

In an earlier post it was suggested that reinstalling grub from a Live session off the boot CD might help resolve the problem.  The commands I used follow...

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt --recheck /dev/sda

I completed these commands and rebooted but still encountered the Grub Error 2 message.

It was next suggested to download and run the bootinfoscript from sourceforge. I have run that script and following are the contents of RESULTS.txt. Any suggestions would be greatly appreciated!


```


============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2a293498

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   314,167,139   314,167,077  83 Linux
/dev/sda2         314,167,140   320,159,384     5,992,245   5 Extended
/dev/sda5         314,167,203   320,159,384     5,992,182  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e0be5e4e-1e06-4f04-b732-877ec0cb6efe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ff09b7d3-e139-41f2-ac9d-849913b06a15" TYPE="swap" 

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
# kopt=root=UUID=e0be5e4e-1e06-4f04-b732-877ec0cb6efe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e0be5e4e-1e06-4f04-b732-877ec0cb6efe

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
uuid        e0be5e4e-1e06-4f04-b732-877ec0cb6efe
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e0be5e4e-1e06-4f04-b732-877ec0cb6efe ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e0be5e4e-1e06-4f04-b732-877ec0cb6efe
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e0be5e4e-1e06-4f04-b732-877ec0cb6efe ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e0be5e4e-1e06-4f04-b732-877ec0cb6efe
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e0be5e4e-1e06-4f04-b732-877ec0cb6efe /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff09b7d3-e139-41f2-ac9d-849913b06a15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 138.9GB: boot/grub/menu.lst
 139.0GB: boot/grub/stage2
 139.0GB: boot/initrd.img-2.6.28-11-generic
 138.9GB: boot/vmlinuz-2.6.28-11-generic
 139.0GB: initrd.img
 138.9GB: vmlinuz

```

---

### Post by merlinus on 2009-07-28
FWIW, here is some info about grub error 2:

The reason why is because Intrepid now formats its partitions to use a 256 byte inode file system size, whereas previous Ubuntu verions used 128 bytes. The older Grub versions choke on the newer ext3 partitions that use 256 byte inode sizes, and Grub returns an error 2.

It seems quite rare...

You might try this:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

Also, note this:
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   314,167,139   314,167,077  83 Linux

What happened to blocks 1-62?

---

### Post by tneal on 2009-07-28
I booted from the Live CD and ran the grub commands you specified.  They appeared to run successfully, no errors or warnings.  After that I shutdown the Live CD and tried to boot from the hard drive but still encountered the Grub Error 2.

If it would help I can capture the output from the grub session?

Regarding the missing blocks (1-62) I have no idea.  I took the defaults and said to use the entire disk when prompted for partitioning info during the 9.04 install.  No errors or warnings were displayed during the install.

Should I try reinstalling and specify a different filesystem format other than ext3?  I have nothing but time invested in this yet. 

Thanks again for any help!

---

### Post by merlinus on 2009-07-28
I am still mighty suspicious about those missing blocks at the very beginning of your hdd.  Might it be a hidden partition installed by the OEM for windows recovery?  What OS was originally on the computer?

Generally the very beginning of the hdd is the mbr, which is where grub has been installed.  But if for some reason it is hidden, then that just might be the source of the problem.

---

### Post by stlsaint on 2009-07-29
merlin is right...first thing a computer hunts for is the mbr...if that is corrupt or hidden then that may be where your getting this grub error from. Based off the fact that this is a fresh install and you "nothing but time invested" i would say do a clean fresh install but first format your hdd COMPLETELY...erase that hdd from the face of this earth then re-install jaunty from scratch...if the same error than it may be bad hdd or faulty iso!!

what do you think merlin?

---

### Post by tneal on 2009-07-29
This disk originally had Windows XP installed on it by Dell.  I'll try formatting it and then reinstall 9.04 to see if that resolves the problem.  I'll let you know how it goes.

---

### Post by unutbu on 2009-07-29
tneal, I don't know the solution to your problem, but just wanted to point out that the
partition table looks fine.

The boot_info_script runs
```

fdisk -lu    # Note the -u flag
```

which outputs the start, end locations in sectors rather than blocks.

At least in my experience, the first partition (after a normal install) always starts at the 63rd sector.

---

### Post by tneal on 2009-07-29
Not sure what the problem actually was, but after I deleted all the existing partitions on the disk (using fdisk), and reinstalling 9.04 everything worked just fine.  I'm sending this reply from the machine now.

Thank you to everyone for the suggestions!

--tom

---

### Post by merlinus on 2009-07-29
Glad to hear you got it working.  Have fun!

---

