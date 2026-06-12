---
title: "how would you resize my hard disk"
date: 2010-01-05
forum: Hardware
---

### Post by Keith Fox on 2010-01-05
I noticed there's only 2 GB left on my Ubuntu partition (97% full).  I originally started with Linux Mint, resized that down, basically My Ubuntu partition needs more space on it.   Check out the screenshot of my disk partitions below:
[LIST]
[*] [SIZE=1]The other ubuntu (/dev/sda8) partition is necessary, because I can't figure out how to fix my grub2.  The grub2 loader is messed up, so I just added another ubuntu to fix my grub2 boot loader problem. (temporary fix)[/SIZE]
[/LIST]
 
[SIZE=2]How can I implement the *unallocated* *space* *(525GB)* towards _Ubuntu_ partition (/dev/sda6)?[/SIZE]

---

### Post by SteveDee on 2010-01-05
Surely sda5,6,7 & 8 live in the extended partition sd3. So if to stretch sda3 to include the free space, you will then be able to stretch sd6 to the size you require.

Re: Grub 2 issues: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Keith Fox on 2010-01-05
Thank you for that link steveDee, I was searching for that in the help section but just couldn't find it on my own. I was looking in the wrong spot, at partitioning.  I understand I need to stretch sda3, but unsure how to unfold that exactly.  I am booting from the ubutuntu karmic koala disc at startup, then opening Gparted... trying to get it to resize, maybe i'm still a little, "der der-der" Carlos Mencia would put it.

---

### Post by oldfred on 2010-01-05
The key symbol says the partition is mounted. Even from a liveCD it normally uses a swap if found. To use gparted you then have to do a swapoff.  

You should be able to expand the extended partition left into the unallocated space, then expand sda6 into the space in the extended partition. 

You have 2 swap partitions from your installs and should only need one, but each install probably points to a different swap and you would have to modify fstab to use the same swap.

---

### Post by drs305 on 2010-01-05
Here's a guide on expanding an Ubuntu partition. The second half would apply to you. 

[ Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

Major points include defragging Windows before any repartitioning, backing up important data, and unmounting swap even if using the LiveCD. In your case, you will have to expand the extended partition before you expand your / system.

---

### Post by SteveDee on 2010-01-05
> **Keith Fox said:**
> Thank you for that link steveDee, I was searching for that in the help section but just couldn't find it on my own. I was looking in the wrong spot, at partitioning.  I understand I need to stretch sda3, but unsure how to unfold that exactly.  I am booting from the ubutuntu karmic koala disc at startup, then opening Gparted... trying to get it to resize, maybe i'm still a little, "der der-der" Carlos Mencia would put it.

Yeah, I think in your particular case you should be able to boot from a Ubuntu LiveCD, run gparted, click on the block to the right of your unallocated area, then drag the left edge across to the left. Nothing actually happens until you confirm any pending changes.

The small print: Of course things can go wrong so you should backup any files your really don't want to lose.

---

### Post by Keith Fox on 2010-01-06
Thank you everyone.  I successfully got my Gparted to resize my ubuntu after doing Swapoff.  Now If I can just figure out the GRUB 2.  I got the link and I'm reading, trying to figure out which swap file is for Ubuntu and which swap file is for Ubuntu2. 

[LIST]
[*] I'm not familiar with fstab: for the swap files.
[*] I would like to use fstab to fix my swap file, then I could remove the other "ubuntu2": See attached thumbnail screenshot.
[*]I noticed there is no fstab folder in /etc
[*]Reading info located at [URL="https://help.ubuntu.com/community/Fstab"]Fstab
[/URL]
[/LIST]

---

### Post by louieb on 2010-01-06
> **Keith Fox said:**
> 
[LIST]
[*]  I noticed there is no fstab folder in /etc
[/LIST]

Please look again. There should be /etc/fstab is sda6. 

It would help if you followed the    [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and out put the results.txt file in your next post.

---

### Post by Keith Fox on 2010-01-06
Thanks again for helping me out.  I never knew of this "Boot Info Script"  Is there any thread tools on this site so I can bookmark that post to my favorites?
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 7 Gloria - x64 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5e6d5181

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   371,326,409   371,326,347  83 Linux
/dev/sda3         371,326,410 1,774,813,004 1,403,486,595   5 Extended
/dev/sda5       1,771,359,093 1,774,813,004     3,453,912  82 Linux swap / Solaris
/dev/sda6    *    371,326,536 1,683,901,169 1,312,574,634  83 Linux
/dev/sda7       1,683,901,233 1,692,913,634     9,012,402  82 Linux swap / Solaris
/dev/sda8       1,692,913,698 1,710,954,629    18,040,932  83 Linux


blkid -c /dev/null: ____________________________________________________________

sda1: LABEL="Mint" UUID="02cdc07d-a890-408f-8d6a-eafb1ea178e5" SEC_TYPE="ext2" TYPE="ext3" 
sda5: UUID="e0699dae-f711-4de0-9ca8-5d322a94f1ac" TYPE="swap" 
sda6: LABEL="Ubuntu" UUID="65382740-bdee-4bd0-942b-7144b09d4f52" TYPE="ext4" 
sda7: UUID="4c641559-3d0a-4488-a64e-2bfaa8d6c0b5" TYPE="swap" 
sda8: LABEL="ubuntu2" UUID="d8f379b7-1d1b-464b-a46c-b39b39b980db" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chieffox/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chieffox)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
##      altoptions=(single-user) single
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

title        Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria x64, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=02cdc07d-a890-408f-8d6a-eafb1ea178e5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4a044337-ddac-4e5f-ad0e-1bae7cc88992 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.28-11-generic
    .0GB: boot/initrd.img-2.6.28-16-generic
    .0GB: boot/vmlinuz-2.6.28-11-generic
    .0GB: boot/vmlinuz-2.6.28-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria x64, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set d8f379b7-1d1b-464b-a46c-b39b39b980db
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d8f379b7-1d1b-464b-a46c-b39b39b980db ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set d8f379b7-1d1b-464b-a46c-b39b39b980db
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d8f379b7-1d1b-464b-a46c-b39b39b980db ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=65382740-bdee-4bd0-942b-7144b09d4f52 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4c641559-3d0a-4488-a64e-2bfaa8d6c0b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 190.1GB: boot/grub/core.img
 190.1GB: boot/grub/grub.cfg
 190.1GB: boot/initrd.img-2.6.31-14-generic
 190.1GB: boot/initrd.img-2.6.31-15-generic
 190.1GB: boot/initrd.img-2.6.31-16-generic
 190.1GB: boot/vmlinuz-2.6.31-14-generic
 190.1GB: boot/vmlinuz-2.6.31-15-generic
 190.1GB: boot/vmlinuz-2.6.31-16-generic
 190.1GB: initrd.img
 190.1GB: initrd.img.old
 190.1GB: vmlinuz
 190.1GB: vmlinuz.old

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set d8f379b7-1d1b-464b-a46c-b39b39b980db
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
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set d8f379b7-1d1b-464b-a46c-b39b39b980db
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d8f379b7-1d1b-464b-a46c-b39b39b980db ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set d8f379b7-1d1b-464b-a46c-b39b39b980db
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d8f379b7-1d1b-464b-a46c-b39b39b980db ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria x64, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro single
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux /boot/vmlinuz-2.6.31-15-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro single
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=65382740-bdee-4bd0-942b-7144b09d4f52 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=d8f379b7-1d1b-464b-a46c-b39b39b980db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e0699dae-f711-4de0-9ca8-5d322a94f1ac none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=4c641559-3d0a-4488-a64e-2bfaa8d6c0b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 866.7GB: boot/grub/core.img
 866.7GB: boot/grub/grub.cfg
 866.7GB: boot/initrd.img-2.6.31-14-generic
 866.7GB: boot/vmlinuz-2.6.31-14-generic
 866.7GB: initrd.img
 866.7GB: vmlinuz

```

---

### Post by Keith Fox on 2010-01-06
> **Keith Fox said:**
> 
[LIST]
[*]I noticed there is no fstab folder in /etc
[/LIST]


Sorry about the confusion.  I thought for some reason fstab was a folder in /etc, but rather it is a file. Woops! :confused:

---

### Post by drs305 on 2010-01-06
> **Keith Fox said:**
> Thanks again for helping me out.  I never knew of this "Boot Info Script"  Is there any thread tools on this site so I can bookmark that post to my favorites?

Keith,

Actually, it would be best to bookmark it outside this forum using your browser's bookmarks. The link to the page to bookmark is:
[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")
This will point to the latest script.

If you really want to "bookmark" it within the Ubuntu forums, you can go the thread, then use the Thread Tools to Subscribe. I've always found it a bit odd, but you "activate" the subscription by selecting "Reset Fields". Now you will be subscribed to this thread and can access it with the top menu "Quick Links" then "Subscribed Threads". ...  But browser bookmarks are easier.

---

### Post by louieb on 2010-01-06
Now what is it you want to do next?  
I guess from post # 7 you want to use GRUB2 in sda6 and make it your main Ubuntu install. 

lol - drs305 is one of the forums main GRUB2 junkies. Just look at the links at the bottom of post # 11. To confirm what I have written next. 

Anyway boot to the Ubuntu install in sda6. 
Change the MBR to point to sda6 
```
sudo grub-install /dev/sda
```and  update the GRUB menu.
```
**sudo update-grub**
```and finally one last check.
```
**sudo grub-install --recheck /dev/sda**
```

---

### Post by Keith Fox on 2010-01-07
Louib:  I commanded in terminal what you said. I didn't see any errors, what do you think?  Can I delete my other ubuntu partition now?  I don't think it's necessary now that we fixed the GRUB 2 loader.  What do you think?  I did this while booted from sda6.
```

chieffox@chieffox-desktop:~$ sudo grub-install /dev/sda
[sudo] password for chieffox: 
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
chieffox@chieffox-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint 7 Gloria - x64 Edition (7) on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda8
done
chieffox@chieffox-desktop:~$ sudo grub-install --recheck /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda

```

---

### Post by louieb on 2010-01-07
Run the boot info script again - look at the very  top  If it now says its looking in [COLOR=Sienna]partition # 6[/COLOR] - you have what you want -  and you can go ahead and  use partition sda8 for something else or delete it.  

```
============================= Boot Info Summary: 

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in [COLOR=Sienna]partition #8 [/COLOR]for /boot/grub.
```

---

### Post by Keith Fox on 2010-01-07
Thank you to everybody in the forum

---

### Post by Keith Fox on 2010-04-25
> **louieb said:**
> Now what is it you want to do next?  
I guess from post # 7 you want to use GRUB2 in sda6 and make it your main Ubuntu install. 

lol - drs305 is one of the forums main GRUB2 junkies. Just look at the links at the bottom of post # 11. To confirm what I have written next. 

Anyway boot to the Ubuntu install in sda6. 
Change the MBR to point to sda6 
```
sudo grub-install /dev/sda
```and  update the GRUB menu.
```
**sudo update-grub**
```and finally one last check.
```
**sudo grub-install --recheck /dev/sda**
```


what to do now that I can't boot to sda6 anymore even though my files are still there?

See my new bootinfoscript results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 7 Gloria - x64 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5e6d5181

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   371,326,409   371,326,347  83 Linux
/dev/sda3         371,326,410 1,774,813,004 1,403,486,595   5 Extended
/dev/sda5       1,771,359,093 1,774,813,004     3,453,912  82 Linux swap / Solaris
/dev/sda6         371,326,536 1,252,668,374   881,341,839  83 Linux
/dev/sda7       1,683,901,233 1,692,913,634     9,012,402  82 Linux swap / Solaris
/dev/sda8       1,252,668,438 1,671,820,289   419,151,852  83 Linux
/dev/sda9       1,671,820,353 1,683,901,169    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        02cdc07d-a890-408f-8d6a-eafb1ea178e5   ext3       Mint                          
/dev/sda5        e0699dae-f711-4de0-9ca8-5d322a94f1ac   swap                                     
/dev/sda6        65382740-bdee-4bd0-942b-7144b09d4f52   ext4       Ubuntu                        
/dev/sda7        4c641559-3d0a-4488-a64e-2bfaa8d6c0b5   swap                                     
/dev/sda8        58b09602-9d1a-44f2-adb7-6d7e38e16379   ext4       juan                          
/dev/sda9        7a84ba19-73c5-4aa6-b385-a607b58a7de5   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
##      altoptions=(single-user) single
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

title        Linux Mint 7 Gloria x64, kernel 2.6.28-18-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Linux Mint 7 Gloria x64, kernel 2.6.28-18-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Linux Mint 7 Gloria x64, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=02cdc07d-a890-408f-8d6a-eafb1ea178e5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4a044337-ddac-4e5f-ad0e-1bae7cc88992 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 166.0GB: boot/grub/menu.lst
   1.5GB: boot/grub/stage2
   1.6GB: boot/initrd.img-2.6.28-11-generic
 124.4GB: boot/initrd.img-2.6.28-16-generic
 124.5GB: boot/initrd.img-2.6.28-18-generic
   1.5GB: boot/vmlinuz-2.6.28-11-generic
   1.6GB: boot/vmlinuz-2.6.28-16-generic
 124.4GB: boot/vmlinuz-2.6.28-18-generic
 124.5GB: initrd.img
 124.4GB: initrd.img.old
 124.4GB: vmlinuz
   1.6GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 65382740-bdee-4bd0-942b-7144b09d4f52
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
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria x64, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=65382740-bdee-4bd0-942b-7144b09d4f52 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4c641559-3d0a-4488-a64e-2bfaa8d6c0b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 293.5GB: boot/grub/core.img
 329.9GB: boot/grub/grub.cfg

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root=(hd0,8)
search --no-floppy --fs-uuid --set 58b09602-9d1a-44f2-adb7-6d7e38e16379
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 58b09602-9d1a-44f2-adb7-6d7e38e16379
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=58b09602-9d1a-44f2-adb7-6d7e38e16379 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 58b09602-9d1a-44f2-adb7-6d7e38e16379
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=58b09602-9d1a-44f2-adb7-6d7e38e16379 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 58b09602-9d1a-44f2-adb7-6d7e38e16379
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=58b09602-9d1a-44f2-adb7-6d7e38e16379 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 58b09602-9d1a-44f2-adb7-6d7e38e16379
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=58b09602-9d1a-44f2-adb7-6d7e38e16379 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-18-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-18-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-18-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-18-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria x64, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda1 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Linux Mint 7 Gloria x64, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 02cdc07d-a890-408f-8d6a-eafb1ea178e5
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=58b09602-9d1a-44f2-adb7-6d7e38e16379 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=7a84ba19-73c5-4aa6-b385-a607b58a7de5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda8: Location of files loaded by Grub: ===================


 667.2GB: boot/grub/core.img
 650.5GB: boot/grub/grub.cfg
 641.9GB: boot/initrd.img-2.6.31-14-generic
 642.2GB: boot/initrd.img-2.6.31-20-generic
 641.9GB: boot/vmlinuz-2.6.31-14-generic
 641.9GB: boot/vmlinuz-2.6.31-20-generic
 642.2GB: initrd.img
 641.9GB: initrd.img.old
 641.9GB: vmlinuz
 641.9GB: vmlinuz.old
```

---

### Post by oldfred on 2010-04-26
The new results shows you updated the grub.cfg in sda6 and it did not even find its own system, so it seems that there is a problem with the install in sda6.

You could try copying the stanza from your old results for sda6 into 40_custom for sda8 & sudo update-grub to add the entry, but I do not know it that will work.

I expect you will have to chroot into your system from sda8 into sda6 and run repairs from that, but I am not sure what to fix.

drs305 chroot to reinstall grub2 but I do not think reinstalling grub2 will be all, you will need additional update commands to try to get it fixed.
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

---

### Post by Keith Fox on 2010-04-26
Yes thank you for your response.  I am not sure what exactly went corrupt, but all I was doing was an update through the GUI method of updating (Synaptic). When I rebooted I couldn't see my OS in the Grub which appears to be the old style Grub 1 even though it used to be Grub2.  Yesterday before I posted my question, I tried installing Ubuntu in a seperate partition, thinking that would fix my OS at boot, but still not recognized even after installing Grub 2... (I think I did that correctly).

Anyway thanks @oldfred for your advice I will try that. But looking at drs305's post #12 you linked in the 17th post in this thread, should I make it sda6 instead of sda7 in the directions?

---

### Post by oldfred on 2010-04-26
Your installs are in sda6 and the new one in sda8. You are currently booting thru sda8 so would have to update that with an entry for booting sda6. But since sda6 looks like it has issues I am not hopeful that it will boot on its own. You may have to chroot into it and run repairs.

---

### Post by Keith Fox on 2010-04-27
OK looking at the Grub2 directions for Method 3 (CHROOT). I finished through that thoroughly and correctly.  When I reboot there is no sda6 Ubuntu which is my normal system which came up missing after an update I believe.  What's weird is when I command to:* sudo update-grub *
The sda6 Ubuntu is found in the list, but when reboot it's not in the grub menu.  I'm not sure about how to do the 40_custom file, maybe I will read up on that and try that soon. I thought for sure the CHROOT method would fix this. 

Also interesting I found this out:
When commanding: 
     *grub-probe -t device /boot/grub*

I get these strange results:  
    error: cannot open `/dev/sda'
    error: cannot open `/dev/sda'
    /dev/sda1

---

### Post by oldfred on 2010-04-27
this is drs305 chroot to uninstall grub & reinstall:
drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

But I would add these command while in the sda6 chroot to try to update it.

apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade

---

### Post by Keith Fox on 2010-04-27
> **oldfred said:**
> this is drs305 chroot to uninstall grub & reinstall:
drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)

But I would add these command while in the sda6 chroot to try to update it.

apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade

Well I tried your 3 commands while in chroot, but problem is that while in chroot, the machine is booted from the LiveCD and not the installation, so I got an error saying something about a mount missing. I forget exactly which one it was, but I did already mount the following: dev, proc,sys, usr... all before entering chroot.

So anyways, While in Linux Mint I can command 
```
**sudo update-grub**
Updating /boot/grub/grub.cfg ...
Found Debian background: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.28-18-generic
Found initrd image: /boot/initrd.img-2.6.28-18-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
**Found Ubuntu 9.10 (9.10) on /dev/sda6**
Found Ubuntu 9.10 (9.10) on /dev/sda8
done
```

Notice it says it found sda6 Ubuntu which is what I wanted, but I reboot and oh it's not in the list, but sda8 is...shheeessh

---

