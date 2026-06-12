---
title: "Grub 1.97 Fail - not loading OS'es"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by NJC on 2009-11-11
Triple boot Ubuntu 9.10, 9.04 and XP.

This may not be a Grub failure, but mysteriously Ubuntu 9.04 and XP won't boot. I'm getting the same error as [here]("http://ubuntuforums.org/showpost.php?p=8275439&postcount=1") on Ubuntu 9.04. Ubuntu 9.10 DOES boot properly. Grub 1.97 is written to sda1, which starts Ubuntu 9.10 on sdb2. XP = sda1 and 9.04 is sda7.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7860    63135418+   7  HPFS/NTFS
/dev/sda2            7861       33561   206443282+   b  W95 FAT32
/dev/sda3           33562       38913    42989940    5  Extended
/dev/sda5           35995       38426    19535008+  83  Linux
/dev/sda6           38427       38913     3911796   82  Linux swap / Solaris
/dev/sda7           33563       35994    19535008+  83  Linux

Disk /dev/sdb: 640.1 GB

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            3953        4454     4032315    5  Extended
/dev/sdb2   *           1        3952    31744408+  83  Linux
/dev/sdb3            4455       77825   589352557+   b  W95 FAT32
/dev/sdb5            3953        4454     4032283+  82  Linux swap / Solaris

I have tried to update grub but no joy. Suggestions would be very helpful - I'm at a loss on this one.
     

[URL="http://ubuntuforums.org/showpost.php?p=8275439&postcount=1"]
[/URL]

---

### Post by darkod on 2009-11-11
Manual entries for 9.04 and XP? With 9.10 working you would have no problem for that.

---

### Post by NJC on 2009-11-11
Not sure what you mean by manual? Grub 1.97 automatically found the other OS'es and loaded the entries. It was working fine up until a few days ago.

---

### Post by NJC on 2009-11-11
As per bash ~/Desktop/boot_info_script*.sh

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda7 and 
                       looks at sector 542588633 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 71553510.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a9e7d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   126,270,899   126,270,837   7 HPFS/NTFS
/dev/sda2         126,270,900   539,157,464   412,886,565   b W95 FAT32
/dev/sda3         539,157,465   625,137,344    85,979,880   5 Extended
/dev/sda5         578,243,673   617,313,689    39,070,017  83 Linux
/dev/sda6         617,313,753   625,137,344     7,823,592  82 Linux swap / Solaris
/dev/sda7         539,173,593   578,243,609    39,070,017  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a14c4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1          63,488,880    71,553,509     8,064,630   5 Extended
/dev/sdb5          63,488,943    71,553,509     8,064,567  82 Linux swap / Solaris
/dev/sdb2    *             63    63,488,879    63,488,817  83 Linux
/dev/sdb3          71,553,510 1,250,258,624 1,178,705,115   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="92F00C4FF00C3C4B" LABEL="Win XP" TYPE="ntfs" 
/dev/sda2: LABEL="WIN VFAT" UUID="49C5-6324" TYPE="vfat" 
/dev/sda5: LABEL="Ubuntu 9.04 /hom" UUID="27248f60-bad1-49d2-8c6e-c4ff52b83b56" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="38a37ca0-0d07-4e02-be15-95e0eb76e4af" TYPE="swap" 
/dev/sda7: LABEL="Ubuntu 9.04" UUID="5c1482ce-a781-44e2-b2b1-7e3d89a71656" TYPE="ext4" 
/dev/sdb2: UUID="0b6b1e78-675a-4879-b4f0-9e9064c67668" TYPE="ext4" 
/dev/sdb3: LABEL="Win_640GB" UUID="80C4-10A7" TYPE="vfat" 
/dev/sdb5: UUID="d7336a8b-afa3-4e3e-85d3-cd5429754b80" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda2 on /media/win type vfat (rw,dmask=0000,fmask=0111)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/norm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=norm)
/dev/sda1 on /media/Win XP type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/menu.lst: ===========================

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
timeout        3

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
# kopt=root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5c1482ce-a781-44e2-b2b1-7e3d89a71656

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=2be7426f-6f98-43df-98d0-2afb1bcba02f ro quiet splash 
initrd        /boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=2be7426f-6f98-43df-98d0-2afb1bcba02f ro single 
initrd        /boot/initrd.img-2.6.24-18-generic
savedefault
boot




=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sdb7 during installation
UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656  /              ext4         relatime,errors=remount-ro  0  1  
# /home was on /dev/sdb5 during installation
UUID=27248f60-bad1-49d2-8c6e-c4ff52b83b56  /home          ext3         relatime                    0  2  
# swap was on /dev/sda4 during installation
UUID=97f570f2-3617-4598-8db0-3018e2531cfd  none           swap         sw                          0  0  
# swap was on /dev/sdb6 during installation
UUID=38a37ca0-0d07-4e02-be15-95e0eb76e4af  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
# http://slackwiki.org/Windows_Partitionss
/dev/sda2                                  /media/sda2    vfat         rw,dmask=0000,fmask=0111    0  0  

