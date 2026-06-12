---
title: "Grub error 13 on a dual-boot XP install attempt"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by Help A Fool on 2009-07-15
Hello Everyone,

I am very new to Ubuntu so please bear with...

I have an old Athlon XP machine that I am trying to use as a dual-boot system. In preparing for this setup I read that it is easier to install XP first and then Ubuntu, so that is what I have attempted.

The machine has three physical hard drives: one 160GB Hitachi pata drive (for the dual-boot), and two 80GB WD800 sata drives setup for raid-0; I think the presence of these two drives is what is affecting the end result.

...

Please note that I've done the below procedure a few times now... I do know that I could have just done it once and repaired the grub boot settings or the MBR or whatever else is going wrong, but I have a compulsive need to know how to do this right and clean  the first time. Sorry.

...

Anyway, I boot the XP CD and add an 80GB partition to my unpartitioned 160GB drive, format with NTFS and install XP. With XP in a very rough, but installed state, I restart and boot from the Ubuntu Live CD and this is where I am having troubles.

At stage 4 of 7 I specify that I want to manually partition my drive (because I want to break-up the Linux partition structure) whereupon I am greated with the partition manager and the three drives: sda, sdb and sdc. Sda and sdb are my two sata drives and are identified properly, and sdc - which I thought would be hda - is my 160GB pata drive with the 80GB XP NTFS partition (primary 1), and about 75GB of free space to install Ubuntu.

So I go about partitioning Ubuntu as follows on the 160GB pata drive:

primary 2, 256MB, ext3, /boot
logical 5, 2GB, ext 4, /
logical 6, 32GB, ext4, /usr
logical 7, 2GB, swap
logical 8, 2GB, ext4, /tmp
logical 9, 6GB, ext4, /var
logical 10, ~29GB, ext4, /home

That looks okay enough, right? So I then complete the user stuff, and at stage seven go into the advanced options and have currently specified the /boot partition on sdc to install the bootloader, but that isn't working to boot XP either. 

On a reboot after installing Ubuntu and at the grub bootloader I get the aforementioned error 13 if I select to boot XP. If I boot Ubuntu and install gparted I have noticed that I have a 'boot' flag on sda (one of my two raid drives) as well as a 'boot' flag on sdc, /boot partition. I think that grub is getting confused by the presence of the two sata drives and misplacing the 'boot' flag. If I take the 'boot' flag off sda and put it on sdc, partition 1 (NTFS, XP) then XP will boot but I don't get grub and the option to boot Ubuntu. If I put the 'boot' flag on the sdc /boot partition then grub loads but I again get error 13 trying to boot XP.

I am sorry for the long tale, but I really need some help to do steps 4 and 7 of the Ubuntu installation cleanly, and know where I am going wrong with this folly.

Thanks for your time.

---

### Post by Mark Phelps on 2009-07-15
Are you installing from the destktop CD or the alternate CD?  I believe that you have to use the alternate CD to utilize RAID.

---

### Post by ronparent on 2009-07-15
I am having a bit of difficulty following your post. First clarify that sdc is set as the first drive to boot to in bios. The presence of the raid array and the boot flags is otherwise irrelevant.

When the boot order is shuffled in bios grub often is confused. To put thing in order we might try a grub rewrite. Try this by booting to the live cd. From a terminal enter:

**sudo grub**

and from the grub prompt enter:

**find /boot/grub/stage1**

the output will tell your ubuntu location (hdx,y) in grub terms.

Enter that location as presented by the output above in this command:

**root (hdx,y)**

and enter:

**setup (hdx)**

If on reboot all is well then you are done. Otherwise we may have to search for another answer.

---

### Post by Help A Fool on 2009-07-15
To Mark Phelps:

I am using the Desktop CD to install Ubuntu. I was going to reconfigure and reformat the RAID array as a striped NTFS partition after XP was fully working, but it's to be used only by XP. Do you foresee any issues with this setup and Ubuntu?

To ronparent:

I am sorry for being somewhat vague. I am booting from 'sdc' (HDD-0, or the Primary Master PATA drive), but I am having some difficulty understanding how grub might be interpreting the BIOS' boot settings... they are as below:

