---
title: "can't boot winxp after install ubuntu"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by dreamer565 on 2009-05-16
I'm new to the forum, and new to ubuntu.  So my apologies.  I really need some help.

I bought a new external USB hard drive (1 terabyte) for Ubuntu, and want to leave the internal sata drives (80 gb & 100gb) for XP.  I installed ubuntu 9.04, following several threads and instructions on how to install to dual boot.  I do have the ubuntu working but xp won't boot.

At first i had an error where grub wan't even giving me a menu, or booting into either os.  I followed some threads here and now have it working to the point where it does list both OS's and lets me boot ubuntu.

However if i click to boot XP, i get a Error 12: Invalid device requested.  press any key...

Can someone help me with this?  I am a noob, but i'm trying to learn.

I did find where someone suggested running a boot_info_script tool and posting the results to the forum - so here's mine:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 1946118739 on boot drive #3 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc5 and 
                       looks at sector 1949601274 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbc1cbc1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   156,232,124   156,151,800   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb0bbb0b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   234,356,219   234,356,157   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,943,045,684 1,943,045,622   c W95 FAT32 (LBA)
/dev/sdc2       1,943,045,685 1,953,520,064    10,474,380   5 Extended
/dev/sdc5       1,948,282,938 1,953,166,634     4,883,697  83 Linux
/dev/sdc6       1,953,166,698 1,953,520,064       353,367  82 Linux swap / Solaris
/dev/sdc7       1,943,045,811 1,947,929,444     4,883,634  83 Linux
/dev/sdc8       1,947,929,508 1,948,282,874       353,367  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" UUID="6E44-72DD" TYPE="vfat" 
/dev/sdb1: UUID="F6D44421D443E28B" TYPE="ntfs" 
/dev/sdc1: LABEL="My Book" UUID="8C43-8F03" TYPE="vfat" 
/dev/sdc5: UUID="9dbeab05-2ec8-4f8b-bd98-1169d52cafcd" TYPE="ext3" 
/dev/sdc6: UUID="bd9cfd31-fb61-4761-84ec-40f10cbad580" TYPE="swap" 
/dev/sdc7: UUID="2864d388-bd9e-4c88-b8f6-f76395cf653d" TYPE="ext3" 
/dev/sdc8: UUID="98188d93-b108-412e-8c72-5ea2af9eba04" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/sjones/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sjones)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc7 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sdc5/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=9dbeab05-2ec8-4f8b-bd98-1169d52cafcd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9dbeab05-2ec8-4f8b-bd98-1169d52cafcd

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
uuid        9dbeab05-2ec8-4f8b-bd98-1169d52cafcd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9dbeab05-2ec8-4f8b-bd98-1169d52cafcd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9dbeab05-2ec8-4f8b-bd98-1169d52cafcd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9dbeab05-2ec8-4f8b-bd98-1169d52cafcd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9dbeab05-2ec8-4f8b-bd98-1169d52cafcd
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=9dbeab05-2ec8-4f8b-bd98-1169d52cafcd /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=bd9cfd31-fb61-4761-84ec-40f10cbad580 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 998.1GB: boot/grub/menu.lst
 998.1GB: boot/grub/stage2
 998.1GB: boot/initrd.img-2.6.28-11-generic
 998.7GB: boot/vmlinuz-2.6.28-11-generic
 998.1GB: initrd.img
 998.7GB: vmlinuz

