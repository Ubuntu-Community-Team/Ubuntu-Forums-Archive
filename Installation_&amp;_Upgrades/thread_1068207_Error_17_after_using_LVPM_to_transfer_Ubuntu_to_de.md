---
title: "Error 17 after using LVPM to transfer Ubuntu to dedicated Partition"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Mahogan on 2009-02-12
Results of boot error 17 after using Boot Info Script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6e566e56

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   716,804,234   716,804,172   7 HPFS/NTFS
/dev/sda2         716,804,235 1,090,974,149   374,169,915  83 Linux
/dev/sda3       1,091,054,475 1,448,757,764   357,703,290  83 Linux
/dev/sda4       1,448,757,765 1,465,144,064    16,386,300  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="40D8B637D8B62B54" LABEL="750GB" TYPE="ntfs" 
/dev/sda3: UUID="f2c9a6bb-6047-4bca-952a-cdd40f250711" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="b0943acf-21b3-47ae-b4b0-8558b65eb7b2" TYPE="swap" 
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

==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=40D8B637D8B62B54 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=40D8B637D8B62B54 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=40D8B637D8B62B54 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-3-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=40D8B637D8B62B54 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=40D8B637D8B62B54 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda3
root (hd0,2)
configfile /boot/grub/menu.lst



======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"


=================== sda1: Location of files loaded by Grub: ===================


 217.6GB: ubuntu/disks/boot/grub/menu.lst
 139.7GB: ubuntu/disks/boot/initrd.img-2.6.27-3-rt
  32.8GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
  32.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-3-rt
  32.6GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic

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
# kopt=root=UUID=f2c9a6bb-6047-4bca-952a-cdd40f250711  ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2c9a6bb-6047-4bca-952a-cdd40f250711  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2c9a6bb-6047-4bca-952a-cdd40f250711  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-3-rt
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=f2c9a6bb-6047-4bca-952a-cdd40f250711  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=f2c9a6bb-6047-4bca-952a-cdd40f250711  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,0)
makeactive
chainloader +1
boot


title Microsoft Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1
boot


=============================== sda3/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda3
UUID=f2c9a6bb-6047-4bca-952a-cdd40f250711     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda1
UUID=40D8B637D8B62B54       /media/drv0       ntfs-3g         defaults      0   0


# /dev/sda4
UUID=b0943acf-21b3-47ae-b4b0-8558b65eb7b2      none            swap        sw          0   0


=================== sda3: Location of files loaded by Grub: ===================


 601.6GB: boot/grub/menu.lst
 601.7GB: boot/grub/stage2
 601.6GB: boot/initrd.img-2.6.27-3-rt
 601.6GB: boot/initrd.img-2.6.27-7-generic
 601.7GB: boot/vmlinuz-2.6.27-3-rt
 601.7GB: boot/vmlinuz-2.6.27-7-generic
 601.6GB: initrd.img
 601.6GB: initrd.img.old
 601.7GB: vmlinuz
 601.7GB: vmlinuz.old

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script024.sh: line 1043: [: =: unary operator expected
```

---

### Post by caljohnsmith on 2009-02-12
So it looks like you have Kubuntu installed to sda3, but you also have Ubuntu installed inside Windows as a Wubi install? Also, did you manually edit your sda3 menu.lst so that it looks similar to your Wubi install menu.lst? Anyway, to correct your sda3 menu.lst, how about first doing:
```
sudo mount /dev/sda3 /mnt && kdesu kate /mnt/boot/grub/menu.lst
```
I'm not sure if the Kubuntu CD comes with kate, kedit, or both, so if you get an error with the above command, try kedit in place of kate. Next replace all the "root" lines in your menu.lst with a "uuid" line like:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]uuid            f2c9a6bb-6047-4bca-952a-cdd40f250711[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2c9a6bb-6047-4bca-952a-cdd40f250711  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
```
Also change the groot line:
```
# groot=f2c9a6bb-6047-4bca-952a-cdd40f250711
```
Also, you have three essentially identical entries to boot Windows at the end of your menu.lst, so I would recommend deleting two of them and just keeping one. Next reboot, and let me know how far you get when booting Kubuntu.

---

### Post by Mahogan on 2009-02-12
Actually this is not Kubuntu, but Ubuntu Studio.  So wont this affect the code that you wrote with the kde commands?

Just to clairfy my process and answer some of the questions. I initially installed Ubuntu within windows, then used LVPM within Ubuntu to transfer to a dedicated partition sda3 that I created beforehand.  After doing this it did not delete my Ubuntu within windows, but copied to sda3.  I plan on deleting my Ubuntu install from within windows once my sda3 partition is working properly.

So please let me know if that code will work for Ubuntu rather than Kubuntu, as KDE is not installed.

---

### Post by caljohnsmith on 2009-02-12
OK, thanks for clarifying, try this command instead:
```
sudo mount /dev/sda3 /mnt && gksudo gedit /mnt/boot/grub/menu.lst
```

---

### Post by Mahogan on 2009-02-12
That worked great!  Thank you.

Now I'm okay to delete Ubuntu from within Window right?  


My next chore is I would like to change the Grub Menu to look something clean and simple, like this:

Please Select Boot OS Choice:
1) Windows XP
2) Mac
3) Ubuntu


