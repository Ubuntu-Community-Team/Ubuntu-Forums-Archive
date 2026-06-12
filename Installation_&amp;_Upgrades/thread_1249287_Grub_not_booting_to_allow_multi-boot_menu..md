---
title: "Grub not booting to allow multi-boot menu."
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by Officer Dibble on 2009-08-25
Hi,

I recently upgraded my motherboard to an Asrock N68-S. My Grub menu no longer appears and my system only boots into XP unless I use the SuperGrub disk.

I've tried using the SuperGrub disk to fix this, but whatever it says it has done, my system doesn't seem to see it that way and just continues to boot into XP directly.

I can boot into Ubuntu using the Supergrub disk, but I don't want to have to do that forever.

Any advice welcome,

Thanks.

---

### Post by louieb on 2009-08-25
How many hard drives? Have you tried changing the boot order of the drives?

---

### Post by Officer Dibble on 2009-08-25
> **louieb said:**
> How many hard drives? Have you tried changing the boot order of the drives?

There are two drives and Ubuntu is on the second partition of the second drive.

Supergrub sees it and displays the correct information, and has several times said that it has successfully configured the MBR.

At the moment I am still running 7.10, the prospect of backing everything up for a installation of a newer version of Ubuntu isn't part of my busy schedule at the moment - but if it is necessary, (which I don't see why it would be) then I'll squeeze it into a time-slot somewhere.

This issue has only arisen since I have changed motherboard, and in XP changed my anti-virus to Avast. I didn't need to reinstall XP or Ubuntu for any of these upgrades.

I can't find any settings in the motherboard BIOS that would block the installation, running or config of Grub, unless there is something obvious I missed.

Thanks for jumping in here to help, any advice will be tried.

---

### Post by presence1960 on 2009-08-25
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by louieb on 2009-08-25
> **Officer Dibble said:**
> Supergrub sees it and displays the correct information, and has several times said that it has successfully configured the MBR.
 

Are the drives sata (narrow cable to motherboard) or pata (wide flat cable) or a mix?  

Each drive has an MBR seems yours is booting  to the drive that points to Windows in its MBR. Try changing the boot order.   Most modern PCs have the option to select which hard drive to boot.  

Something else beside the motherboard changed - boot order of your hard drives seems to be the obvious.


lol - hi presence1960 - yes do run the script he asked for - information provided by the script will tell us if my boot order guess is right.

---

### Post by presence1960 on 2009-08-25
> **louieb said:**
> Are the drives sata (narrow cable to motherboard) or pata (wide flat cable) or a mix?  

Each drive has an MBR seems yours is booting  to the drive that points to Windows in its MBR. Try changing the boot order.   Most modern PCs have the option to select which hard drive to boot.  

Something else beside the motherboard changed - boot order of your hard drives seems to be the obvious.


lol - hi presence1960 - yes do run the script he asked for - information provided by the script will tell us if my boot order guess is right.

Hi louieb- how you making out?

You are probably correct about the boot order. I like to use the script to see their exact setup.

---

### Post by Officer Dibble on 2009-08-25
This isn't going to be straightforward is it... this is what I get when I enter that line from both the installed Ubuntu and the live CD.

> 
No such file or directory

This is what I typed character for character:

sudo bash ~/Desktop/boot_info_script*.sh

Thanks for your patience here. :-)

---

### Post by Officer Dibble on 2009-08-25
Okay, here we have it... I downloaded the script-doo-daa and then ran the commmand line thingy you suggested and this is the "Result.txt" file you were looking for:

EDIT:

Ah... if my eyes don't deceive me, Grub is being put on the wrong partition... I seem to remember have a problem like this many moons ago.


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/hda
 => Grub0.97 is installed in the MBR of /dev/hdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

hda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, hda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

hdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

hdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43014300

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63    73,400,984    73,400,922   7 HPFS/NTFS
/dev/hda2          73,400,985   312,576,704   239,175,720   5 Extended
/dev/hda5          73,401,048   312,576,704   239,175,657   7 HPFS/NTFS


Drive: hdb ___________________ _____________________________________________________

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfde8d81

Partition  Boot         Start           End          Size  Id System