=========================== sdc7/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=2864d388-bd9e-4c88-b8f6-f76395cf653d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2864d388-bd9e-4c88-b8f6-f76395cf653d

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
uuid        2864d388-bd9e-4c88-b8f6-f76395cf653d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2864d388-bd9e-4c88-b8f6-f76395cf653d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2864d388-bd9e-4c88-b8f6-f76395cf653d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2864d388-bd9e-4c88-b8f6-f76395cf653d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2864d388-bd9e-4c88-b8f6-f76395cf653d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdc5)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9dbeab05-2ec8-4f8b-bd98-1169d52cafcd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdc5)
root        (hd2,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9dbeab05-2ec8-4f8b-bd98-1169d52cafcd ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc5.
title        Ubuntu 9.04, memtest86+ (on /dev/sdc5)
root        (hd2,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdc7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc7 during installation
UUID=2864d388-bd9e-4c88-b8f6-f76395cf653d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc8 during installation
UUID=98188d93-b108-412e-8c72-5ea2af9eba04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc7: Location of files loaded by Grub: ===================


 996.4GB: boot/grub/menu.lst
 996.4GB: boot/grub/stage2
 996.4GB: boot/initrd.img-2.6.28-11-generic
 996.9GB: boot/vmlinuz-2.6.28-11-generic
 996.4GB: initrd.img
 996.9GB: vmlinuz

---

### Post by quixote on 2009-05-17
This part of the /boot/grub/menu.lst is telling grub where to find Windows.> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1

It's expecting your bootable Windows to be on the second partition of your first physical drive (probably the hard drive inside your computer rather than the USB one).

What's probably wrong is (hd0,1).  Usually, for Windows it's (hd0,0).  Basically, the easiest method is just to try different numbers until you hit on the one that works. The first number is the physical drive, the second the partition, and grub starts numbering from 0.

There's more at this site: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) (near the beginning, where it says "If, after installing grub, Windows will not boot")  and more than you ever wanted to know about grub here: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)  :)

---

### Post by dreamer565 on 2009-05-18
Great, thanks I'll try that and see what i get.
 
My concern is that i think I've hosed my mbr on that drive, and that windows won't boot regardless of whether i point it correctly.  I can't even point to that drive via bios and get anything but the grub bootloader.  
 
But I'll give it a shot.  If i can get that drive to boot xp with the usb drive not connected, i should be good.  then with or without grub i'll be able to get to either ubuntu or windows.

---

### Post by quixote on 2009-05-18
Fixing the MBR is actually easier than you might think, if you have a WinXP boot CD.  Start it up, choose the "repair" option, and then when you get a prompt, type "fixmbr" (without quotes).

If you don't have a WinXP boot CD, all is not lost.  If you have access to a functioning XP machine, tell the system to make a rescue floppy (this assumes you can use a floppy in the sick computer!).  That's in Administrative tasks somewhere, I think.  Then boot the sick computer from that floppy, and run fixmbr at the prompt.

---

### Post by dreamer565 on 2009-05-19
Thanks a bunch Quixote, that did it.

I unplugged my external usb drive (where ubuntu is installed), 
booted from my winxp cd and was able to go into recovery mode, and from there did the fixmbr.  I wasn't sure that would do it, since when i did a diskpart command it showed my xp partition as unknown.  but after another reboot, xp booted back to normal.

I now have an extra partition at the end of the drive that i need to merge back in (first place ubuntu installed).  But i can deal with that.

Thanks again.):P

---

### Post by dreamer565 on 2009-05-20
Ok.... now I've gotten quite a bit further, but in some ways i'm back to square one.

I have re-done my ubuntu install, and manually resized the partitions and set it up to use most of the external usb drive (it now has almost all of the 1 terrabytes).  So i no longer have the issues i originally had with nothing being peristent and the only usable version of ubuntu being the one running from live-cd which in itself wasn't persistent and lost all changes every reboot. So having ubuntu boot is a good thing.

I also restored my winxp mbr and can boot into xp if i a) remove the external usb drive, or b) select to boot from the internal hard drive from bios.

I also now have grub booting and displaying what looks deceptively like a valid menu with ubuntu (this section now works after playing with it and point it to the correct boot sector  hd(2,5) in my case. But the xp option doesn't work.  If i point to hd(0,0) which my xp is on the 1st internal drive then it boots to a live-cd option i originally tried to save to the usb drive, in looking at the partitions on that drive there is a 30mb partition 0, and the 79gb partition 1. I believe the 30mb was originally a dell utility partition that won't boot anymore - my guess is that is where the live ubuntu ended up.  If i change the grub menu to point to hd(0,1) it tells me invalid device.  I tried using supergrub, that only screwed up both menu items so i had to manually put them the way they are now.

Hmmmm.... yep, that was where i was before.  So... not sure what to try next.  Any ideas out there?

On the plus side, at least i can boot to either os.  I just have to use bios as my bootloader.

---

### Post by quixote on 2009-05-21
dreamer565, since everything boots when referred to in a way that the machine understands, the only problem is grub.  Somehow, what it thinks a drive number is and what it really is are two different things.

When you have your system booted up and all drives attached, try ```
sudo fdisk -l
``` to get a list of all the drives the machine can see on your system.  

Figure out which one is your bootable Windows partition at this point.  For instance, with the usb drive attached, is it maybe "sdb" or something??  In that case, I think grub would consider it (hd1,0) (second hard drive, first partition on it).  

I'm off on a trip for a week so I don't have time to check it out just now, but one of these two links should give you the details about how grub names drives and partitions to get things sorted out.  (I hope, anyway! :) )

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and the more-than-you-ever-wanted-to-know-about-grub link:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by dreamer565 on 2009-05-21
Thanks for the help and suggestions.  I'm going out of town myself later today and won't be back til next Wednesday.

