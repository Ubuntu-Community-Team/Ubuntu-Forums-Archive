---
title: "Cannot Access and/or Restore GRUB"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by Tindytim on 2009-09-08
I semi-recently installed Windows 7 along side my Ubuntu Studio 9.04 x64 boot, having left the first partition open for it. After the initial install GRUB was, as I expected, unaccessable. I attempted to restore it using the LiveCD, and ran into some issues (If I remember correctly, it didn't work at all). I blew it off, figuring I'd deal with it when I was ready to go back to Ubunutu, after fleshing out my experience with 7. Well, that time is now.

I booted up the LiveCD (9.04 x64), attempted to restore GRUB (as detailed in [this thread]("http://ubuntuforums.org/showthread.php?t=224351")), booted up, and I get Windows 7. I attempted this multiple times before using EasyBCD to remove the Windows 7 bootloader. I boot up again, and I get an "NTLDR is missing" error. So I attempt to restore GRUB again, I boot up, and I get the exact same error. After a few more attempts, I try installing Ubuntu 9.04 on another partition on the first hard drive (where all my OSes are installed), and it installs without a hitch. I boot up, "NTLDR is missing".

I currently have only 3 partitions on my first hard drive with no unallocated space (Windows 7, swap, Ubuntu 9.04). Any help would be greatly appreciated.

---

### Post by presence1960 on 2009-09-08
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by stlsaint on 2009-09-08
considering ntldr is a windows issue i think that you have your bios set to boot your windows hdd and it prolly got messed up when you tried removing bootloader with easybcd ...can you check this please.

---

### Post by Tindytim on 2009-09-09
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 180202038 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #175654710 on boot drive #1
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e5d0f

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   169,357,229   169,357,167   7 HPFS/NTFS
/dev/sda2         169,357,230   175,654,709     6,297,480  82 Linux swap / Solaris
/dev/sda3    *    175,654,710   490,223,474   314,568,765  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6e1605ad

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   490,223,474   490,223,412   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x57435743

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="121C66061C65E4E7" TYPE="ntfs" 
/dev/sda2: UUID="d1cd8cc9-a299-48b3-9622-9294eac37faa" TYPE="swap" 
/dev/sda3: UUID="6b425586-8f00-4eaf-9a3e-2fd9dc0e6003" TYPE="ext4" 
/dev/sdb1: UUID="665044ED5044C591" LABEL="CRAP" TYPE="ntfs" 
/dev/sdc1: UUID="FC586AE4586A9CE0" LABEL="Media" TYPE="ntfs" 

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
timeout		3

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
# kopt=root=UUID=6b425586-8f00-4eaf-9a3e-2fd9dc0e6003 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6b425586-8f00-4eaf-9a3e-2fd9dc0e6003

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
# defoptions=quiet splash vga=795

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
uuid		6b425586-8f00-4eaf-9a3e-2fd9dc0e6003
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6b425586-8f00-4eaf-9a3e-2fd9dc0e6003 ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		6b425586-8f00-4eaf-9a3e-2fd9dc0e6003
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6b425586-8f00-4eaf-9a3e-2fd9dc0e6003 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		6b425586-8f00-4eaf-9a3e-2fd9dc0e6003
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
root	        (hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda3 during installation
UUID=6b425586-8f00-4eaf-9a3e-2fd9dc0e6003  /               ext4         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda2 during installation
UUID=d1cd8cc9-a299-48b3-9622-9294eac37faa  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /media/sdb1     ntfs         defaults                    0  0  
/dev/sdc1                                  /media/Media    ntfs         nls=iso8859-1,umask=000     0  0  

=================== sda3: Location of files loaded by Grub: ===================


 109.1GB: boot/grub/menu.lst
  92.2GB: boot/grub/stage2
 110.2GB: boot/initrd.img-2.6.28-11-generic
 107.0GB: boot/initrd.img-2.6.28-13-generic
 106.9GB: boot/initrd.img-2.6.28-14-generic
 100.7GB: boot/initrd.img-2.6.28-15-generic
 110.2GB: boot/initrd.img-2.6.28-3-rt
  92.2GB: boot/vmlinuz-2.6.28-11-generic
  90.7GB: boot/vmlinuz-2.6.28-13-generic
  90.2GB: boot/vmlinuz-2.6.28-14-generic
 107.0GB: boot/vmlinuz-2.6.28-15-generic
 107.2GB: boot/vmlinuz-2.6.28-3-rt
 100.7GB: initrd.img
 106.9GB: initrd.img.old
 107.0GB: vmlinuz
  90.2GB: vmlinuz.old
```

> **stlsaint said:**
> considering ntldr is a windows issue i think that you have your bios set to boot your windows hdd and it prolly got messed up when you tried removing bootloader with easybcd ...can you check this please.
> **Tindytim said:**
> I try installing Ubuntu 9.04 on another partition on the first hard drive (where all my OSes are installed)
> **Tindytim said:**
> I currently have only 3 partitions on my first hard drive with no unallocated space (Windows 7, swap, Ubuntu 9.04). Any help would be greatly appreciated.

---

### Post by presence1960 on 2009-09-09
This is going to be a two part fix. First you need to restore windows 7 bootloader. Then you will restore GRUB.

You will need your Windows 7 install DVD. Reboot with the DVD in the drive. Go into BIOS and ensure that your disk with Ubuntu & Windows 7 is set to boot first in the hard disk boot order. This is critical! Then go [here]("http://ubuntuforums.org/showthread.php?t=1014708") and follow the instructions for Vista. When complete reboot without the Windows DVD and you should boot right into Windows 7. if successful move on.

Next you will boot off the Ubuntu Live CD. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,2)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,2)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

**In #6 use setup (hd0)**

```
You should be good to go!

P.S. Stay away from neosmart Easy BCD. Use GRUB it is way more configurable and can do way more than Easy BCD.

---

### Post by sahabcse on 2009-09-09
follow below url for fixing the grub issue

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

---

### Post by Tindytim on 2009-09-09
> **presence1960 said:**
> This is going to be a two part fix. First you need to restore windows 7 bootloader. Then you will restore GRUB.
Didn't help, it restored the Windows 7 bootloader, but I still cannot restore GRUB. It's no different then when I had Windows 7 working anyway.

> **presence1960 said:**
> P.S. Stay away from neosmart Easy BCD. Use GRUB it is way more configurable and can do way more than Easy BCD.
EasyBCD isn't a bootloader, it's a utility to configure the default Vista/7 bootloader, and I wasn't using it to change any settings, just uninstall the bootloader.

> **sahabcse said:**
> follow below url for fixing the grub issue

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)
If you'll note what I said in my post
> **Tindytim said:**
> I booted up the LiveCD (9.04 x64), attempted to restore GRUB (as detailed in [this thread]("http://ubuntuforums.org/showthread.php?t=224351")), booted up, and I get Windows 7.
I've done exactly that multiple times. I've memorized the process since I often like to try various different OSes, on multiple systems.

I've run out of ideas, My only options appears to be moving all my data to an external and reformatting.

---

### Post by Tindytim on 2009-09-10
I haven't found any solutions, but is there a way to get a fresh install of GRUB?

---

### Post by presence1960 on 2009-09-10
I am looking over the output from your boot info script again.

> I currently have only 3 partitions on my first hard drive with no unallocated space (Windows 7, swap, Ubuntu 9.04). Any help would be greatly appreciated.

Something is messed up with your installations because the boot info output reports that you have Windows Vista with XP boot sector, swap and ubuntu on that partition.

It also reports that GRUB is installed in the MBR of sda, but looks to partition #5, which does not exist. If you are booting from sda (which I doubt) you would receive a GRUB error.

here is why I doubt you are booting from sda. When you boot you get the windows bootloader. According to the output from the script windows is installed on MBR of sdc. if you look further ar the sdc1 partition the windows files needed to boot from that partition are incomplete. This leads me to believe you have the sdc disk first in the boot order in BIOS. it has windows on MBR and the boot files required to boot Windows are incomplete on partition sdc1. As a matter of fact ntldr is not listed on sdc1 which is why you are getting that error. 

Go in BIOS and check that the sda disk is set to boot first in the hard disk boot order.

P.S. I know windows 7 is listed as Vista. I tried windows 7 for a while.

---

### Post by Tindytim on 2009-09-10
Thanks!

I was unaware that an OS could change my boot priority, I learned something new today. Thanks everyone!

---

### Post by presence1960 on 2009-09-10
> **Tindytim said:**
> Thanks!

I was unaware that an OS could change my boot priority, I learned something new today. Thanks everyone!

Glad you got it working! Enjoy Ubuntu.

---