Once Option 3) Ubuntu is selected, perhaps allowing the other Ubuntu recovery mode and Memtest options to be selected.


Ive searched for something similar, but not quite the same.

Would you know if this is possible?

---

### Post by caljohnsmith on 2009-02-12
Well if you want Windows to be first in your menu, just move it directly above the "Automagic Kernels" lines in your menu.lst:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
And if you want a submenu for Ubuntu, what you can do is create another menu.lst, say menu_ubuntu.lst, and put the Ubuntu entries in that file. Then in your main menu.lst you can use:
```
title           Ubuntu
uuid            f2c9a6bb-6047-4bca-952a-cdd40f250711
configfile      /boot/grub/[COLOR="Blue"]menu_ubuntu.lst[/COLOR]
```
Also, it sounds like it would be OK to delete your Wubi install, but to be on the safe side you might want to give it just a few days. Glad you can at least boot Windows and Ubuntu now.

---

### Post by Mahogan on 2009-02-12
That works Perfect!  I like the ability to simplify the menu, now my wife & kids will not be confused when starting the computer.  And it will load their default XP when starting, so they don't even have to stress over the choices.  

Thanks again John, your the best!

---

### Post by caljohnsmith on 2009-02-12
Glad to hear that worked OK; cheers and enjoy all your OSes. :)

---

### Post by irfan9727 on 2009-04-10
I also have the same problem, and I'm using Ubuntu 8.10. I transferred Ubuntu to /dev/sda9. Where I can download the Boot Info Script?

---

### Post by meierfra. on 2009-04-10
> Where I can download the Boot Info Script? 

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Download the script to  your desktop and run it via

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by irfan9727 on 2009-04-10
The result:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8ded8de

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   156,296,384   115,330,635   5 Extended
/dev/sda5          40,965,813    65,786,174    24,820,362   7 HPFS/NTFS
/dev/sda6          65,786,238   102,398,309    36,612,072   7 HPFS/NTFS
/dev/sda7         102,398,373   134,849,609    32,451,237   7 HPFS/NTFS
/dev/sda8         134,849,673   136,954,124     2,104,452  82 Linux swap / Solaris
/dev/sda9         136,954,188   156,296,384    19,342,197  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="B6B0BB3FB0BB0541" TYPE="ntfs" 
/dev/sda5: UUID="EC88E12688E0F04E" LABEL="Data" TYPE="ntfs" 
/dev/sda6: UUID="54942E59942E3DBC" LABEL="Other" TYPE="ntfs" 
/dev/sda7: UUID="8850F4B950F4AED6" LABEL="Multimedia" TYPE="ntfs" 
/dev/sda8: UUID="c818c717-86fd-426b-996c-4f61bda7a44b" TYPE="swap" 
/dev/sda9: UUID="09b8370d-d20e-45c1-8951-dfb906bb0e4a" TYPE="ext3" 
/dev/loop0: UUID="0a456348-502d-4a62-93e4-eaa044b8522a" TYPE="ext3" 