/dev/hdb1                  63   119,041,649   119,041,587   7 HPFS/NTFS
/dev/hdb2    *    119,041,650   158,015,339    38,973,690  83 Linux
/dev/hdb3         158,015,340   160,071,659     2,056,320   5 Extended
/dev/hdb5         158,015,403   160,071,659     2,056,257  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/hda1: UUID="DABCCA24BCC9FB51" TYPE="ntfs" 
/dev/hda5: UUID="98F8E904F8E8E18C" LABEL="Data" TYPE="ntfs" 
/dev/hdb1: UUID="987C47DA7C47B234" LABEL="60GB" TYPE="ntfs" 
/dev/hdb2: UUID="982ff0d1-a589-4510-a392-945a314690e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/hda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hdb2 on /media/disk-1 type ext3 (rw,nosuid,nodev)


================================ hda1/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== hdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== hdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=982ff0d1-a589-4510-a392-945a314690e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=a05086be-9702-4635-b33c-26ac36c1ae5d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== hdb2: Location of files loaded by Grub: ===================


  66.6GB: boot/grub/menu.lst
  65.4GB: boot/grub/stage2
  77.6GB: boot/initrd.img-2.6.22-14-generic
  67.7GB: boot/initrd.img-2.6.22-14-generic.bak
  65.7GB: boot/initrd.img-2.6.22-15-generic
  65.7GB: boot/initrd.img-2.6.22-15-generic.bak
  66.8GB: boot/initrd.img-2.6.22-16-generic
  66.8GB: boot/initrd.img-2.6.22-16-generic.bak
  67.6GB: boot/vmlinuz-2.6.22-14-generic
  65.6GB: boot/vmlinuz-2.6.22-15-generic
  66.5GB: boot/vmlinuz-2.6.22-16-generic
  66.8GB: initrd.img
  65.7GB: initrd.img.old
  66.5GB: vmlinuz
  65.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sda sdb sdc sdd 
```

---

### Post by louieb on 2009-08-25
> 
 => Windows is installed in the MBR of /dev/hda
 => Grub0.97 is installed in the MBR of /dev/hdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.


and from your /boot/grub/menu.lst
```

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

looks like I was right about the boot order. But it also looks like your menu.lst is setup for the boot order being the way it is now. and won't work if switched. 

Next guess : if you put grubs stage1 code in the MBR of hda it should work.
```
sudo grub
```
at the grub prompt
```

find /boot/grub/stage2

```
should return (hd1,1) if it does

```

root (hd1,1)
setup (hd0)
quit

```
if not then I'm the monkeys uncle. and I'm out of ideas.

---

### Post by presence1960 on 2009-08-25
> **louieb said:**
> and from your /boot/grub/menu.lst
```

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

looks like I was right about the boot order. But it also looks like your menu.lst is setup for the boot order being the way it is now. and won't work if switched. 

Next guess : if you put grubs stage1 code in the MBR of hda it should work.
```
sudo grub
```
at the grub prompt
```

find /boot/grub/stage2

```
should return (hd1,1) if it does

```

root (hd1,1)
setup (hd0)
quit