SATA & SCSI Boot Order [SATA,SCSI]
First Boot Device [HDD-0] * changes to [CD-ROM] when installing an OS.
Second Boot Device [Disabled]
Third Boot Device [Disabled]
Boot Other Device [Disabled]

As the Ubuntu partitioner is interpreting all three devices as being SCSI (address-wise) and naming them 'sda' (SATA-0), 'sdb' (SATA-1) and 'sdc' (HDD-0) should I maybe reverse the SATA & SCSI Boot Order as described above?

I have tried the grub rewrite two ways: first from the Live CD as you suggested; and then using gparted to move the boot flag from the XP NTFS partition (to boot XP) to the Ubuntu ext3 /boot partition, and then booting Ubuntu off the hard drive. Either way I get "Error Code 15: File Not Found".

What am I doing wrong in the installation part of this procedure? That has me more perplexed than the issue of fixing the boot loader problem after installation.

Thanks.

---

### Post by Help A Fool on 2009-07-16
Hmmm...

The problem definitely appears to be with grub, as it's way of naming hard drives seems to differ slightly from the way linux names hard drives. It would appear that sda, sdb and sdc are identified by grub as hd0, hd1 and hd2, respectively. 

So on stage 7 of the installation I should specify to install the boot loader to hd2 as opposed to the default hd0... am I right?

Anyone? :)

Thanks.

---

### Post by Help A Fool on 2009-07-16
Here are the contents of my menu.lst, device.map and fstab files along with an fdisk -l command return.

_menu.lst_

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        31382542-8625-4918-8efa-e486cce2d274
kernel        /vmlinuz-2.6.28-11-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro quiet splash vga=788 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        31382542-8625-4918-8efa-e486cce2d274
kernel        /vmlinuz-2.6.28-11-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        31382542-8625-4918-8efa-e486cce2d274
kernel        /memtest86+.bin
quiet

---

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

[U]device.map

[/U](hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc[U]

fstab[/U]

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc3 during installation
UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdc2 during installation
UUID=31382542-8625-4918-8efa-e486cce2d274 /boot           ext3    relatime        0       2
# /home was on /dev/sdc9 during installation
UUID=06e4b3bd-d027-4441-ad2c-36280d827a9b /home           ext4    relatime        0       2
# /tmp was on /dev/sdc7 during installation
UUID=9838c874-aeba-4803-95e2-b3cce3b265fb /tmp            ext4    relatime        0       2
# /usr was on /dev/sdc5 during installation
UUID=bc8560d6-5b03-42fe-889c-57f7068d300b /usr            ext4    relatime        0       2
# /var was on /dev/sdc8 during installation
UUID=9020d265-ea22-4fe2-871e-3635be9788fd /var            ext4    relatime        0       2
# swap was on /dev/sdc6 during installation
UUID=09949747-01d7-4fbb-8602-11a617577acf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

_fdisk -l return_

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd63fd63

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4d0e4d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10443    83883366    7  HPFS/NTFS
/dev/sdc2           10444       10476      265072+  83  Linux
/dev/sdc3           10477       10731     2048287+  83  Linux
/dev/sdc4           10732       20023    74637990    5  Extended
/dev/sdc5           10732       14902    33503526   83  Linux
/dev/sdc6           14903       15157     2048256   82  Linux swap / Solaris
/dev/sdc7           15158       15412     2048256   83  Linux
/dev/sdc8           15413       16193     6273351   83  Linux
/dev/sdc9           16194       20023    30764443+  83  Linux

------

Any thoughts? I just need some expert advice on how to fix grub.

Thanks.

---

### Post by unutbu on 2009-07-16
Please run [boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the RESULTS.txt file here. Using [code tags]("http://ubuntuforums.org/showpost.php?p=5490091&postcount=43") would be appreciated.

With your current setup are you getting GRUB Error #15 (when booting Ubuntu) or #13 (When booting Windows)?

PS. I have to leave now. Others may be able to assist you tonight. If not, I'll look at this tomorrow.

---

### Post by Help A Fool on 2009-07-17
Hi unutbu,

This morning I took one more crack at a clean install of both operating systems. The menu.lst, device.map and fstab file contents along with the results of the 'fdisk -l' command came from this recent, and current setup. I had hoped that I'd fix it in the doing, but it is obviously a big old waste of time.

For this latest reinstall I tweaked a couple bios options giving the cd-rom first boot and enabling hdd-0 as the second boot just in case grub needed it's presence. I also entered my sataraid bios and destroyed and recreated my raid striped set, by doing that it seemed to prevent the ubuntu partitioner from seeing any free space on either sda or sdb.

At stage 7 of the installation I changed the default boot loader placement from hd0 to hd2 which should be correct right?

Here are the results you were looking for:

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe4d0e4d0

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   167,766,794   167,766,732   7 HPFS/NTFS
/dev/sdc2         167,766,795   168,296,939       530,145  83 Linux
/dev/sdc3         168,296,940   172,393,514     4,096,575  83 Linux
/dev/sdc4         172,393,515   321,669,494   149,275,980   5 Extended
/dev/sdc5         172,393,578   239,400,629    67,007,052  83 Linux
/dev/sdc6         239,400,693   243,497,204     4,096,512  82 Linux swap / Solaris
/dev/sdc7         243,497,268   247,593,779     4,096,512  83 Linux
/dev/sdc8         247,593,843   260,140,544    12,546,702  83 Linux
/dev/sdc9         260,140,608   321,669,494    61,528,887  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="6EB8AFC8B8AF8D61" TYPE="ntfs" 
/dev/sdc2: UUID="31382542-8625-4918-8efa-e486cce2d274" TYPE="ext3" 
/dev/sdc3: UUID="73779004-5d13-4b77-8b0c-6b9ff5964886" TYPE="ext4" 
/dev/sdc5: UUID="bc8560d6-5b03-42fe-889c-57f7068d300b" TYPE="ext4" 
/dev/sdc6: UUID="09949747-01d7-4fbb-8602-11a617577acf" TYPE="swap" 
/dev/sdc7: UUID="9838c874-aeba-4803-95e2-b3cce3b265fb" TYPE="ext4" 
/dev/sdc8: UUID="9020d265-ea22-4fe2-871e-3635be9788fd" TYPE="ext4" 
/dev/sdc9: UUID="06e4b3bd-d027-4441-ad2c-36280d827a9b" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdc3 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc2 on /boot type ext3 (rw,relatime)
/dev/sdc9 on /home type ext4 (rw,relatime)
/dev/sdc7 on /tmp type ext4 (rw,relatime)
/dev/sdc5 on /usr type ext4 (rw,relatime)
/dev/sdc8 on /var type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sinner/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sinner)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=sinner)


