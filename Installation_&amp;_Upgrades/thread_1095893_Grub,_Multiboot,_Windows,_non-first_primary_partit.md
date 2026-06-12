---
title: "Grub, Multiboot, Windows, non-first primary partition, problem"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by munishvit on 2009-03-14
Guys I use Ubuntu 8.04 that I have installed on extended partition. I cleaned my third-primary partition to install Windows, but I don't know how to do that exactly. 
This is how I have done hard-disk partitions:
/dev/hda1	/boot
/dev/hda2	linux-swap
/dev/hda3	for windows
/dev/hda4	extended
/dev/hda5	/
/dev/hda6	/mnt/HDA6
/dev/hda7	/mnt/HDA7

One idea :-k that comes to me is first to make entry in menu.lst file as follows:

title	WindowsXP
	hide (hd0,0)
	hide (hd0,1)	//[COLOR="Red"]Is this entry necessary?[/COLOR]
	unhide (hd0,2)
	rootnoverify (hd0,2)
	chainloader +1
	makeactive	//[COLOR="Red"]What it's use, as (hd0,0) and (hd0,1) are already hidden?[/COLOR]

and then try to boot from this entry and install Windows normally.

> **Edited:** How I was thinking of to get it worked? As there is no already present OS at the partition whose boot sector is being chainloaded. But the execution of this menu entry will make first two primary partitions hidden and the third one unhidden and active. After rebooting, I would be able to install through Widows XP CD if the first-primary partition would have Windows compatiable file-system.

If this is possible and somehow installation gets intrupted in between, will I be able to boot into Ubuntu? or those first two primary parititions will still be hidden.
Does this 'hide' option hides the paritions for only once while booting? 

> **Edited:** Once you make a partition hidden/unhidden/active/unactive it will remain same till the time you deliberately alter its status

Do I need to modify the menu entry of Ubuntu?
	unhide (hd0,0)
	unhide (hd0,1)	//[COLOR="Red"]Is this necessary?[/COLOR]
	unhide (hd0,2)	//[COLOR="Red"]what about this?[/COLOR]
If there would have been another Windows instead of /boot on (hd0,0), how the modifications should be done in the menu entry of this windows?
One more doubt I would like to ask. What if I like to install windows on /dev/hda6 which resides on extended partition? 
Any help would be greatly appreciated.
Thanks in advance...

---

### Post by munishvit on 2009-03-14
No help for so long...I couldn't wait and tried this
> default		saved
timeout		5
fallback	0

# 0th entry
title	Ubuntu 8.04.2, kernel 2.6.24-23-generic
	unhide (hd0,0)
	unhide (hd0,1)
	root	(hd0,0)
	kernel	/vmlinuz-2.6.24-23-generic root=UUID=0730e16b-8ca4-47e8-b373-cb54333f5831 ro quiet
	initrd	/initrd.img-2.6.24-23-generic
	quiet
	savedefault 0

# 1st entry
title	Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
	root	(hd0,0)
	kernel	/vmlinuz-2.6.24-23-generic root=UUID=0730e16b-8ca4-47e8-b373-cb54333f5831 ro single
	initrd	/initrd.img-2.6.24-23-generic

# 2nd entry
title	Ubuntu 8.04.2, memtest86+
	root	(hd0,0)
	kernel	/memtest86+.bin
	quiet

# 3rd entry
title	WindowsXP @ /dev/hda3
	hide (hd0,0)
	hide (hd0,1)
	unhide (hd0,2)
	rootnoverify (hd0,2)
	chainloader +1
	makeactive	
	savedefault fallback
Well when I try to enter through 3rd entry...it fallbacks to 0th...doesn't permit me to install through Windows CD. I found that if I would not have changed the 0th entry, I must have lost GRUB. 
After booting in through Ubuntu I opened terminal and typed:
> sudo grub
grub> hide (hd0,0)
grub> hide (hd0,1)
grub> unhide (hd0,2)
Then I booted again with WinXP in tray. First it gave a one line message (some 'configuring your installation') then screen went blank and nothing happened for long.
What to do now?

---

