---
title: "Windows 7 in Grub Menu?"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by apple_head on 2009-01-23
Hi

Just installed XP, 7 and Ubuntu in a triple boot on one SATA HDD.

Xp and Ubuntu appear in the GRUB Menu but I windows 7 doesnt?

When I press XP it takes me to a windows loader with XP and 7 in there?

How do I get Windows 7 Into the Gruib Boot loader and get rid of the Dos boot loader?

Thanks :D

---

### Post by apple_head on 2009-01-23
Have just tried editing it but windows 7 launcher just says no boot manager available??

---

### Post by caljohnsmith on 2009-01-23
In order to get a clearer picture of your setup related to your Windows booting issue, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot XP and Win7 separately.

---

### Post by apple_head on 2009-01-23
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006d299

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  268,414,019  268,413,957   7 HPFS/NTFS
/dev/sda2        268,414,020  377,463,239  109,049,220   7 HPFS/NTFS
/dev/sda3        377,463,240  475,122,374   97,659,135  83 Linux
/dev/sda4        475,122,375  488,392,064   13,269,690  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D45445C25445A856" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda2: UUID="E0FC4551FC4522E0" TYPE="ntfs" 
/dev/sda3: UUID="3b741995-30ec-4965-bfd8-fa8aee9822a5" TYPE="ext3" 
/dev/sda4: UUID="1da8b6a0-d472-4e6d-89c0-ecc31bf31a8d" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/daniel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daniel)

================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3b741995-30ec-4965-bfd8-fa8aee9822a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3b741995-30ec-4965-bfd8-fa8aee9822a5

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

title		Ubuntu 8.10
uuid		3b741995-30ec-4965-bfd8-fa8aee9822a5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3b741995-30ec-4965-bfd8-fa8aee9822a5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, (recovery mode)
uuid		3b741995-30ec-4965-bfd8-fa8aee9822a5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3b741995-30ec-4965-bfd8-fa8aee9822a5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3b741995-30ec-4965-bfd8-fa8aee9822a5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3b741995-30ec-4965-bfd8-fa8aee9822a5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=1da8b6a0-d472-4e6d-89c0-ecc31bf31a8d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location  of files loaded by Grub: ===================


 223.6GB: boot/grub/menu.lst
 223.6GB: boot/grub/stage2
 223.5GB: boot/initrd.img-2.6.27-7-generic
 223.5GB: boot/vmlinuz-2.6.27-7-generic
 223.5GB: initrd.img
 223.5GB: vmlinuz

=============================== StdErr Messages: ===============================

No errors were reported.
```

Thanks for the reply :)

Here are the results.

---

### Post by Herman on 2009-01-23
> How do I get Windows 7 Into the Gruib Boot loader and get rid of the Dos boot loader? I have Windows 7 installed just for testing and it just needs exactly the same kind of chainloader command as all the previous versions of Windows.
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
[title]("http://users.bigpond.net.au/hermanzone/p15.htm#windowstitle")        Microsoft Windows 7 Free Evaluation and Testing Edition
[root]("http://users.bigpond.net.au/hermanzone/p15.htm#root_or_rootnoverify_")        (hd0,0)
[savedefault]("http://users.bigpond.net.au/hermanzone/p15.htm#savedefault_")
[makeactive]("http://users.bigpond.net.au/hermanzone/p15.htm#makeactive")
[chainloader    +1]("http://users.bigpond.net.au/hermanzone/p15.htm#chainloader_1_")

```Where: Your Windows 7 is (hd0,0), meaning first hard disk, first partition. Please adjust the partition number according to your circumstances.  
Mine's in partition number 2 actually, so mine's (hd0,1).
I haven't tried booting it on a non-first hard disk yet.

Regards, Herman :)

---