================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


============================= sdc2/grub/menu.lst: =============================

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
# kopt=root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=31382542-8625-4918-8efa-e486cce2d274

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/vmlinuz-2.6.28-13-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro quiet splash vga=795 
initrd		/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/vmlinuz-2.6.28-13-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro  single
initrd		/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/vmlinuz-2.6.28-11-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro quiet splash vga=795 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/vmlinuz-2.6.28-11-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=================== sdc2: Location of files loaded by Grub: ===================


  86.1GB: grub/menu.lst
  86.1GB: grub/stage2
  85.9GB: initrd.img-2.6.28-11-generic
  85.9GB: initrd.img-2.6.28-13-generic
  85.9GB: vmlinuz-2.6.28-11-generic
  85.9GB: vmlinuz-2.6.28-13-generic

=========================== sdc3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=31382542-8625-4918-8efa-e486cce2d274

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/vmlinuz-2.6.28-13-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro quiet splash vga=795 
initrd		/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/vmlinuz-2.6.28-13-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro  single
initrd		/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/vmlinuz-2.6.28-11-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro quiet splash vga=795 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/vmlinuz-2.6.28-11-generic root=UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		31382542-8625-4918-8efa-e486cce2d274
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc3 during installation
UUID=73779004-5d13-4b77-8b0c-6b9ff5964886 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sdc2 during installation
UUID=31382542-8625-4918-8efa-e486cce2d274 /boot           ext3    relatime        0       2
# /home was on /dev/sdc9 during installation
UUID=06e4b3bd-d027-4441-ad2c-36280d827a9b /home           ext4    relatime        0       2
# /tmp was on /dev/sdc7 during installation
UUID=9838c874-aeba-4803-95e2-b3cce3b265fb /tmp            ext4    relatime        0       2
# /usr was on /dev/sdc5 during installation
UUID=bc8560d6-5b03-42fe-889c-57f7068d300b /usr            ext4    relatime        0       2
# /var was on /dev/sdc8 during installation
UUID=9020d265-ea22-4fe2-871e-3635be9788fd /var            ext4    relatime        0       2
# swap was on /dev/sdc6 during installation
UUID=09949747-01d7-4fbb-8602-11a617577acf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc3: Location of files loaded by Grub: ===================


  86.3GB: boot/grub/menu.lst
  86.3GB: boot/grub/stage2
  86.2GB: boot/initrd.img-2.6.28-11-generic
  86.2GB: boot/initrd.img-2.6.28-13-generic
  86.1GB: boot/vmlinuz-2.6.28-11-generic
  86.1GB: boot/vmlinuz-2.6.28-13-generic
  86.2GB: initrd.img
  86.2GB: initrd.img.old
  86.1GB: vmlinuz
  86.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  7a 42 ff 3f 37 c8 10 00  00 00 00 00 3f 00 00 00  |zB.?7.......?...|