```
if not then I'm the monkeys uncle. and I'm out of ideas.

That looks good louieb. 

Or he can just switch the boot order of the disks in BIOS so hdb boots first. Then he wiill have to change the (hdx,y) in the windows entry of menu.lst to (hd1,0)

Either way will work. That's another reason I love Linux there are usually more than one way to accomplish the same task.

---

### Post by Officer Dibble on 2009-08-25
You guys are great, many thanks for your help, you certainly know your stuff... and you're really friendly with it too.

There's a T shirt logo... "Ubuntu people are really nice" :)

I'll follow through on your suggestion and then report it solved.

Many thanks again!

---

### Post by Officer Dibble on 2009-09-08
Okay... there's still a problem here. :(

After I change grub it locks up at this point. (See attached image)

Anybody know what's up here, please?

---

### Post by presence1960 on 2009-09-08
> **Officer Dibble said:**
> Okay... there's still a problem here. :(

After I change grub it locks up at this point. (See attached image)

Anybody know what's up here, please?
 why are you changing GRUB, I thought it was working? What are the commands that precipitated all those lines from the top of your screen shot to near the bottom?
 let us know exactly what you are doing and why.

---

### Post by Officer Dibble on 2009-09-08
> **presence1960 said:**
> why are you changing GRUB, I thought it was working? What are the commands that precipitated all those lines from the top of your screen shot to near the bottom?
 let us know exactly what you are doing and why.

I was hoping that the title of this thread and the ongoing discussion would have explained this. GRUB isn't booting, it's just going straight into XP.

I've tried to help GRUB find the Ubuntu partition but that has caused the freeze I have described here. (Previously I could boot into Ubuntu using the Ubuntu CD) The conclusion reached in this thread was that GRUB was looking in the wrong place to boot Ubuntu. I've tried to redirect it by editing GRUB via Supergrub.

Does this help?

---

### Post by presence1960 on 2009-09-08
I need to see your exact setup & boot process. Do this:

Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

P.S. I know you did it a week back, but I want to see if your fiddling has changed anything.

---

### Post by stlsaint on 2009-09-08
tho you already posted the script results...now that you have changed some things we need to see whats new and causing non-boot!

---

### Post by Officer Dibble on 2009-09-08
> **presence1960 said:**
> I need to see your exact setup & boot process. Do this:

Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

P.S. I know you did it a week back, but I want to see if your fiddling has changed anything.

Fiddling?... tsk.... :)

Okay, I've got to disappear for an hour or two, so I'll drop it here about 21:30'ish  (GMT) if any are still around then.

Thanks for your patience.

---

### Post by presence1960 on 2009-09-08
> **Officer Dibble said:**
> Fiddling?... tsk.... :)

Okay, I've got to disappear for an hour or two, so I'll drop it here about 21:30'ish  (GMT) if any are still around then.

Thanks for your patience.

I didn't mean it in a bad way...:)

---

### Post by Officer Dibble on 2009-10-11
Hi,

Had a bout of ill health, sorry to take so long getting to this.

After looking at this could you tell me how to use Supergrub, or something as good as or better, that would fix it, please?

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x43014300

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    73,400,984    73,400,922   7 HPFS/NTFS
/dev/sda2          73,400,985   312,576,704   239,175,720   5 Extended
/dev/sda5          73,401,048   312,576,704   239,175,657   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfde8d81

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   119,041,649   119,041,587   7 HPFS/NTFS
/dev/sdb2    *    119,041,650   158,015,339    38,973,690  83 Linux
/dev/sdb3         158,015,340   160,071,659     2,056,320   5 Extended
/dev/sdb5         158,015,403   160,071,659     2,056,257  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="DABCCA24BCC9FB51" TYPE="ntfs" 
/dev/sda5: UUID="98F8E904F8E8E18C" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: UUID="987C47DA7C47B234" LABEL="60GB" TYPE="ntfs" 
/dev/sdb2: UUID="982ff0d1-a589-4510-a392-945a314690e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" 

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
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

C:\ubnldr.mbr="Auto Super Grub Disk"


=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=982ff0d1-a589-4510-a392-945a314690e1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=a05086be-9702-4635-b33c-26ac36c1ae5d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  66.6GB: boot/grub/menu.lst
  65.4GB: boot/grub/stage2
  77.6GB: boot/initrd.img-2.6.22-14-generic
  67.7GB: boot/initrd.img-2.6.22-14-generic.bak
  65.7GB: boot/initrd.img-2.6.22-15-generic
  65.7GB: boot/initrd.img-2.6.22-15-generic.bak
  66.8GB: boot/initrd.img-2.6.22-16-generic
  66.8GB: boot/initrd.img-2.6.22-16-generic.bak
  67.6GB: boot/vmlinuz-2.6.22-14-generic
  65.6GB: boot/vmlinuz-2.6.22-15-generic
  66.5GB: boot/vmlinuz-2.6.22-16-generic
  66.8GB: initrd.img
  65.7GB: initrd.img.old
  66.5GB: vmlinuz
  65.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by presence1960 on 2009-10-11
You are booting into windows because your 160 Gb disk (sda) is first in hard disk boot order in BIOS and it has windows on MBR. GRUB is installed on MBR of your 82 GB disk (sdb). To get GRUB at boot you need to set sdb (82 GB) as first hard disk to boot in BIOS. Here is where I get this info from your posted output of the script you ran:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
```