### Post by munishvit on 2009-03-15
I am very surprised to see. On this forum where people come up so fast to help others, on this thread I am getting no response at all...
I tried by myself, this time I used Ubuntu Live CD...
Although, I already had made my /dev/hda1 (/boot partition) and /dev/hda2 (swap) hidden, I was still not able to install Windows; may be because it could not find hdd.
So, I booted through Ubuntu Live CD. Firstly took the back up of /boot and then formatted first two primary partitions with fat32. Again using grub command, these two partitions were made hidden (Doubt: If you make any partition hidden, second next time when you boot, will it still be hidden?). Then restarted the system.
This time I could install Windows on /dev/hda3. After installation, I again booted through Live disc and made the following changes:
	1. Formatted /dev/hda1 with ext3 and /dev/hda2 with linux-swap and made the swap ON.
	2. Copied grub up to /dev/hda1
	3. Made following changes 0th entry of menu.lst file:
	> title Ubuntu 8.04.2, kernel 2.6.24*23*generic
	      unhide (hd0,0)
	      unhide (hd0,1)
	      root (hd0,0)
	      kernel (hd0,0)/vmlinuz*2.6.24*23*generic root=/dev/hda5 ro quiet
	      initrd (hd0,0)/initrd.img*2.6.24*23*generic
	      quiet
	      savedefault 0
	4. Installed Grub at MRB
	sudo grub
	grub> root (hd0,0)
	grub> setup (hd0)
After restart I logged in into Linux successfully :D but when I tried to boot Windows through Windows-menu in Grub...I got error. :(
> Error 17: Cannot mount selected partition
Fallback made me logged in Ubuntu instead.
Where I went wrong this time???

---

### Post by meierfra. on 2009-03-15
In order to get a clearer picture of your setup, I suggest to boot to  Ubuntu and  download the Boot Info Script to your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by munishvit on 2009-03-16
Thanks for looking at this confusing thread...:)
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/hda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/hdc

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

hda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, hda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       hda2 starts at sector 208845.
    Mounting failed:
mount: /dev/hda2 already mounted or hda2 busy

hda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hda3 hda3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hda3 hda3 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hda3 hda3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hda3 hda3 ntfs-3g force 0 0

hda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

hda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29592959

Partition  Boot         Start           End          Size  Id System

/dev/hda1              16,065       208,844       192,780  83 Linux
/dev/hda2             208,845     1,783,214     1,574,370  82 Linux swap / Solaris
/dev/hda3    *      1,783,215    18,555,074    16,771,860   7 HPFS/NTFS
/dev/hda4          18,555,075    78,140,159    59,585,085   5 Extended
/dev/hda5          18,555,138    37,431,449    18,876,312  83 Linux
/dev/hda6          37,431,513    70,991,234    33,559,722  83 Linux
/dev/hda7          70,991,298    78,140,159     7,148,862  83 Linux


Drive: hdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 728 MB, 728528896 bytes
255 heads, 63 sectors/track, 22 cylinders, total 355727 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: UUID="0b373e5c-8db4-434f-89d2-02cdc5bff377" TYPE="ext3" 
/dev/hda2: SEC_TYPE="msdos" UUID="49BC-D40A" TYPE="vfat" 
/dev/hda3: UUID="5A8814AE88148B21" LABEL="WinXP" TYPE="ntfs" 
/dev/hda5: UUID="0730e16b-8ca4-47e8-b373-cb54333f5831" TYPE="ext3" 
/dev/hda6: UUID="06c46213-d270-43b7-aecb-e4fd3f5f5ab3" TYPE="ext3" 
/dev/hda7: UUID="353c8030-a796-483f-a280-cf515022a7f4" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/hda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/hda1 on /boot type ext3 (rw,relatime)
/dev/hda6 on /mnt/HDA6 type ext3 (rw)
/dev/hda7 on /mnt/HDA7 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/munish/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=munish)


============================= hda1/grub/menu.lst: =============================

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


## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).

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
# kopt=root=UUID=0730e16b-8ca4-47e8-b373-cb54333f5831 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

default		saved
timeout		5
fallback	0
password --md5 $1$zdbpx$hrTJ/dbWdG5TBc0k0SKRU1

# 0th entry
title	Ubuntu 8.04.2, kernel 2.6.24-23-generic
	unhide (hd0,0)
	unhide (hd0,1)
	root	(hd0,0)
	kernel	(hd0,0)/vmlinuz-2.6.24-23-generic root=/dev/hda5 ro quiet
	initrd	(hd0,0)/initrd.img-2.6.24-23-generic
	quiet
	savedefault 0