> sjones@slj-ubuntu:~$ sudo fdisk -l
[sudo] password for sjones: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbc1cbc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9725    78075900    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb0bbb0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14588   117178078+   7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002db5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3145    25262181    c  W95 FAT32 (LBA)
/dev/sdc2            3146      121601   951497820    5  Extended
/dev/sdc5            3146      120475   942453193+  83  Linux
/dev/sdc6          120476      121601     9044563+  82  Linux swap / Solaris
sjones@slj-ubuntu:~$ 

Here's my grub (which is back to the original format, that comes back with invalid device found message)-

> title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ace99491-53c1-4932-a443-09851e527906
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ace99491-53c1-4932-a443-09851e527906 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ace99491-53c1-4932-a443-09851e527906
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ace99491-53c1-4932-a443-09851e527906 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ace99491-53c1-4932-a443-09851e527906
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

At this point, i've tried substituting hd(0,0) = boots to a live-cd version of ubuntu, hd(0,1) = boots to invalid disk, hd(1,0) = blank screen that says "Starting up..."; hd(1,1) = same "starting up..."; for the heck of it I even tried hd(2,0) and got the same thing.  

I think it needs to be hd(0,1) or hd(0,0), and based on the fdisk, it looks like it should be hd(0,1).  but neither seems to work.  At this point maybe i'll just live with using bios to switch which i boot from.

Quixote thanks for all the help - have a good trip.

---

### Post by dreamer565 on 2009-05-21
forgot to mention that when i boot to ubuntu from grub, it says it is booting hd(0,4) and boots to the ubuntu on the 5th partition of the external usb drive.

---

### Post by quixote on 2009-05-27
I'm no expert on grub, unfortunately.  As I understand what's going on:

/dev/sda = 80GB hard disk (inside your computer?).  Two partitions:1 is Dell recovery, 2 is bootable Windows (XP or Vista)

/dev/sdb = 120GB drive.  One partition: bootable Windows (XP or Vista)

/dev/sdc = 1TB drive (external USB hard drive, I assume). Two partitions that concern you: sdc1 is bootable WinXP; sdc5 is Ubuntu.

It's interesting that grub considers the USB drive the first one in the system.  That's why it's finding Ubuntu at "(hd0,4)" (=drive 1, partition 5).  (Remember that grub numbering starts from zero, not one.)

So (hd0,1) would be trying to boot off /dev/sdc2.  That's your extended partion, the one that is just a container for your linux partitions.  Not bootable, so that returns an error message.

(hd0,0) would be the first partition on your 1TB USB drive, which is listed as a bootable WinXP partition, but maybe that installation of WinXP is having issues of its own.

