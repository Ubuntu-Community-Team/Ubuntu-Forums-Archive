---
title: "Win XP, Win7, Ubuntu (XP boot problem)"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by Ikerry on 2009-10-20
Hi@all

i hope u guys can help me. 

My problem: I installed WinXP after Ubuntu and Win7, after restoring Grub with GRUB Super CD i can not boot WinXP. 

I tried to modify the menu.lst and successfully find the right partition for winxp but after selecting Win XP in the GRUB loader i get the Message: NTLDR is missing. 

I dont really know what to do. 
plz help. 

PS: sry for the bad english

---

### Post by presence1960 on 2009-10-20
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Ikerry on 2009-10-20
Thx u here the file: 

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

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

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x46829300

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   102,402,047   102,195,200   7 HPFS/NTFS
/dev/sda3         102,407,760   231,305,759   128,898,000   5 Extended
/dev/sda5         102,407,823   219,587,759   117,179,937  83 Linux
/dev/sda6         219,587,823   231,305,759    11,717,937  82 Linux swap / Solaris
/dev/sda4    *    231,305,760   488,375,999   257,070,240   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1ADA30C5DA309F47" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="7E824D5C824D1A53" TYPE="ntfs" 
/dev/sda4: UUID="86EC78FFEC78EAB7" TYPE="ntfs" 
/dev/sda5: UUID="fd8476c0-65c8-4833-afe4-58cbcbab6ce0" TYPE="ext3" 
/dev/sda6: UUID="caea418d-1c1d-4488-a683-3305579e43b3" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/orri/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=orri)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# array will desynctitle        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1 and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=fd8476c0-65c8-4833-afe4-58cbcbab6ce0 ro acpi_osi="Linux"

## default grub root device
## e.g. groot=(hd0,0)
# groot=fd8476c0-65c8-4833-afe4-58cbcbab6ce0

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

title        Ubuntu 9.04 
uuid        fd8476c0-65c8-4833-afe4-58cbcbab6ce0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=fd8476c0-65c8-4833-afe4-58cbcbab6ce0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, (recovery mode)
uuid        fd8476c0-65c8-4833-afe4-58cbcbab6ce0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=fd8476c0-65c8-4833-afe4-58cbcbab6ce0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Windows 7 
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title         Windows XP 3
rootnoverify    (hd0,3)
savedefault    
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST







=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=fd8476c0-65c8-4833-afe4-58cbcbab6ce0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=caea418d-1c1d-4488-a683-3305579e43b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  97.4GB: boot/grub/menu.lst
  97.4GB: boot/grub/stage2
  97.4GB: boot/initrd.img-2.6.28-11-generic
  97.4GB: boot/initrd.img-2.6.28-15-generic
  97.4GB: boot/vmlinuz-2.6.28-11-generic
  97.4GB: boot/vmlinuz-2.6.28-15-generic
  97.4GB: initrd.img
  97.4GB: initrd.img.old
  97.4GB: vmlinuz
  97.4GB: vmlinuz.old

---

### Post by presence1960 on 2009-10-20
change this:

```
title Windows 7
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title Windows XP 3
rootnoverify (hd0,3)
savedefault
makeactive
chainloader +1
```

to:

```
title         Windows 7
rootnoverify  (hd0,1)
chainloader   +1

title         Windows XP 3
rootnoverify  (hd0,3)
chainloader   +1

```

Acouple of other things to look at. When a second version of Windows is installed usually the bootloader for one of them takes over booting both versions of windows. After changing the windows entries in menu.lst try booting both versions of windows. If one does not work try the other and see if you are presented with the option to choose which windows you want to use. Unfortunately that is how windows works.

The other thing is your OS section of menu.lst is rather odd. Did you edit it to be that way? Your Ubuntu should be in another spot & list the kernels with it. This will be important once you update kernels. Here is my menu.lst. Scroll down to the OSs and compare to yours.
```

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
timeout		4

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
# kopt=root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f31336b1-0908-4580-aad2-6b04ac995b9b

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f31336b1-0908-4580-aad2-6b04ac995b9b ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f31336b1-0908-4580-aad2-6b04ac995b9b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1

title           Masonux 9.04
rootnoverify    (hd0,6)
chainloader     +1
```

---

### Post by presence1960 on 2009-10-20
oops sorry (hd0,0) is your recovery partition. Try booting into Windows 7 and see if you are presented with the option of choosing XP or 7

```
title         Windows XP 3
rootnoverify  (hd0,3)
chainloader   +1
```is correct for XP

---

### Post by presence1960 on 2009-10-20
if the above does not work this is why:

```
sda4: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
[COLOR="Red"]Boot files/dirs:[/COLOR] 
```

see the red above, you have no boot files for XP.

You can fix that by doing [this]("http://ubuntuforums.org/showthread.php?t=1014708") (follow directions for XP)

This should repair your boot files for XP but then windows bootloader will be on MBR. When you boot you will go directly into windows. You will need to restore GRUB like this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

you should be good to go.

---

### Post by Ikerry on 2009-10-20
Thx u very much, it will definetliy help me

---

### Post by Mark Phelps on 2009-10-21
Looks like the OP installed 7 first, in which case, the first partition is really the new BOOT partition that 7 creates when it is installed to an unformatted drive.  You'll notice that the 7 bootloader files are present on that partition.

When XP was installed, it probably changed the MBR to point to the XP partition, thus not booting into 7 anymore, but as to why there are no XP boot files (NTLDR, boot.ini, etc) on that partition is a mystery.

When he "repairs" XP, I wouldn't be surprised if it writes the boot files to the first partition, not to the XP partition.

But even that might work since both sets of boot files will then be on a single partition. Would just have to change menu.lst to point only to that partition for MS Windows boot.

---

### Post by presence1960 on 2009-10-21
> **Mark Phelps said:**
> Looks like the OP installed 7 first, in which case, the first partition is really the new BOOT partition that 7 creates when it is installed to an unformatted drive.  You'll notice that the 7 bootloader files are present on that partition.

When XP was installed, it probably changed the MBR to point to the XP partition, thus not booting into 7 anymore, but as to why there are no XP boot files (NTLDR, boot.ini, etc) on that partition is a mystery.

When he "repairs" XP, I wouldn't be surprised if it writes the boot files to the first partition, not to the XP partition.

But even that might work since both sets of boot files will then be on a single partition. Would just have to change menu.lst to point only to that partition for MS Windows boot.

Good catch Mark, I didn't notice the partition label for sda1 is "System Reserved" which is the win 7 boot partition. I zeroed in on the fact that XP has no boot files, which is odd even if there are two versions of Windows. Thanks for the second set of eyes. To boot Win 7 from GRUB the hd designation should then be (hd0,0)

---

### Post by Mark Phelps on 2009-10-21
In looking over the report again, I noticed that the XP boot files are already present in the same partition, thus, my guess about XP writing its loader files to the first MS-compatible partition it finds was correct.

When the OP makes the changes you suggested, he should then get an MS OS selection menu when he tries to boot into XP or 7.

---