00000010  00 00 00 00 20 20 20 20  57 20 2d 44 4d 57 4d 41  |....    W -DMWMA|
00000020  48 39 31 33 37 31 33 31  00 00 00 40 41 00 32 2e  |H9137131...@A.2.|
00000030  30 30 20 20 20 20 57 44  43 20 57 44 38 30 30 4a  |00    WDC WD800J|
00000040  44 2d 37 35 4d 53 41 31  20 20 20 20 20 20 20 20  |D-75MSA1        |
00000050  20 20 20 20 20 20 20 20  20 20 20 20 20 20 10 80  |              ..|
00000060  00 00 00 2f 01 40 00 00  00 00 07 00 00 4f a0 12  |.../.@.......O..|
00000070  00 00 00 00 00 00 10 01  90 2f 50 09 00 00 07 00  |........./P.....|
00000080  03 00 78 00 78 00 78 00  78 00 00 00 00 00 00 00  |..x.x.x.x.......|
00000090  00 00 00 00 00 00 1f 00  06 07 00 00 4c 00 40 00  |............L.@.|
000000a0  fe 00 00 00 6b 74 01 7f  23 40 69 74 01 3e 23 40  |....kt..#@it.>#@|
000000b0  7f 40 00 00 00 00 00 00  00 00 00 00 80 80 00 00  |.@..............|
000000c0  00 00 00 00 00 00 00 00  90 2f 50 09 00 00 00 00  |........./P.....|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  01 00 00 00 12 31 95 10  04 00 02 00 31 51 20 16  |.....1......1Q .|
00000110  07 09 20 00 64 00 00 00  02 00 ff ff 00 00 00 00  |.. .d...........|
00000120  00 00 00 00 01 00 00 00  01 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 52 f6  |..............R.|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 3f 10 00 00  |............?...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 a5 49  |...............I|
00000200

Unknown MBR on /dev/sdb

00000000  7a 42 ff 3f 37 c8 10 00  00 00 00 00 3f 00 00 00  |zB.?7.......?...|
00000010  00 00 00 00 20 20 20 20  57 20 2d 44 4d 57 4d 41  |....    W -DMWMA|
00000020  48 39 37 32 32 34 30 32  00 00 00 40 41 00 32 2e  |H9722402...@A.2.|
00000030  30 30 20 20 20 20 57 44  43 20 57 44 38 30 30 4a  |00    WDC WD800J|
00000040  44 2d 37 35 4d 53 41 31  20 20 20 20 20 20 20 20  |D-75MSA1        |
00000050  20 20 20 20 20 20 20 20  20 20 20 20 20 20 10 80  |              ..|
00000060  00 00 00 2f 01 40 00 00  00 00 07 00 00 4f a0 12  |.../.@.......O..|
00000070  00 00 00 00 00 00 10 01  90 2f 50 09 00 00 07 00  |........./P.....|
00000080  03 00 78 00 78 00 78 00  78 00 00 00 00 00 00 00  |..x.x.x.x.......|
00000090  00 00 00 00 00 00 1f 00  06 07 00 00 4c 00 40 00  |............L.@.|
000000a0  fe 00 00 00 6b 74 01 7f  23 40 69 74 01 3e 23 40  |....kt..#@it.>#@|
000000b0  7f 40 00 00 00 00 00 00  00 00 00 00 80 80 00 00  |.@..............|
000000c0  00 00 00 00 00 00 00 00  90 2f 50 09 00 00 00 00  |........./P.....|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  01 00 00 00 12 31 95 10  04 00 02 00 31 51 20 16  |.....1......1Q .|
00000110  07 09 20 00 64 00 01 00  02 00 ff ff 00 00 00 00  |.. .d...........|
00000120  00 00 00 00 01 00 00 00  01 00 00 02 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 53 f1  |..............S.|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 3f 10 00 00  |............?...|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 a5 48  |...............H|
00000200