#s/dev/sdb2                                  /media/sdb2    vfat         owner,users,user            0  0  

=================== sda7: Location of files loaded by Grub: ===================


 276.0GB: boot/grub/menu.lst
 276.0GB: boot/grub/stage2
 276.0GB: boot/initrd.img-2.6.28-11-generic
 276.0GB: boot/initrd.img-2.6.28-13-generic
 276.0GB: boot/initrd.img-2.6.28-14-generic
 276.0GB: boot/initrd.img-2.6.28-15-generic
 276.0GB: boot/initrd.img-2.6.28-16-generic
 276.0GB: boot/vmlinuz-2.6.28-11-generic
 276.0GB: boot/vmlinuz-2.6.28-13-generic
 276.0GB: boot/vmlinuz-2.6.28-14-generic
 276.0GB: boot/vmlinuz-2.6.28-15-generic
 276.0GB: boot/vmlinuz-2.6.28-16-generic
 276.0GB: initrd.img
 276.0GB: initrd.img.old
 276.0GB: vmlinuz
 276.0GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 ro single 
    initrd    /boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 92f00c4ff00c3c4b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=38a37ca0-0d07-4e02-be15-95e0eb76e4af none            swap    sw              0       0
# vfat /dev/sda2 on /media/BACKUP 320GB 
/dev/sda2        /media/win                               vfat         rw,dmask=0000,fmask=0111    0  0  
# swap was on /dev/sdb5 during installation
UUID=d7336a8b-afa3-4e3e-85d3-cd5429754b80 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-11-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-11-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  7d 9e 0a 00 00 00 80 01  |...<.u..}.......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 75 bd 86 07 00 00  |......?...u.....|
000001d0  c1 ff 0b fe ff ff b4 bd  86 07 25 26 9c 18 00 fe  |..........%&....|
000001e0  ff ff 05 fe ff ff d9 e3  22 20 e8 f2 1f 05 00 00  |........" ......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by presence1960 on 2009-11-11
> **NJC said:**
> As per bash ~/Desktop/boot_info_script*.sh

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda7 and 
                       looks at sector 542588633 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 71553510.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a9e7d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   126,270,899   126,270,837   7 HPFS/NTFS
/dev/sda2         126,270,900   539,157,464   412,886,565   b W95 FAT32
/dev/sda3         539,157,465   625,137,344    85,979,880   5 Extended
/dev/sda5         578,243,673   617,313,689    39,070,017  83 Linux
/dev/sda6         617,313,753   625,137,344     7,823,592  82 Linux swap / Solaris
/dev/sda7         539,173,593   578,243,609    39,070,017  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a14c4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1          63,488,880    71,553,509     8,064,630   5 Extended
/dev/sdb5          63,488,943    71,553,509     8,064,567  82 Linux swap / Solaris
/dev/sdb2    *             63    63,488,879    63,488,817  83 Linux
/dev/sdb3          71,553,510 1,250,258,624 1,178,705,115   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="92F00C4FF00C3C4B" LABEL="Win XP" TYPE="ntfs" 
/dev/sda2: LABEL="WIN VFAT" UUID="49C5-6324" TYPE="vfat" 
/dev/sda5: LABEL="Ubuntu 9.04 /hom" UUID="27248f60-bad1-49d2-8c6e-c4ff52b83b56" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="38a37ca0-0d07-4e02-be15-95e0eb76e4af" TYPE="swap" 
/dev/sda7: LABEL="Ubuntu 9.04" UUID="5c1482ce-a781-44e2-b2b1-7e3d89a71656" TYPE="ext4" 
/dev/sdb2: UUID="0b6b1e78-675a-4879-b4f0-9e9064c67668" TYPE="ext4" 
/dev/sdb3: LABEL="Win_640GB" UUID="80C4-10A7" TYPE="vfat" 
/dev/sdb5: UUID="d7336a8b-afa3-4e3e-85d3-cd5429754b80" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda2 on /media/win type vfat (rw,dmask=0000,fmask=0111)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/norm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=norm)
/dev/sda1 on /media/Win XP type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/menu.lst: ===========================

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
timeout        3

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
# kopt=root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5c1482ce-a781-44e2-b2b1-7e3d89a71656

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5c1482ce-a781-44e2-b2b1-7e3d89a71656
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=2be7426f-6f98-43df-98d0-2afb1bcba02f ro quiet splash 
initrd        /boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=2be7426f-6f98-43df-98d0-2afb1bcba02f ro single 
initrd        /boot/initrd.img-2.6.24-18-generic
savedefault
boot