# 1st entry
title	Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
	root	(hd0,0)
	kernel	(hd0,0)/vmlinuz-2.6.24-23-generic root=/dev/hda5 ro single
	initrd	(hd0,0)/initrd.img-2.6.24-23-generic

# 2nd entry
title	Ubuntu 8.04.2, memtest86+
	root	(hd0,0)
	kernel	(hd0,0)/memtest86+.bin
	quiet

# 3rd entry
title	WindowsXP @ /dev/hda3
	lock
	unhide (hd0,2)
	hide (hd0,0)
	hide (hd0,1)
	rootnoverify (hd0,2)
	makeactive
	chainloader +1	
	savedefault fallback

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== hda1: Location of files loaded by Grub: ===================


    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd.img-2.6.24-23-generic
    .0GB: initrd.img-2.6.24-23-generic.bak
    .0GB: vmlinuz-2.6.24-23-generic

=========================== hda5/boot/grub/menu.lst: ===========================

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


## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).

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
# kopt=root=UUID=0730e16b-8ca4-47e8-b373-cb54333f5831 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

default		saved
timeout		5
fallback	0
password --md5 $1$zdbpx$hrTJ/dbWdG5TBc0k0SKRU1

# 0th entry
title	Ubuntu 8.04.2, kernel 2.6.24-23-generic
	unhide (hd0,0)
	unhide (hd0,1)
	root	(hd0,0)
	kernel	(hd0,0)/vmlinuz-2.6.24-23-generic root=/dev/hda5 ro quiet
	initrd	(hd0,0)/initrd.img-2.6.24-23-generic
	quiet
	savedefault 0

# 1st entry
title	Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
	root	(hd0,0)
	kernel	(hd0,0)/vmlinuz-2.6.24-23-generic root=/dev/hda5 ro single
	initrd	(hd0,0)/initrd.img-2.6.24-23-generic

# 2nd entry
title	Ubuntu 8.04.2, memtest86+
	root	(hd0,0)
	kernel	(hd0,0)/memtest86+.bin
	quiet

# 3rd entry
title	WindowsXP @ /dev/hda3
	lock
	unhide (hd0,2)
	hide (hd0,0)
	hide (hd0,1)
	rootnoverify (hd0,2)
	makeactive
	chainloader +1	
	savedefault fallback

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== hda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for root-drive:
/dev/hda5 / ext3 relatime,errors=remount-ro 0 1
# Entry for boot-drive:
/dev/hda1 /boot ext3 relatime 0 2
# Entry for swap-drive:
/dev/hda2 none swap sw 0 0

#other entries
/dev/hdc /mnt/IMAGE udf,iso9660 user,noauto,exec,utf8 0 0
/dev/hda3 /mnt/HDA3 auto defaults 0 0
/dev/hda6 /mnt/HDA6 ext3 defaults 0 0
/dev/hda7 /mnt/HDA7 ext3 defaults 0 0

=================== hda5: Location of files loaded by Grub: ===================


   9.5GB: boot/grub/menu.lst
   9.5GB: boot/grub/stage2
   9.5GB: boot/initrd.img-2.6.24-23-generic
   9.5GB: boot/initrd.img-2.6.24-23-generic.bak
   9.5GB: boot/vmlinuz-2.6.24-23-generic
   9.5GB: initrd.img
   9.5GB: vmlinuz