To try to boot off the internal 80GB hard drive, I'd suggest trying (hd2,1), counterintuitive as that might seem.  (Third drive, second partition.) 
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2                  ##i.e. internal 80GB drive, partition 2
title Microsoft Windows XP Professional
rootnoverify (hd0,1)            ## change to (hd2,1)
savedefault
makeactive
chainloader +1 
```

I don't have either "noverify" or the "savedefault" line on my system.  I don't think they're essential, so you might also try it deleting those and see if that helps matters.  ie. just "root (hd2,1)"

---

### Post by dreamer565 on 2009-06-02
I'll give that a shot without the "noverify"  I already tried it with the rootnoverify (hd2,1).  I basically tried all combinations.

I think grub sees the usb first because i told bios to boot from the usb first.   
You are correct that at one time the 120gb drive was a bootable windows partition - its a drive i moved over from a prior computer and added as a slave drive.  However, the USB drive was never a bootable windows drive.  It does have a ntfs partition on it.  

What you said about using hd(0,1) makes since why it is invalid since it points to the extended partition of the usb drive which isn't bootable.  

hd(0,0) which is the first partition of the usb drive boots to a live-cd version of ubuntu which isn't useful.  That's the one you say for some reason shows up as another xp partition.  Perhaps because it is ntfs?

I was expecting that if hd0 was the usb drive that hd1 would be the first internal drive.  I did try using hd (1,0) and hd(1,1) - I agree that the utility partition is ,0 so the bootable XP partition should be ,1

I also tried hd(2,0) but not sure at this point if i tried hd(2,1) so that may be what i was missing.

I also saw a thread somewhere regarding needing to make some sort of swap because XP needs to think it is the drive 0, but I'm not really sure how to go about that.

I really appreciate the help.  I'll let you know how i make out.

---

### Post by quixote on 2009-06-02
> hd(0,0) which is the first partition of the usb drive boots to a live-cd version of ubuntu which isn't useful. That's the one you say for some reason shows up as another xp partition. Perhaps because it is ntfs?

When you say "liveCD version" do you mean you have an iso image there?  If it's formatted ntfs it would I think indeed be listed as a windows partition, so that explains that.

If (hd2,1) doesn't work to get at the WinXp boot partition, I don't have any other ideas.  Let us know how it goes.  (Also, make sure you use "(hd2,1)" not "hd(2,1)". Grub expects the first format.)

As for Windows needing to be on what it thinks is the first drive, yeah, I'll bet that's true, but I don't know how to make it think it is.  Fusspot of an OS, that.

I hope it works!

---

### Post by dreamer565 on 2009-06-03
ok, here's what I've tried and the results:

(hd0,0) boots to a live ubuntu
(hd0,1) has a error 12 invalid disk
(hd1,0) boots to a blank screen saying "starting up...."
(hd1,1) boots to a blank screen saying "starting up...."
(hd2,0) boots to a blank screen saying "starting up...."
(hd2,1) error 12 invalid disk

physical drives -
/dev/sda = 80GB hard disk (internal).  Two partitions:1 is Dell recovery, 2 is bootable Windows (XP)

/dev/sdb = 120GB drive (internal).  One partition: former bootable Windows (XP)

/dev/sdc = 1TB drive (external USB hard drive). partition 0 is ubuntu live version, partition 5 is ubuntu full version

since ubuntu full boots to (hd0,4) that seems to imply that sdc = hd0

So I have run out of ideas.  It might be that XP wants to be the drive0 and that is why it isn't booting.  Or it might be who knows what.  I can boot to XP if i hit F12 to select boot order and select to boot from the internal harddrive.  So I can dual boot, I just can't use Grub to do it.  That may be the best I can do.

I do appreciate all the help.

---

### Post by quixote on 2009-06-03
There has got to be a way to do this that's more elegant than altering boot order.  There just has to be.  Unfortunately, I don't know what it is.  Grr.

I was looking at your first message and noticed this right near the top:> sda2: __________________________________________________ _______________________

File system:
Boot sector type: Grub
Boot sector info: Grub0.97 is installed in the boot sector of sda2 and
looks at sector 1946118739 on boot drive #3 for the
stage2 file. A stage2 file is at this location on
/dev/sdc. Stage2 looks on partition #7 for
/boot/grub/menu.lst.
Mounting failed:
mount: unknown filesystem type ''
As your Windows partition, I'll bet it's not supposed to have a grub boot sector type.  I don't remember whether you said you'd already tried to fix windows MBR (Master Boot Record).  At this point, I'd guess that that's the trouble.  

If you're not totally fed up at this point, try fixing that.  About 4/5 of the way down on [this site]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") under Troubleshooting are the obscure-looking commands.  I haven't tried those myself, but I've found help.ubuntu.com to be bulletproof so far.  Or try search for "fix mbr windows grub"  or something like that.

(Also, if you follow the convoluted track of what it thinks it's doing, no wonder it can't find an OS: grub in the boot sector of your Windows drive is looking at a specific sector on /dev/sdc/ and from there it's directed to /dev/sdc7 which doesn't exist, I think?)

In any case, we can't let a damn computer win this one, can we?

---

### Post by dreamer565 on 2009-06-05
well, that might have changed.  Originally I did have the MBR screwed up on my XP drive and couldn't boot to it at all, so that bootinfo might be a bit out of date.  I was able to successfully fix the MBR and as mentioned, I can boot to XP, just not from grub.

I'll try to come up with a new copy of the bootinfo if that would help.

---

### Post by dreamer565 on 2009-06-05
Here's the bootinfo:

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcbc1cbc1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   156,232,124   156,151,800   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb0bbb0b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   234,356,219   234,356,157   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002db5e

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    50,524,424    50,524,362   c W95 FAT32 (LBA)
/dev/sdc2          50,524,425 1,953,520,064 1,902,995,640   5 Extended
/dev/sdc5          50,524,488 1,935,430,874 1,884,906,387  83 Linux
/dev/sdc6       1,935,430,938 1,953,520,064    18,089,127  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" UUID="6E44-72DD" TYPE="vfat" 
/dev/sda2: UUID="6A90726D90723F9D" TYPE="ntfs" 
/dev/sdb1: UUID="F6D44421D443E28B" TYPE="ntfs" 
/dev/sdc1: LABEL="My Book" UUID="8C43-8F03" TYPE="vfat" 
/dev/sdc5: UUID="ace99491-53c1-4932-a443-09851e527906" TYPE="ext3" 
/dev/sdc6: UUID="759ed8c5-ab95-4c80-a286-c3ee86933e43" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdc5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/sjones/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sjones)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc5/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=ace99491-53c1-4932-a443-09851e527906 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ace99491-53c1-4932-a443-09851e527906

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
uuid        ace99491-53c1-4932-a443-09851e527906
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ace99491-53c1-4932-a443-09851e527906 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ace99491-53c1-4932-a443-09851e527906
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ace99491-53c1-4932-a443-09851e527906 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ace99491-53c1-4932-a443-09851e527906
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd2,1)
savedefault
makeactive
chainloader    +1


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=ace99491-53c1-4932-a443-09851e527906 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=759ed8c5-ab95-4c80-a286-c3ee86933e43 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 408.6GB: boot/grub/menu.lst
 408.5GB: boot/grub/stage2
 408.6GB: boot/initrd.img-2.6.28-11-generic
 408.5GB: boot/vmlinuz-2.6.28-11-generic
 408.6GB: initrd.img
 408.5GB: vmlinuz

```