When you reboot go into BIOS and set the 82 GB disk (sdb) as first boot in the hard disk boot order. This will bring up GRUB which is installed on MBR of that disk. Save changes to CMOS and exit BIOS. Boot into Ubuntu and open a terminal when desktop loads & run this command: ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

scroll down to windows entry at bottom and edit the windows entry to look exactly like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		        Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map                     (hd0) (hd1)
map                     (hd1) (hd0)
chainloader	        +1

```
Click Save on toolbar, close file. Reboot and you should now also be able to boot into windows from GRUB.

Sorry to hear about your illness, hope all is better now.

---

### Post by rreese6 on 2009-10-11
+2 presence1960
For your patience and determination.

---

### Post by oldfred on 2009-10-11
[http://ubuntuforums.org/showthread.php?t=1288713](http://ubuntuforums.org/showthread.php?t=1288713)

OP started new thread, I think I tried to tell him the same thing presence said, but as usual presence is a little more clear in explaining things.

---

### Post by rreese6 on 2009-10-11
> **oldfred said:**
> [http://ubuntuforums.org/showthread.php?t=1288713](http://ubuntuforums.org/showthread.php?t=1288713)

OP started new thread, I think I tried to tell him the same thing presence said, but as usual presence is a little more clear in explaining things.

I felt presense 1960 was very clear and lead to the final solution, unfortunately there is that "migration group" that want nothing more than "Click Next"...it is difficult for some to embrace freedom after being a salve to an OS for so long.

I imagine the OP is still hoping for a point and click solution.
But if the OP doesn't understand, I hope they know all they have to do is ask us to explain things to them...and of course there is always RTFM.

---

### Post by Officer Dibble on 2009-10-12
Presence1960, thank you ever so much for this explanation. You have genuinely demonstrated the spirit of Ubuntu. :)

I started a new thread after adding to this one, and before Presence1960 made a response to this one. My experience dictated that people are more readily inclined to jump on a new thread, and in many cases prefer to avoid lengthy protracted threads because of the catch-up involved.

Yep, I am more dependent on point and click these days, unfortunately my health and powers of concentration aren't what they used to be. I used to be able to develop in 5 completely different programming languages. I reveled in robotics, and adapting well known software packages for the disabled... man, their need for point and click would have really riled the backs of certain contributors to this thread.

Anyway, I'll try to slowly work my way through Presence1960's solution here, albeit, I was hoping there would be a easier way of doing this.

Thanks to all. :)

---

### Post by Officer Dibble on 2009-10-12
Presence1960, I'm sorry to say that this hasn't worked. I made the changes in the BIOS as you suggested. It does boot to the Grub menu, but it will not boot into either Ubuntu or Windows.

With Ubuntu it reports error 17, and with XP it reports 'Can't find NTLR'.

Why isn't Supergrub fixing this either?

If I backed up my Home folder, would that then allow me to reinstall Ubuntu without losing anything? I only want to do this as an absolute last resort. I hate the defeatism of reinstalls...

---

### Post by presence1960 on 2009-10-12
> **Officer Dibble said:**
> Presence1960, I'm sorry to say that this hasn't worked. I made the changes in the BIOS as you suggested. It does boot to the Grub menu, but it will not boot into either Ubuntu or Windows.

With Ubuntu it reports error 17, and with XP it reports 'Can't find NTLR'.

Why isn't Supergrub fixing this either?

If I backed up my Home folder, would that then allow me to reinstall Ubuntu without losing anything? I only want to do this as an absolute last resort. I hate the defeatism of reinstalls...

I just noticed you are running Ubuntu 7.10 which is no longer supported. I would install either 8.04 which is an LTS or 9.04.

I can help you fix 7.10, but in my opinion that will be an exercise in futility as 7.10 is no longer supported. But if you insist post back.

---

### Post by Officer Dibble on 2009-10-12
At the moment it would be easier to fix this than to reinstall, please forgive me if that sounds as illogical as it does to me.

What may be confusing matters about the config of the drives is that I've had a fiddle with it in Supergrub, but please trust me on this, wear sunscreen, oh, and in the BIOS everything is as it should be regarding the boot sequence of the drives.

Thank you for your immense patience.

---

### Post by wilee-nilee on 2009-10-12
> **presence1960 said:**
> I just noticed you are running Ubuntu 7.10 which is no longer supported. I would install either 8.04 which is an LTS or 9.04.

I can help you fix 7.10, but in my opinion that will be an exercise in futility as 7.10 is no longer supported. But if you insist post back.

excellent idea, I see that the OP post that this is not an option, which is to bad because the later releases have safer more robust all around programs.

---

### Post by Officer Dibble on 2009-10-12
[QUOTE=wilee-nilee;8094752]excellent idea, I see that the OP post that this is not an option, which is to bad because the later releases have safer more robust all around programs.[/QUOTE

I can appreciate what you are saying here, but the problem is not with Ubuntu 7.10, it's with Grub, which could happen with any version of Ubuntu.

If nobody wants to help fix Grub, then I can appreciate the technical difficulties it may pose.

---

### Post by presence1960 on 2009-10-12
Boot from the Live CD. When the desktop loads Open a file browser from Places> Computer, Highlight your Ubuntu root partition on the left pane to mount it.

Once mounted (you will see the directories in that partition on the right) , open a terminal and run ```
gksu nautilus
```

When nautilus opens highlight your Ubuntu root partition and then open boot directory, then open grub directory then open menu.lst. change your OS section at the bottom to this:
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-16-generic

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=982ff0d1-a589-4510-a392-945a314690e1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1
```