### Post by caljohnsmith on 2009-01-23
It looks like there are a few things you'll need to do in order to get rid of the "DOS" boot loader (which is actually the Windows boot loader) and be able to boot XP and Win7 separately with Grub:
[LIST]
[*]Your Windows XP sda1 boot sector is a Vista style boot sector right now (boots "bootmgr") since your Windows 7 took over booting for both Windows versions; you'll want to restore the XP boot sector back to an XP version (boots "ntldr"). 
[*]Restore Windows 7's boot files to its own sda2 partition, make sure the BCD (Boot Configuration Data) is configured correctly to boot from that partition.
[*]Update your Grub's menu.lst with the changes so you can boot Win XP and Win 7 separately.
[/LIST]
The first thing I would recommend would be to follow step 2 of [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") in order to restore "bootmgr" and the "Boot" folder to your Windows 7 partition (you would of course boot your Win 7 Install CD and not a Vista CD like the tutorial says). Note you don't have to do the very last "bootsect" command in step 2 since your Win 7 partition all ready has a Vista boot sector. Next boot your Windows XP Install CD, go to the "recovery console", and do:
```
map
```
Find the drive letter of your Windows XP partition from the above output, and then do:
```
fixboot C:
```
And replace C with the drive letter of the XP partition. Next boot back into Ubuntu and change Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the bottom:
```
title Windows 7
root (hd0,1)
chainloader +1
```
Then reboot, try both XP and Win7 from your Grub menu, and let me know exactly what happens. We can work from there if you want.

---

### Post by itzfritz on 2009-05-02
> **caljohnsmith said:**
> It looks like there are a few things you'll need to do in order to get rid of the "DOS" boot loader (which is actually the Windows boot loader) and be able to boot XP and Win7 separately with Grub:
[LIST]
[*]Your Windows XP sda1 boot sector is a Vista style boot sector right now (boots "bootmgr") since your Windows 7 took over booting for both Windows versions; you'll want to restore the XP boot sector back to an XP version (boots "ntldr"). 
[*]Restore Windows 7's boot files to its own sda2 partition, make sure the BCD (Boot Configuration Data) is configured correctly to boot from that partition.
[*]Update your Grub's menu.lst with the changes so you can boot Win XP and Win 7 separately.
[/LIST]
The first thing I would recommend would be to follow step 2 of [this tutorial]("http://ubuntuforums.org/showpost.php?p=5726832") in order to restore "bootmgr" and the "Boot" folder to your Windows 7 partition (you would of course boot your Win 7 Install CD and not a Vista CD like the tutorial says). Note you don't have to do the very last "bootsect" command in step 2 since your Win 7 partition all ready has a Vista boot sector. Next boot your Windows XP Install CD, go to the "recovery console", and do:
```
map
```
Find the drive letter of your Windows XP partition from the above output, and then do:
```
fixboot C:
```
And replace C with the drive letter of the XP partition. Next boot back into Ubuntu and change Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the bottom:
```
title Windows 7
root (hd0,1)
chainloader +1
```
Then reboot, try both XP and Win7 from your Grub menu, and let me know exactly what happens. We can work from there if you want.

Do you have instructions re. how to do this for a Vista + Windows 7 scenario (instead of XP + Windows 7), specifically regarding the "restore the XP bootloader" instruction?

I feel that with the public release of WIndows 7 RC coming on May5, this will be required more and more.  (Currently I am unable to find specific instructions re. how to use grub to boot Vista, Windows 7, and Ubuntu).
\
Thanks!

Thanks!

---

### Post by caljohnsmith on 2009-05-02
> **itzfritz said:**
> Do you have instructions re. how to do this for a Vista + Windows 7 scenario (instead of XP + Windows 7), specifically regarding the "restore the XP bootloader" instruction?

I feel that with the public release of WIndows 7 RC coming on May5, this will be required more and more.  (Currently I am unable to find specific instructions re. how to use grub to boot Vista, Windows 7, and Ubuntu).

Thanks!
So are you trying to boot Vista and Win 7 separately from Grub, or what is your ultimate goal? It would help to get a clearer picture of your setup first, so how about following the instructions from post #3 and posting the RESULTS.txt file that the Boot Info Script outputs. We can work from there if you want.

Cheers,
John

---

### Post by itzfritz on 2009-05-04
FYI there is now a HOWTO on this subject at:
[http://ubuntuforums.org/showthread.php?t=1146266](http://ubuntuforums.org/showthread.php?t=1146266)

---