=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sdb7 during installation
UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656  /              ext4         relatime,errors=remount-ro  0  1  
# /home was on /dev/sdb5 during installation
UUID=27248f60-bad1-49d2-8c6e-c4ff52b83b56  /home          ext3         relatime                    0  2  
# swap was on /dev/sda4 during installation
UUID=97f570f2-3617-4598-8db0-3018e2531cfd  none           swap         sw                          0  0  
# swap was on /dev/sdb6 during installation
UUID=38a37ca0-0d07-4e02-be15-95e0eb76e4af  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
# http://slackwiki.org/Windows_Partitionss
/dev/sda2                                  /media/sda2    vfat         rw,dmask=0000,fmask=0111    0  0  

#s/dev/sdb2                                  /media/sdb2    vfat         owner,users,user            0  0  

=================== sda7: Location of files loaded by Grub: ===================


 276.0GB: boot/grub/menu.lst
 276.0GB: boot/grub/stage2
 276.0GB: boot/initrd.img-2.6.28-11-generic
 276.0GB: boot/initrd.img-2.6.28-13-generic
 276.0GB: boot/initrd.img-2.6.28-14-generic
 276.0GB: boot/initrd.img-2.6.28-15-generic
 276.0GB: boot/initrd.img-2.6.28-16-generic
 276.0GB: boot/vmlinuz-2.6.28-11-generic
 276.0GB: boot/vmlinuz-2.6.28-13-generic
 276.0GB: boot/vmlinuz-2.6.28-14-generic
 276.0GB: boot/vmlinuz-2.6.28-15-generic
 276.0GB: boot/vmlinuz-2.6.28-16-generic
 276.0GB: initrd.img
 276.0GB: initrd.img.old
 276.0GB: vmlinuz
 276.0GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 0b6b1e78-675a-4879-b4f0-9e9064c67668
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 ro single 
    initrd    /boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 92f00c4ff00c3c4b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=5c1482ce-a781-44e2-b2b1-7e3d89a71656 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 5c1482ce-a781-44e2-b2b1-7e3d89a71656
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=0b6b1e78-675a-4879-b4f0-9e9064c67668 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=38a37ca0-0d07-4e02-be15-95e0eb76e4af none            swap    sw              0       0
# vfat /dev/sda2 on /media/BACKUP 320GB 
/dev/sda2        /media/win                               vfat         rw,dmask=0000,fmask=0111    0  0  
# swap was on /dev/sdb5 during installation
UUID=d7336a8b-afa3-4e3e-85d3-cd5429754b80 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-11-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-11-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  7d 9e 0a 00 00 00 80 01  |...<.u..}.......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 75 bd 86 07 00 00  |......?...u.....|
000001d0  c1 ff 0b fe ff ff b4 bd  86 07 25 26 9c 18 00 fe  |..........%&....|
000001e0  ff ff 05 fe ff ff d9 e3  22 20 e8 f2 1f 05 00 00  |........" ......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

It looks to me as if the problem is in sda7. You have installed GRUB Legacy 0.97 to the partition sda7. When you choose 9.04 from the GRUB 2 it may be a problem because 9.04 is not chainloaded in grub.cfg in 9.10. When GRUB is installed to a partition it is usually to be chainloaded from the GRUB on MBR. Your 9.04 is not chainloaded in GRUB 2, it is trying to boot directly to a kernel.

This is my theory on how to fix it, but it is just a theory based on my understanding of GRUB 2. I know legacy GRUB better than the back of my hand but GRUB 2 not as well. 

I would try this to get GRUB Legacy off sda7: Use 9.04 Live CD to setup GRUB Legacy in the MBR of sda rather than in partition sda7 then use the 9.10 Live CD to restore GRUB 2 to MBR of sda. If my thinking is correct this will remove Legacy GRUB from the sda7 partition and put it on MBR of sda, which you will then replace with GRUB 2. I would proceed like this:

```
1. Boot your computer up with Ubuntu 9.04 CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,6)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,6)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

use instructions [here]("https://help.ubuntu.com/community/Grub2") to restore GRUB 2 from the 9.10 Live CD. Scroll down to almost the bottom of the page to find instructions to restore GRUB 2 from Live CD

---

### Post by NJC on 2009-11-11
Thanks very much for the help. I'll try to reload grub legacy onto sda and see what transpires.

Edit: 

```
find /boot/grub/stage1
```rendered Error 15: File not found. I'll go ahead and install grub first.

Edit #2: I have another problem, there seems to be the same boot error even starting the Live CD ... when Live CD finally booted up, none of my hard drives appear? This is an odd problem.

---

### Post by NJC on 2009-11-12
:roll:

I wonder how many times THIS happens. A few days ago I was trying to solve my display not waking after it is shut off via power manager (Ubuntu 9.10). Hopefully this will help someone else. I had changed the following to Disabled, instead of default Enabled:

ACPI ASIC (Application Specific Integrated Circuit) Support 

The giveaway was the error was still present when booting from Live CD.

---

