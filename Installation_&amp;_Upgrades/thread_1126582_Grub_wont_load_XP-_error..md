---
title: "Grub wont load XP- error."
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by DrGreenthumb on 2009-04-15
Hi all, 

I installed Ubuntu (latest version) to its own ex3 partition, and created it a 1000mb swap file.  Booted fine.
I then installed Windows XP allocated to a 60gb NTFS partition on the same drive. Booted fine.

But, after the XP install i wasnt presented with an O/S boot menu, so i booted the buntu live cd and installed grub.

Ive added numerous things to grubs menu.lst in order to overcome the problem- i now have ubuntu and XP options in the boot menu, but when i select to boot XP i'm returned an error by grub stating that XP is non executable or something along those lines.

Can anyone help because im tearing my hair out here?
Boot info script results are below:
> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1e34a276

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    17,575,109    17,575,047  83 Linux
/dev/sda2          17,575,110    19,535,039     1,959,930   5 Extended
/dev/sda5          17,575,173    19,535,039     1,959,867  82 Linux swap / Solaris
/dev/sda3          19,535,040   156,280,319   136,745,280   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="25b1bd42-855f-4b73-8a19-e355c03705b1" TYPE="ext3" 
/dev/sda3: UUID="2ABCD6B4BCD67A31" TYPE="ntfs" 
/dev/sda5: UUID="496fcc47-2e3d-49c4-b199-4236b52975c1" TYPE="swap" 

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
gvfs-fuse-daemon on /home/greenthumb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=greenthumb)


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
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$eVgx./$eaiUdSsXIJXqTSZuPp7X8/
#
# examples
#
title		Windows XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1
map (hd0) (hd1)
map (hd1) (hd0)
#
#title		Ubuntu 8.4
#root		(hd0,0)
#kernel		/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=25b1bd42-855f-4b73-8a19-e355c03705b1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=25b1bd42-855f-4b73-8a19-e355c03705b1

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10 (kernel 2.6.27-7-generic)
uuid		25b1bd42-855f-4b73-8a19-e355c03705b1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=25b1bd42-855f-4b73-8a19-e355c03705b1 ro quiet 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=25b1bd42-855f-4b73-8a19-e355c03705b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=496fcc47-2e3d-49c4-b199-4236b52975c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
    .1GB: boot/initrd.img-2.6.27-7-generic
    .2GB: boot/vmlinuz-2.6.27-7-generic
    .1GB: initrd.img
    .2GB: vmlinuz

================================ sda3/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


---

### Post by ronparent on 2009-04-15
This is the text from menu.list to load windows:

title Windows XP Pro
root (hd0,0)
savedefault
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)

Since windows xp is loaded on sda3, shouldn't you use root (hd0,2)?

---

### Post by DrGreenthumb on 2009-04-15
> **ronparent said:**
> This is the text from menu.list to load windows:

title Windows XP Pro
root (hd0,0)
savedefault
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)

Since windows xp is loaded on sda3, shouldn't you use root (hd0,2)?

Thanks for your reply

I just made your recommended ammendment- upon reboot to XP (or XP select from menu) a different message now appears, and im prompted to CRTL ALT DEL.

Any more help would be greatly appreciated.

---

### Post by ronparent on 2009-04-15
Lets try redoing grub - this will hopefully rewrite menu.lst to find windows as you have it inatalled.

Booted to ubuntu (either your system or the live cd), open a terminal. Write commands as follows:

sudo grub

Getting you the grub prompt. From the prompt enter:

grub> find /boot/grub/stage1

The output of the above command will probably be (hd0,0) - in any event use the output as follows:

grub> root (hd0,0)
grub> setup (hd0)

The output of the above command will indicate if the operation was successful. Rebbot and lets see if windows will load now.

---

### Post by meierfra. on 2009-04-15
Reinstalling grub does not rewrite menu.lst. Use this  entry for XP in menu.lst


title Windows XP Pro
rootnoverify (hd0,2)
chainloader +1

---

### Post by DrGreenthumb on 2009-04-15
> **meierfra. said:**
> Reinstalling grub does not rewrite menu.lst. Use this  entry for XP in menu.lst


title Windows XP Pro
rootnoverify (hd0,2)
chainloader +1

This method worked.  Thanks very much to both of you.  Before i go, can either of you recommend a good Adobe Flash plugin for firefox, other than the Adobe one itself?

---