Click Save on toolbar, close file. Close both file browsers and reboot.

---

### Post by wilee-nilee on 2009-10-12
> **Officer Dibble said:**
> [quote=wilee-nilee;8094752]excellent idea, I see that the OP post that this is not an option, which is to bad because the later releases have safer more robust all around programs.[/QUOTE

I can appreciate what you are saying here, but the problem is not with Ubuntu 7.10, it's with Grub, which could happen with any version of Ubuntu.

If nobody wants to help fix Grub, then I can appreciate the technical difficulties it may pose.

 Yes but a fresh install would fix all your problems your a month into this problem seems like a waste of time. Also if you had grub2 installed all you would have to do is run sudo update-grub and your problems would be over.

---

### Post by Officer Dibble on 2009-10-13
Presence1960, you have been incredibly helpful. However awkward I may have seemed please don't let it detract from the immense appreciation I have for the help you've given.

wilee-nilee, I never knew about Grub2. I haven't been purposely difficult, but recalling some of the things I have said I realise now how awkward I was being without realising it, but it wasn't purposely. So, I'm very sorry.

If I can't get this to work then I'll just go for the reinstall sometime. Thanks for your help all. :)

---

### Post by presence1960 on 2009-10-13
> **Officer Dibble said:**
> Presence1960, you have been incredibly helpful. However awkward I may have seemed please don't let it detract from the immense appreciation I have for the help you've given.

wilee-nilee, I never knew about Grub2. I haven't been purposely difficult, but recalling some of the things I have said I realise now how awkward I was being without realising it, but it wasn't purposely. So, I'm very sorry.

If I can't get this to work then I'll just go for the reinstall sometime. Thanks for your help all. :)

Don't apologize, we all had to start at the beginning, so you are right where you are supposed to be. If you need more help post back. But booting from the Live CD and editing menu.lst by changing Ubuntu & windows as I suggested should get you booting into Ubuntu & windows from the GRUB menu.

---

### Post by wilee-nilee on 2009-10-13
> **presence1960 said:**
> Don't apologize, we all had to start at the beginning, so you are right where you are supposed to be. If you need more help post back. But booting from the Live CD and editing menu.lst by changing Ubuntu & windows as I suggested should get you booting into Ubuntu & windows from the GRUB menu.

 I agree with this, presence is the most knowledgeable person helping you so follow his lead and everything will be fixed in the end. Hopefully you can get your original setup restored and then you can go from there.

---