Not sure if that makes any difference but just in case anything has changed since starting this process.

---

### Post by quixote on 2009-06-05
Your Windows boot drive definitely looks more sensible now. :D

The page I mentioned in my last message ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)) is the one I've generally used, but they say that it doesn't apply if you have Linux on a different physical drive.  The recommendation is to use "SuperGrub" ([download link]("http://forjamari.linex.org/projects/supergrub/"))  I haven't tried that, but it looks pretty slick.  Well worth a look: [http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems](http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems)  Yours sounds like the first link under "Windows Boot Problems."

They also have examples and "Onederer Solution B" ([http://www.supergrubdisk.org/w/index.php5?title=OnedererTwoHardDisksExample](http://www.supergrubdisk.org/w/index.php5?title=OnedererTwoHardDisksExample)) seems to me to describe your situation.

Hope that works!

---

### Post by dreamer565 on 2009-06-06
ok.... i finally have it!!

I followed the links, supergrub didn't really help that much, think because of my set-up with windows boot being a seperate disk and it couldn't quite sort it out.  I followed the link regarding the "windows boot problems" and the Solution B you referenced, but it appeared that was more an example of how to use XP as the main boot and change the boot loader (boot.ini) file to point to ubuntu.  I gave that a shot and followed the directions for the heck of it, and copied the linux.bin file to C:\ and updated my boot.ini to have an option to use it, and changed the boot order to boot first from the internal drive, that did allow me to boot into XP, and see the boot loader menu, from which i could boot XP, but got a similar failure when i selected Ubuntu - it just gave me a blank screen and did nothing.

So, i decided my main problem was because i have two seperate drives not two partitions on the same drive, and that XP especially is finicky and wants to be the first drive.  SO... I did some further searching on how to trick it and found some examples using a map command.  I had to try a couple different combinations but finally got one that works.  

So at this point, I boot to my usb external drive, the grub menu comes up, and I can boot into ubuntu or I can now boot into XP.  YEAH! 

Here's the code in the grub menu.lst that i changed:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
root    (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader    +1

```

I think what this does is swap hd0 and hd1 so that what it sees as hd1 becomes hd0, and i think booting from the USB drive (ubuntu) the drives become numbered hd0=sdc, hd1=sda, and hd2=sdb.  That's why ubuntu boots as hd(0,4) when it exists on sdc partition 5.  I'm certainly no expert, and could just be guessing to make the facts fit my theory.  But that's how i can make it appear semi-logical to my thinking.

I greatly appreciate all the help.  And i feel much better having it all work the way it is supposed to.  I admit I was ready to give it up, but your >  In any case, we can't let a damn computer win this one, can we? made me keep searching for the answer.

Thanks again!

---

### Post by quixote on 2009-06-07
Sounds like it was quite a rabbit hunt.  Thanks for posting your solution!  Now I'll be able to make better use of a 320GB USB drive lying around the house myself. :D

---