```

---

### Post by hichamroudi on 2009-03-16
[http://ubuntuforums.org/showthread.php?t=1096354](http://ubuntuforums.org/showthread.php?t=1096354)

---

### Post by meierfra. on 2009-03-16
I  can't find anything wrong. But all the hiding and unhiding  is unnecessary for booting. So I suggest to remove all "hide" and "unhide" lines.
"savedefault" is also known to cause problems in some rare cases. 

So add the following two items to menu.lst:


title XP (root)
root (hd0,2)
chainloader +1

title XP (rootnoverify)
rootnoverify (hd0,2)
chainloader +1


Try both entries, and report any error messages. If one of them works, you can add the "savedefault"  and "lock"   lines (one at a time) and see whether is still works. But for now I suggest to keep things as simple as possible.

---

### Post by munishvit on 2009-03-16
> **meierfra. said:**
> 
title XP (root)
root (hd0,2)
chainloader +1

title XP (rootnoverify)
rootnoverify (hd0,2)
chainloader +1


I am totally surprised, both Windows entries are working. Thanks a lot.
But some doubts are popping up in my mind, it would be great if you could answer:
1. Why my Windows' menu.lst entry was not working, as Windows has noting to do with (hd0,0) and (hd0,1). Moreover, it should have helped Windows to avoid confusion. (I read it here [http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows))
2. If I would had another Windows at (hd0,1), Would the same menu.lst entries for (hd0,2) have worked?
3. What is use of 'makeactive'?
4. Are 'rootnoverify' and 'root' same, when we are talking about Windows?
5. If I would have installed Windows in (hd0,5) (logical partition in extended partition), would the similar entries (as suggested by you) have worked?
Thanks again for help

---

### Post by dandnsmith on 2009-03-16
For Windows you definitely want *rootnoverify* not *root* - it's to do with the way GRUB works.

I have XP on the PC I'm using at this point in time in hda7 which is, of course, within an extended partition.

When installing Windows, you don't need to hide linux partitions, as the Windows installer will ignore those. You will have to recover the GRUB bootstrap in the first block of the HDD, as Windows **will** overwrite it.

I've never seen a use for the *makeactive* - my experiments suggest that it is never needed in the normal course of events. The one thing I can see for its use is to set the boot flag on a partition (you may need this for Windows, but linux just doesn't care and neither does GRUB).

If you have more than one Windows installation on the HDD, it depends on how you've done it as to what the entries need to be (for XP, I let it organise its own menu for selecting which to use).

HTH

---

### Post by munishvit on 2009-03-16
Thanks :P:P:P dandnsmith for all this explanation. If you don't mind, just clarify one doubt:
Let this be the partition scheme
```
/dev/hda1 /boot
/dev/hda2 Windows XP-1
/dev/hda3 Windows XP-2
/dev/hda4 extended
/dev/hda5 / (Ubuntu)
/dev/hda6 Linux-swap
/dev/hda7 /mnt/HDA7
```
How will you write menu.lst file then?

---

### Post by meierfra. on 2009-03-16
```
Why my Windows' menu.lst entry was not working,
```
I'm not sure. Maybe it was caused by the "unhide (hd0,2)". It might malfunction if your Windows  partition was not hidden at the time.

I suggest  to do some experiments.  Starting with "root (hd0,2), chainloader +1" add all the extra lines you had used. But add one line at a time and see whether you can still boot into Windows after each line you added. This way we will at least know which line of code was the culprit.

 
> If I would had another Windows at (hd0,1), Would the same menu.lst entries for (hd0,2) have worked?

It depends on how the two Windows were install. 

There are three different cases:

1)  Windows on (hd0,1) was installed first and then Windows on (hd0,2).

In this case you would have to use  "root (hd0,1)" and  choosing Windows at the Grub menu will give you a Windows Boot menu, where you can choose between the two Windows.

2)  Windows on (hd0,2) was installed first and then Windows on (hd0,1).

Same as Case 1), except you have to use "root (hd0,2)" in menu.lst.


3)  The two windows are installed in some order, but  the one installed first is hidden while the second one is installed.

In this case you  can boot both Windows directly from the Grub menu. Use two items, one with "root (hd0,1)" and the other with "root (hd0,2)"

---

### Post by munishvit on 2009-03-16
> I suggest  to do some experiments.
For Ubuntu's menu case, following entries doesn't create any problem:
	unhide (hd0,0)
	unhide (hd0,1)
and the Windows' menu doesn't work if 'hide (hd0,0)' is present, rest two are ok.
	hide (hd0,1)
	unhide (hd0,2)
this lefts us only with one WHY?
> There are three different cases:
About dual-windows (on hda1 and hda2) installation, my logics suggest me if one Windows is installed, then we can't install other without hiding first one. But, there won't be any problem if we are going to install one on primary and second on some logical drive of extended partition.
Plz correct me if I am wrong.

---

### Post by meierfra. on 2009-03-16
> and the Windows' menu doesn't work if 'hide (hd0,0)' is present

Very strange.  I'll do some testing myself.

---

### Post by meierfra. on 2009-03-16
> About dual-windows (on hda1 and hda2) installation, my logics suggest me if one Windows is installed, then we can't install other without hiding first one.


Why?  As far as I know, where is no problem installing various  primary Windows. But they will all use  the first  Windows for the boot files.

---

### Post by munishvit on 2009-03-16
> **meierfra. said:**
> Why?  As far as I know, where is no problem installing various  primary Windows. But they will all use  the first  Windows for the boot files.

Ok, if you are that much sure...I accept:popcorn:

Edit:
If you come to know any reason behind (hd0,0) problem, please let us know.

---

### Post by meierfra. on 2009-03-16
I did my own experiment:

I added "hide (hd0,0)" to my windows item in menu.lst. I had no problems booting into Windows. But after reboot I got "Grub Error 17" before the Grub Menu appeared.  Which actually makes sense:  The Boot partition was still hidden at the time of the reboot, so grub stage1.5 was  not able the find grub's stage2 on the boot partition.

But your experience seems to be different. Is there any chance that your Grub Error was not caused by  the current  "hide/unhide" commands,  but by the ones from the previous time you booted?

---

### Post by munishvit on 2009-03-17
Here, you cleared one of my doubts. I always wondered what will happen if I could boot into Windows using hide (hd0,0) and after proper SHUT DOWN, press the POWER button again.

So, grub doesn't unhide it automatically unless you do somehow. 

When I added (hd0,0) to Windows menu, I did used  the fallback mechanism to make it fall to Ubuntu instead where I added unhide (hd0,0) & (hd0,1) already.

```
default		saved
timeout		5
fallback	0
password --md5 $1$zdbpx$hrTJ/dbWdG5TBc0k0SKRU1