=============================== "mount" output: ===============================

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda6 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/irfan9727/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=irfan9727)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda5 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/Multimedia type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9 on /mnt type ext3 (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=7NNVFC /Kernel=TUKernel.exe
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=7NNVFC-BAK
c:\wubildr.mbr="Ubuntu"

==================== sda6/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=54942E59942E3DBC loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54942E59942E3DBC loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=54942E59942E3DBC loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda9
root (hd0,8)
configfile /boot/grub/menu.lst



======================== sda6/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================== sda6Wubi: ==================================

Operating System: "Ubuntu 8.10"

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda6: Location of files loaded by Grub: ===================


  33.8GB: ubuntu/disks/boot/grub/menu.lst
  33.9GB: ubuntu/disks/boot/initrd.img-2.6.27-7-generic
  33.8GB: ubuntu/disks/boot/vmlinuz-2.6.27-7-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda8

00000000  b2 6a 3f 39 8d ac c3 ef  2e 2b 3c cd e4 a0 f4 39  |.j?9.....+<....9|
00000010  d9 86 02 c0 2a ec 2e f8  d3 34 be f7 5e 34 d3 2b  |....*....4..^4.+|
00000020  2b 2e f4 66 8d af 65 cb  f1 c5 f4 1b 29 ba 3c ec  |+..f..e.....).<.|
00000030  fc 87 50 45 1f 3b 8c 13  d5 d9 08 46 81 a9 36 f9  |..PE.;.....F..6.|
00000040  8e 88 b0 43 ef eb 49 d4  da d0 1f f0 79 6d 9a 40  |...C..I.....ym.@|
00000050  b3 9d 35 3d 47 b9 08 57  87 7c 04 4c 90 c2 00 b6  |..5=G..W.|.L....|
00000060  d3 38 10 39 68 04 f1 31  12 a4 d2 02 9f 3d 29 d6  |.8.9h..1.....=).|
00000070  9c 8c 7a cc dd 3d 63 cf  f0 a6 4f f4 25 0b ed 84  |..z..=c...O.%...|
00000080  99 85 e7 a3 ef 14 5f 71  74 a7 ce 50 3a 53 ab 9c  |......_qt..P:S..|
00000090  2e e8 6a 0f 67 ba 97 5b  fd 04 1c f8 6e d5 09 45  |..j.g..[....n..E|
000000a0  d3 d3 8f 8d 0d dd 59 28  a4 88 12 1f 0f 69 3d 05  |......Y(.....i=.|
000000b0  9f 72 92 ae cd d2 0c 38  9f 26 a0 9d 10 48 7a 81  |.r.....8.&...Hz.|
000000c0  15 d6 8f 18 67 7b cb 2b  6f ac b3 23 4a 49 ef 5a  |....g{.+o..#JI.Z|
000000d0  ce 0d 8f 3a 45 46 a2 0b  93 7c a8 14 76 b6 32 c8  |...:EF...|..v.2.|
000000e0  55 6d 78 75 0e 84 08 40  4e f4 19 c4 e2 5c e6 5a  |Umxu...@N....\.Z|
000000f0  90 e1 01 5b 42 91 4d 31  35 19 d5 ce 3e a2 8a 67  |...[B.M15...>..g|
00000100  7b 1c a5 00 ed 34 85 62  3f 91 5c 34 09 54 40 c6  |{....4.b?.\4.T@.|
00000110  87 fc b7 00 2e 72 7c 97  1f a0 d2 0f ca cc dd 10  |.....r|.........|
00000120  33 3a db 9c 67 d8 0e 3e  dc af 15 0e 85 66 e4 6a  |3:..g..>.....f.j|
00000130  bf 1f 1f 13 42 bc fd 7d  cd 82 2e 5d e3 c7 4b 5d  |....B..}...]..K]|
00000140  8f 1c 92 8c 8a 74 ba 2b  a5 0d 61 2e 6d 10 8a 5d  |.....t.+..a.m..]|
00000150  bb bb 5e 80 25 91 9e fc  95 78 bc 9e a7 17 8c 2c  |..^.%....x.....,|
00000160  ad 31 94 6b 3f a8 f7 45  13 e1 07 be a8 c4 79 8f  |.1.k?..E......y.|
00000170  ff 2f b8 18 f5 a4 ae fd  9a 5c 72 b0 5b 3c 95 dd  |./.......\r.[<..|
00000180  d8 70 40 5d 6f bb a6 48  e1 27 88 9a b9 98 80 1c  |.p@]o..H.'......|
00000190  c5 e8 eb 27 30 ee 2b be  15 59 3b 63 50 1d 57 57  |...'0.+..Y;cP.WW|
000001a0  cd 6e 15 ce 3e f6 c8 03  d0 bf 54 55 58 de 22 ac  |.n..>.....TUX.".|
000001b0  0e ed 32 0d c9 ce 91 c3  c7 e6 3a 02 c3 a9 75 09  |..2.......:...u.|
000001c0  33 83 ad 4a 12 a1 5e 57  56 e6 4a ad ba 92 a6 bb  |3..J..^WV.J.....|
000001d0  1c 6a 53 2a e8 62 a2 87  0d 39 a5 b7 45 13 de c7  |.jS*.b...9..E...|
000001e0  bf 05 5e 2b 1e 58 c3 de  60 42 06 f0 d6 7a 63 b9  |..^+.X..`B...zc.|
000001f0  cc 5e d5 49 1b 27 b3 44  01 51 22 d8 18 d7 94 b6  |.^.I.'.D.Q".....|
00000200


=============================== StdErr Messages: ===============================

/home/irfan9727/Desktop/boot_info_script29.sh: line 1229: cd: /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda9 on /mnt: No such file or directory
```

What should I do next?

---

### Post by meierfra. on 2009-04-10
> =============================== StdErr Messages: ===============================

/home/irfan9727/Desktop/boot_info_script29.sh: line 1229: cd: /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda9 on /mnt: No such file or directory

There seems to be a bug in the boot info script which  prevented the boot files on /dev/sda9 to be displayed.  So I need some more information:

Please post the output of

```
sudo mkdir /media/sda9
sudo mount /dev/sda9 /media/sda9
cat /media/sda9/boot/grub/menu.lst 
```

---

### Post by irfan9727 on 2009-04-10
Bug? Anyway, this is the result:

```
irfan9727@ubuntu:~$ sudo mkdir /media/sda9
[sudo] password for irfan9727: 
irfan9727@ubuntu:~$ sudo mount /dev/sda9 /media/sda9
irfan9727@ubuntu:~$ cat /media/sda9/boot/grub/menu.lst
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
# kopt=root=UUID=09b8370d-d20e-45c1-8951-dfb906bb0e4a  ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=09b8370d-d20e-45c1-8951-dfb906bb0e4a  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=09b8370d-d20e-45c1-8951-dfb906bb0e4a  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,5)
makeactive
chainloader +1
boot


title Windows NT/2000/XP (loader)
root (hd0,0)
makeactive
chainloader +1
boot

irfan9727@ubuntu:~$ 

```

Thanks for helping.

---

### Post by meierfra. on 2009-04-10
Mount /dev/sda9  (only do this if you  did reboot since the last time you mounted /dev/sd9):

```
sudo mkdir /media/sda9
sudo mount /dev/sda9 /media/sda9

```

Open menu.lst via

```
gksudo gedit /media/sda9/boot/grub/menu.lst
```

Change  

# groot=()/ubuntu/disks

to 

# groot=09b8370d-d20e-45c1-8951-dfb906bb0e4a


change  all three occurrences of 


root		()/ubuntu/disks

to

uuid   09b8370d-d20e-45c1-8951-dfb906bb0e4a 


Save the file and reboot. Hopefully you will now  be able to boot into Ubuntu.

---

### Post by irfan9727 on 2009-04-10
do you mean change this
root            ()/ubuntu/disks *to*
root            ()uuid 09b8370d-d20e-45c1-8951-dfb906bb0e4a
**or**
root            ()/ubuntu/disks *to*
uuid            09b8370d-d20e-45c1-8951-dfb906bb0e4a ?

I'm confused :( 
Maybe you can post the edited menu.lst, please?

---

### Post by meierfra. on 2009-04-10
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
# kopt=root=UUID=09b8370d-d20e-45c1-8951-dfb906bb0e4a  ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=09b8370d-d20e-45c1-8951-dfb906bb0e4a

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
uuid            09b8370d-d20e-45c1-8951-dfb906bb0e4a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=09b8370d-d20e-45c1-8951-dfb906bb0e4a  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            09b8370d-d20e-45c1-8951-dfb906bb0e4a
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=09b8370d-d20e-45c1-8951-dfb906bb0e4a  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid            09b8370d-d20e-45c1-8951-dfb906bb0e4a
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1



```

I made the chances. I also deleted the last two Windows item. (One was a duplicate and the other would just produce an error message.

---

### Post by irfan9727 on 2009-04-12
It works. Thanks!

---

### Post by meierfra. on 2009-04-12
> It works. Thanks!
Great. Enjoy your new Ubuntu.

---

### Post by eyadhafez on 2009-12-31
Please help me with this !!!!

[HTML]============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr.mbr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb6/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x74268b97

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sda2         102,398,310   976,768,064   874,369,755   f W95 Ext d (LBA)
/dev/sda5         102,398,373   976,768,064   874,369,692   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x53705370

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   102,398,309   102,398,247   7 HPFS/NTFS
/dev/sdb2         102,398,310   488,375,999   385,977,690   5 Extended
/dev/sdb5         102,398,373   204,796,619   102,398,247   7 HPFS/NTFS
/dev/sdb6         204,796,683   235,528,964    30,732,282   7 HPFS/NTFS
/dev/sdb7         235,529,028   307,194,929    71,665,902  83 Linux
/dev/sdb8         307,194,993   488,375,999   181,181,007   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="c8494eaa-e804-4134-be44-016a41caaaa3" TYPE="ext3" 
/dev/sda1: UUID="82701D48701D43F7" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda5: UUID="389892409891FD16" LABEL="Big Storage" TYPE="ntfs" 
/dev/sdb1: UUID="F8A40F35A40EF642" TYPE="ntfs" 
/dev/sdb5: UUID="004C05C14C05B308" TYPE="ntfs" 
/dev/sdb6: UUID="B018F14818F10DDA" TYPE="ntfs" 
/dev/sdb7: UUID="6f07c6b0-54f1-4119-b17e-34d3aad2c77c" TYPE="ext3" 
/dev/sdb8: UUID="543410F93410E032" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/loop0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/sdb5 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6 on /media/sdb6 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eyad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eyad)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb7 on /media/sdb7 type ext3 (rw)
/dev/sr1 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,utf8,user=eyad)
/dev/sdb8 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


==================== sda5/ubuntu/disks/boot/grub/menu.lst: ====================

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
default		2

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
# kopt=root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst



======================== sda5/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

=================== sda5: Location of files loaded by Grub: ===================


  52.4GB: ubuntu/disks/boot/grub/menu.lst
  52.4GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
  52.4GB: ubuntu/disks/boot/initrd.img-2.6.31-14-generic
  52.4GB: ubuntu/disks/boot/initrd.img-2.6.31-15-generic
  52.4GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic
  52.4GB: ubuntu/disks/boot/vmlinuz-2.6.31-14-generic
  52.4GB: ubuntu/disks/boot/vmlinuz-2.6.31-15-generic

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc          proc         defaults                      0  0  
/host/ubuntu/disks/root.disk  /              ext3         loop,errors=remount-ro        0  1  
/host/ubuntu/disks/boot       /boot          none         bind                          0  0  
/host/ubuntu/disks/swap.disk  none           swap         loop,sw                       0  0  
/dev/scd0                     /media/cdrom0  udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/scd1                     /media/cdrom1  udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/sda5                     /media/D Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda1                     /media/C Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda6                     /media/sda6    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sda7                     /media/F Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda1                     /media/sda1    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sda5                     /media/sda5    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda7                     /media/sda7    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sdb1                     /media/sdb1    vfat         dmask=227,user                0  0  
/dev/sdb5                     /media/sdb5    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda2                     /media/sda2    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda3                     /media/sda3    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sdb6                     /media/sdb6    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sdb7                     /media/sdb7    ntfs         nls=iso8859-1,umask=000,user  0  0  

================= sda5/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz

================================ sdb1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

c:\wubildr.mbr="Ubuntu" 


==================== sdb6/ubuntu/disks/boot/grub/menu.lst: ====================

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
default		2

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
# kopt=root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=B018F14818F10DDA loop=/ubuntu/disks/root.disk ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sdb7
root (hd1,6)
configfile /boot/grub/menu.lst



======================== sdb6/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

=================== sdb6: Location of files loaded by Grub: ===================


 104.8GB: ubuntu/disks/boot/grub/menu.lst
 104.8GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
 104.8GB: ubuntu/disks/boot/initrd.img-2.6.31-14-generic
 104.8GB: ubuntu/disks/boot/initrd.img-2.6.31-15-generic
 104.8GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic
 104.8GB: ubuntu/disks/boot/vmlinuz-2.6.31-14-generic
 104.8GB: ubuntu/disks/boot/vmlinuz-2.6.31-15-generic

============================= sdb6/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc          proc         defaults                      0  0  
/host/ubuntu/disks/root.disk  /              ext3         loop,errors=remount-ro        0  1  
/host/ubuntu/disks/boot       /boot          none         bind                          0  0  
/host/ubuntu/disks/swap.disk  none           swap         loop,sw                       0  0  
/dev/scd0                     /media/cdrom0  udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/scd1                     /media/cdrom1  udf,iso9660  user,noauto,exec,utf8         0  0  
/dev/sda5                     /media/D Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda1                     /media/C Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda6                     /media/sda6    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sda7                     /media/F Drive  ntfs         nls=iso8859-1,umask=000  0  0  
/dev/sda1                     /media/sda1    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sda5                     /media/sda5    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda7                     /media/sda7    ntfs         nls=iso8859-1,umask=000       0  0  
/dev/sdb1                     /media/sdb1    vfat         dmask=227,user                0  0  
/dev/sdb5                     /media/sdb5    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda2                     /media/sda2    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sda3                     /media/sda3    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sdb6                     /media/sdb6    ntfs         nls=iso8859-1,umask=000,user  0  0  
/dev/sdb7                     /media/sdb7    ntfs         nls=iso8859-1,umask=000,user  0  0  

================= sdb6/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sdb7/boot/grub/menu.lst: ===========================

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
default		8

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
# kopt=root=UUID=  ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=  ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,3)
kernel		/vmlinuz root=/dev/hda3 ro
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=  ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=  ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title UnknownOS
root (hd1,5)
makeactive
chainloader +1
boot


title Windows 7 (loader)
root (hd1,0)
makeactive
chainloader +1
boot


=============================== sdb7/etc/fstab: ===============================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sdb7
UUID=     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sdb6
UUID=       /media/drv0                defaults      0   0


=================== sdb7: Location of files loaded by Grub: ===================


 120.5GB: boot/grub/menu.lst
 120.5GB: boot/grub/stage2
 120.5GB: boot/initrd.img-2.6.28-16-generic
 120.5GB: boot/initrd.img-2.6.31-14-generic
 120.5GB: boot/initrd.img-2.6.31-15-generic
 120.5GB: boot/initrd.img-2.6.31-16-generic
 120.5GB: boot/vmlinuz-2.6.28-16-generic
 120.5GB: boot/vmlinuz-2.6.31-14-generic
 120.5GB: boot/vmlinuz-2.6.31-15-generic
 120.5GB: initrd.img
 120.5GB: initrd.img.old
 120.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 31 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |.1..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 80 fa 33 c0 8e d8  8e d0 bc 00 7c b8 30 08  |....3.......|.0.|
00000040  8e c0 fb b8 00 b8 8e e8  e8 1d 00 b9 03 00 32 f6  |..............2.|
00000050  b8 28 02 2e 8a 16 32 7c  bb 00 01 50 cd 13 72 03  |.(....2|...P..r.|
00000060  58 cd 13 ea 00 01 30 08  60 b9 e8 03 33 db 66 65  |X.....0.`...3.fe|
00000070  c7 07 00 00 00 00 83 c3  04 e2 f3 b4 02 32 ff 33  |.............2.3|
00000080  d2 cd 10 61 c3 60 b4 a0  f6 e4 32 ff d1 e3 03 d8  |...a.`....2.....|
00000090  8a 14 0a d2 74 09 65 89  17 46 83 c3 02 eb f1 61  |....t.e..F.....a|
000000a0  c3 50 61 72 61 67 6f 6e  00 4c 6f 61 64 69 6e 67  |.Paragon.Loading|
000000b0  2e 2e 2e 2e 00 4d 42 52  20 52 65 76 69 73 69 6f  |.....MBR Revisio|
000000c0  6e 20 30 00 ef ee fe ff  ef ee fe ff ef ee fe ff  |n 0.............|
000000d0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
000000e0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
000000f0  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000100  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000110  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000120  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000130  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000140  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000150  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000160  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000170  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000180  ef ee fe ff ef ee fe ff  ef ee fe ff ef ee fe ff  |................|
00000190  ef ee fe ff ef ee fe ff  3a 00 00 00 3c 00 00 00  |........:...<...|
000001a0  00 00 00 00 00 00 00 00  fb ce f5 0a cf a0 a3 7b  |...............{|
000001b0  00 00 00 00 3b 59 2e 1f  97 8b 26 74 ef ee 80 01  |....;Y....&t....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 27 79 1a 06 00 00  |......?...'y....|
000001d0  c1 ff 0f fe ff ff 66 79  1a 06 db d2 1d 34 00 00  |......fy.....4..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))[/HTML]

---

### Post by erenay on 2010-01-02
I have the same problem, described in the title.
Can anybody help me about this?

I tried to transfer the wubi installation on windows vista to a separate partition, but I think, mistakenly I tried to transfer it to the swap partition. Now I am getting the Error 17 from Grub and I am unable to boot into any operating system.

Additionally, before creating the ext3 partition to transfer ubuntu, windows partition manager did not allow me to shrink for enough space, so I used an opensource third party tool to create the ext3 partition, and that might have caused improper fragmentation of the kernel.

When I check /dev/sda2 with ubuntu partition editor, It gives 35 "cluster accounting failed at ... extra cluster in $Bitmap" errors: [http://img685.imageshack.us/img685/9315/screenshoter.png](http://img685.imageshack.us/img685/9315/screenshoter.png)


```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf95e6b7a

Partition  Boot         Start           End          Size  Id System

/dev/sda1         185,004,540   225,970,289    40,965,750  83 Linux
/dev/sda2    *      3,074,048   185,004,539   181,930,492   7 HPFS/NTFS
/dev/sda3         225,970,290   234,436,544     8,466,255  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="91590796-0392-4948-bf9c-7ae6133139b2" SEC_TYPE="ext2" TYPE="ext3" 
sda2: UUID="127474E77474CECB" LABEL="Vista" TYPE="ntfs" 
sda2/Wubi: UUID="dbb3b2af-def2-480c-890a-cad5fb3fb73b" SEC_TYPE="ext2" TYPE="ext3" 
sda3: UUID="3136f931-e850-4b03-90a7-273face73e8d" TYPE="swap" 

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
/dev/loop1 on /vdisk type ext3 (rw)


==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=127474E77474CECB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.10, kernel 2.6.31-17-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=127474E77474CECB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=127474E77474CECB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=127474E77474CECB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=127474E77474CECB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=127474E77474CECB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=127474E77474CECB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda3
root (hd0,2)
configfile /boot/grub/menu.lst



======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda2/boot.ini: ================================

[operating systems]

[boot loader]

timeout=15


=================== sda2: Location of files loaded by Grub: ===================


  20.6GB: ubuntu/disks/boot/grub/menu.lst
  63.8GB: ubuntu/disks/boot/initrd.img-2.6.31-15-generic
  68.8GB: ubuntu/disks/boot/initrd.img-2.6.31-16-generic
  17.4GB: ubuntu/disks/boot/initrd.img-2.6.31-17-generic
  19.6GB: ubuntu/disks/boot/vmlinuz-2.6.31-15-generic
  56.3GB: ubuntu/disks/boot/vmlinuz-2.6.31-16-generic
  19.7GB: ubuntu/disks/boot/vmlinuz-2.6.31-17-generic

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/sda1 /media/WinRE ntfs-3g defaults,locale=en_GB.UTF-8 0 0
=============================== StdErr Messages: ===============================

umount: /win: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

```
ubuntu@ubuntu:~/Desktop/ms-sys-2.1.4$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf95e6b7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           11517       14066    20482875   83  Linux
/dev/sda2   *         192       11516    90965246    7  HPFS/NTFS
/dev/sda3           14067       14593     4233127+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4192 MB, 4192206848 bytes
2 heads, 63 sectors/track, 64983 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x00056bfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       64984     4093920    b  W95 FAT32

```

---

### Post by erenay on 2010-01-02
OK, it seems like using ms-sys solved my problem: [http://packages.debian.org/etch/ms-sys](http://packages.debian.org/etch/ms-sys)

---

### Post by eyadhafez on 2010-01-08
Please help me with my problem:(

---

