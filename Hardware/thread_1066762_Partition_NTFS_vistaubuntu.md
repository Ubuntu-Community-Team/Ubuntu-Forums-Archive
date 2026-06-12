---
title: "Partition NTFS vista/ubuntu"
date: 2009-02-11
forum: Hardware
---

### Post by WannabeFantasma on 2009-02-11
Not sure if this is the right thread but

I partitioned a part NTFS on my hard drive just without things for ubuntu/vista (no /home or something) in the hope i could use it with ubuntu/vista i used it with ubuntu alot and it worked good but yesterday i had to start vista for something and now i can't "mount" the partition :(
vista won't even start up....
Someone who can help me?

---

### Post by caljohnsmith on 2009-02-11
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by WannabeFantasma on 2009-02-11
well the problem isn't really that vista doesn't start :D(don't use it) but just that the partition can't be "visited" after i started up vista :s

but i'll  do that :)

Edit:::
 kjeld@kjeld-laptop:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/kjeld/Desktop/boot_info_script*.sh: No such file or directory
HUH??

---

### Post by caljohnsmith on 2009-02-11
Did you download the script first to your desktop? Please see the link in my previous post.

---

### Post by meierfra. on 2009-02-11
deleted.

---

### Post by WannabeFantasma on 2009-02-11
lol ok i forgot that :D

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader? is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 sda1 ntfs-3g force 0 0

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 sda2 ntfs-3g force 0 0

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda4': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda4 sda4 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda4 sda4 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda4': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda4 sda4 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda4 sda4 ntfs-3g force 0 0

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x80d2f3ee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,958,054   209,957,992   7 HPFS/NTFS
/dev/sda2         209,958,912   262,258,687    52,299,776   7 HPFS/NTFS
/dev/sda3         262,261,125   293,700,329    31,439,205   5 Extended
/dev/sda5         262,261,188   268,108,784     5,847,597  82 Linux swap / Solaris
/dev/sda6         268,108,848   293,700,329    25,591,482  83 Linux
/dev/sda4         293,703,344   312,581,807    18,878,464   7 HPFS/NTFS

/dev/sda4 ends after the last cylinder of /dev/sda

Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 4047 MB, 4047372288 bytes
13 heads, 32 sectors/track, 19002 cylinders, total 7905024 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x709a3cfb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064     7,905,023     7,896,960   7 HPFS/NTFS

/dev/sdb1 ends after the last cylinder of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0515A45E72386AE3" TYPE="ntfs" 
/dev/sda2: UUID="0E5E2F645E2F4435" LABEL="Vibuntu" TYPE="ntfs" 
/dev/sda4: UUID="485221BD5221B09C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="ff1f6fe6-2585-42ea-9327-daeb67ae2cbf" TYPE="swap" 
/dev/sda6: UUID="b60748ca-f4f7-4d9c-975c-6bc405f1753c" TYPE="ext3" 
/dev/sdb1: UUID="30706C42706C10C0" LABEL="KJELD'S USB" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/kjeld/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kjeld)
/dev/sdb1 on /media/KJELD'S USB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b60748ca-f4f7-4d9c-975c-6bc405f1753c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b60748ca-f4f7-4d9c-975c-6bc405f1753c

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
uuid		b60748ca-f4f7-4d9c-975c-6bc405f1753c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b60748ca-f4f7-4d9c-975c-6bc405f1753c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		b60748ca-f4f7-4d9c-975c-6bc405f1753c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=b60748ca-f4f7-4d9c-975c-6bc405f1753c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b60748ca-f4f7-4d9c-975c-6bc405f1753c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b60748ca-f4f7-4d9c-975c-6bc405f1753c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b60748ca-f4f7-4d9c-975c-6bc405f1753c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b60748ca-f4f7-4d9c-975c-6bc405f1753c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b60748ca-f4f7-4d9c-975c-6bc405f1753c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b60748ca-f4f7-4d9c-975c-6bc405f1753c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ff1f6fe6-2585-42ea-9327-daeb67ae2cbf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 140.2GB: boot/grub/menu.lst
 140.3GB: boot/grub/stage2
 140.2GB: boot/initrd.img-2.6.27-11-generic
 140.2GB: boot/initrd.img-2.6.27-7-generic
 140.3GB: boot/vmlinuz-2.6.27-11-generic
 140.3GB: boot/vmlinuz-2.6.27-7-generic
 140.2GB: initrd.img
 140.2GB: initrd.img.old
 140.3GB: vmlinuz
 140.3GB: vmlinuz.old
```

---

### Post by caljohnsmith on 2009-02-11
It looks like the issue is that all your NTFS partitions were "uncleanly" shutdown or unmounted. You could try the following:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo ntfsfix /dev/sda2
sudo ntfsfix /dev/sda4
```
Then try mounting the partitions again, and let me know what the result is.

---

### Post by WannabeFantasma on 2009-02-11
well vista was shut down normally yesterday when i wanted to "unmount" the partition (not sure if that's even possible) today it just loaded for 5 minutes and nothing... so yeh i shut it down with the power button (Unclean shut down)

wooow :o it worked for my Vibuntu partition :D now going to try if vista loads :) 
other wise just **** vista and UBUNTU all the way (after i figure out why the people in the store say HP has a create recovery disk program but i can't find it :s)
[LIST]
thanks for the help :D 
i'll report back in later to tell you if vista works

Well vista still doesn't work (keeps loading for a looooong time :D But meh i got my music and that's the most important for me :D (back up data and try to recover vista just to have vista so my mom doesn't start to whine :D)

---