# 0th entry
title	Ubuntu 8.04.2, kernel 2.6.24-23-generic
	unhide (hd0,0)
	unhide (hd0,1)
	root	(hd0,0)
	kernel	(hd0,0)/vmlinuz-2.6.24-23-generic root=/dev/hda5 ro quiet
	initrd	(hd0,0)/initrd.img-2.6.24-23-generic
	quiet
	savedefault 0

# 1st entry
title	Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
	root	(hd0,0)
	kernel	(hd0,0)/vmlinuz-2.6.24-23-generic root=/dev/hda5 ro single
	initrd	(hd0,0)/initrd.img-2.6.24-23-generic

# 2nd entry
title	Ubuntu 8.04.2, memtest86+
	root	(hd0,0)
	kernel	(hd0,0)/memtest86+.bin
	quiet

# 3rd entry
title	WindowsXP @ /dev/hda3
	lock
	# hide (hd0,0) //this entry is creating problem
	hide (hd0,1)
	unhide (hd0,2)
	rootnoverify (hd0,2)
	chainloader +1
	makeactive	
	savedefault fallback
```

These are the entries that right now I am using with no problem in booting (Ubuntu and Windows). 

Could there be some hardware issue due to which I am not able to use (hd0,0)?

---

### Post by munishvit on 2009-03-17
I am using only single GRUB, which I have installed on MBR and kept (hd0,0) as /boot. May be problem is arising as I am trying to hide (hd0,0) itself, which is /boot. But before we hit the Windows Menu, the GRUB has already read the /boot files and it appears while GRUB is active it keeps a copy of menu.lst in RAM. If this would not be the case, how come it is able to read the 'fallback' line.
```
title	WindowsXP @ /dev/hda3
	lock
	# hide (hd0,0) //this entry is creating problem
	hide (hd0,1)
	unhide (hd0,2)
	rootnoverify (hd0,2)
	chainloader +1
	makeactive	
	savedefault fallback
```

---

### Post by munishvit on 2009-03-22
> **meierfra. said:**
> ```
Why my Windows' menu.lst entry was not working,
```

It depends on how the two Windows were install. 

There are three different cases:

1)  Windows on (hd0,1) was installed first and then Windows on (hd0,2).

In this case you would have to use  "root (hd0,1)" and  choosing Windows at the Grub menu will give you a Windows Boot menu, where you can choose between the two Windows.

2)  Windows on (hd0,2) was installed first and then Windows on (hd0,1).

Same as Case 1), except you have to use "root (hd0,2)" in menu.lst.


3)  The two windows are installed in some order, but  the one installed first is hidden while the second one is installed.

In this case you  can boot both Windows directly from the Grub menu. Use two items, one with "root (hd0,1)" and the other with "root (hd0,2)"

I was wrong. But, now I have got your point. Thanks a lot

---