```

After I had installed both operating systems, and was able to boot ubuntu, I rebooted with the xp cd, ran the recovery console and did a fixboot, but not a fixmbr. Now where I had a grub error #13 (initially) - and then a grub error #21 on this recent attempt to boot xp prior to the 'fixboot' - I now have no grub error just the old 'invalid system disk' error.

I'm not going to try any more shenanigans until further advice is proffered as I am out of my element here. Ubuntu is up and running and up-to-date on this machine and if I get bored I'll just play a game on my i7/Windoze7 machine (boo! hiss!) ;).

Thanks again y'all.

---

### Post by merlinus on 2009-07-17
This may be totally off the wall, but try changing this:

title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

to this:

title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

and restart.

---

### Post by unutbu on 2009-07-17
Yes, I agree with merlinus.

To do what merlinus suggests, boot Ubuntu, open a terminal (Applications>Accessories>Terminal) and type
```

gksu gedit /boot/grub/menu.lst
```

This will open the gedit text editor with root privileges. 
You'll find the boot stanza to be edited at end of the file. 

Let us know how it goes.

---

### Post by Help A Fool on 2009-07-18
Hi,

Sorry for the late follow-up.

I made the suggested changes to grub's menu.lst and it worked! I now have both systems up and running and all is good... well except for the fact that I have no sound as there doesn't seem to be a proper linux driver for x-fi's, but oh well.

...

So was this a user fault or did grub just need some tlc, as I swear that my very first dual-boot install attempt a few days ago had the bootloader installed to (hd0,0); maybe it's all blurring together and I'm confused.

What should I have done differently when I was installing the OS's?

...

Anyway a huge amount of thanks to you good people... I hope down the road that I'll be able to return the favour.

Ciao.

---

### Post by merlinus on 2009-07-18
Glad it is working!  Good on you for hanging in there.

My best guess is that the problem was in the boot order of your hdds.  Clearly something changed when you reinstalled.

---

### Post by unutbu on 2009-07-18
I'm glad to hear you can now dual-boot.

Here is my guess as to what happened:

When running Linux, GRUB uses Linux to list the available drives. It names them (hd0), (hd1), etc. The alternate installer saw /dev/sdc1 was a Windows partition. sdc was the third drive (as listed by Linux) so the menu.lst was written with a boot stanza that said Windows was on (hd2,0) (GRUB-talk for /dev/sdc1). 

When booting, GRUB uses the BIOS (not Linux!) to list the available drives.
Sometimes the BIOS chooses to list the drives in a different order than Linux.
The BIOS order depends on the position the drive are connected on the data cable,
the BIOS boot order that you set in the BIOS menu, and the way the BIOS is programmed. 
Some BIOSes may choose to list all SATAs before PATAs, for example.

The alternate Ubuntu installer has no way of determining what order the BIOS is going to list the drives. It just guesses. 

So given the current state of technology (too many different BIOS?), the best you can do is understand how GRUB works, and be prepared to modify the menu.lst when necessary.

In your case, if you wish to reinstall in the future or on another multi-disk machine,
you could just add many boot stanzas like the following and just try them all until 
you discover the one that works with your BIOS.

```
title		Microsoft Windows XP Professional (hd0,0)
rootnoverify	(hd0,0)
savedefault
chainloader	+1

title		Microsoft Windows XP Professional (hd1,0)
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Microsoft Windows XP Professional (hd2,0)
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

Note that Windows always expects to be on the first drive. So when the BIOS lists Windows on the second drive, we use the GRUB map command to switch the meaning of (hd1) to (hd0) right before the chainload command, so that by the time Windows is booted, it is on the first drive. The first boot stanza above has no map commands because Windows is already on the first drive (as listed by the BIOS).

---

