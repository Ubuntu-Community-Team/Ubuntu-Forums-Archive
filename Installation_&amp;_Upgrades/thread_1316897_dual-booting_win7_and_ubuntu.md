---
title: "dual-booting win7 and ubuntu"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by unisol on 2009-11-06
this is the scenario: i have windows7 installed on a single partition 500 gb hd. i want to install ubuntu as dual boot. (i have done this before but not with win7.) can i go into disk management and reduce the win 7 volume by say 50 gb. format it fat32 and install ubuntu. and still have dual-boot? thanks in advance. i plan on using either ubuntu 9.04 or 9.10.

---

### Post by t.rei on 2009-11-06
I am running a dual boot kubuntu/w7 on my computer. 
If you do any changes to the windows partitions do it in the windows. I am not shure what windows does, but I expect them to do the usual: fight all existance of anything else but windows.

So, yes, dual boot works (altho I hardly ever boot into windows7) but I would use windows to make space on the HD. (I don't even know if windows comes with the software to do that? sry). After having the space for your linux, you can format it during installation. No problem.

---

### Post by Killbot956 on 2009-11-07
Well I managed to install Windows 7 and re-installed GrUB. The only problem now is, when I boot into Ubuntu it will not auto mount my other partitins. When I open gparted, sda, which has my Ubuntu partition, is mostly unallocated space. When I use Terminal and run fdisk -l it shows me all the partions on the disk. I have checked the fstab file and nothing has changed. All the auto mount partitions are still on the file. When I go to 'Places' on the top panel I can see most of the partitions on sda. I can log into the Windows system fine and all the other partitions are visible and accessible. Any suggestions:confused:??

---

### Post by Dukkhey on 2009-12-12
first of all, hello everyone! :) this is my first post.
well... ill get right to it then. my linux experience started with ubuntu 9.10. works almost fine, except for a few kinks (some freezing at start-up but afterwards works just fine)
my main probl is that i'd like to dual boot with a win 7. but i don't know anything on the subject. i've looked up some tutorials on how to do that and one of them(the only one i could actually understand) said that i should back up my grub boot menu with the command lin sudo gedit /boot/grub/menu.lst 
i tried that and all i get is an empty file. i tried to manually back it up by going to the hard drive and finding the file. there's nothing in the directory.
could you please give me a step by stept tutorial on how to dual boot ubuntu 9/10 and windows7 with linux already installed?

thanks in advance!

---

### Post by darkod on 2009-12-12
> **unisol said:**
> this is the scenario: i have windows7 installed on a single partition 500 gb hd. i want to install ubuntu as dual boot. (i have done this before but not with win7.) can i go into disk management and reduce the win 7 volume by say 50 gb. format it fat32 and install ubuntu. and still have dual-boot? thanks in advance. i plan on using either ubuntu 9.04 or 9.10.

Yes, shrink your win7 partition with the Disk Management but do NOT create any partition(s) in the unallocated free space created with the shrink. Why do people insist creating ntfs/fat32 partitions for ubuntu when it doesn't use them?
Leave the space as unallocated. Boot win7 few times to make sure it's happy with the shrink, then just boot with ubuntu cd, select Install Ubuntu, and let it use Largest Available Free space. It will install itself into the unallocated space creating / and swap partitions.

---

### Post by darkod on 2009-12-12
> **Dukkhey said:**
> first of all, hello everyone! :) this is my first post.
well... ill get right to it then. my linux experience started with ubuntu 9.10. works almost fine, except for a few kinks (some freezing at start-up but afterwards works just fine)
my main probl is that i'd like to dual boot with a win 7. but i don't know anything on the subject. i've looked up some tutorials on how to do that and one of them(the only one i could actually understand) said that i should back up my grub boot menu with the command lin sudo gedit /boot/grub/menu.lst 
i tried that and all i get is an empty file. i tried to manually back it up by going to the hard drive and finding the file. there's nothing in the directory.
could you please give me a step by stept tutorial on how to dual boot ubuntu 9/10 and windows7 with linux already installed?

thanks in advance!

You are using grub2 most probably with 9.10 and that's why menu.lst doesn't exist. No need to back up the grub files, you will just have to restore grub2 after win7 deletes it. The grub2 config files will still remain on your ubuntu partition.

---

### Post by Dukkhey on 2009-12-12
this is what i did once: shrank the allocated space for ubuntu and installed win 7 on unallocated space. what happened then is that the only thing that would boot and be recognized was win 7. as i understand it i have to restore grub2 afterwards. how do i do that?

---

### Post by darkod on 2009-12-12
> **Dukkhey said:**
> this is what i did once: shrank the allocated space for ubuntu and installed win 7 on unallocated space. what happened then is that the only thing that would boot and be recognized was win 7. as i understand it i have to restore grub2 afterwards. how do i do that?

If you are sure it's grub2, boot with the ubuntu 9.10 cd, Try Ubuntu option and in terminal execute:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

NOTE: The above commands assume ubuntu is on /dev/sda and your root partition is /dev/sda5. To check your partition first in terminal run:
sudo fdisk -l (small L)

Most probably you have one large root partition and smaller swap partition. Use the name for the root partition in the command above. That's all you need to do.

---

### Post by Dukkhey on 2009-12-13
well... i managed to install win 7, retrieved the grub with the commands darkod posted. thanks very much for that. the problem now is that the pc will only boot ubuntu. wasn't i supposed to get a screen where i could choose between the two, or something?

---

### Post by darkod on 2009-12-13
> **Dukkhey said:**
> well... i managed to install win 7, retrieved the grub with the commands darkod posted. thanks very much for that. the problem now is that the pc will only boot ubuntu. wasn't i supposed to get a screen where i could choose between the two, or something?

The first thing to try is in ubuntu in terminal do:
sudo update-grub

You should notice if it detects win7. Reboot and check if it worked. If that doesn't work, we'll see.

---

### Post by Dukkhey on 2009-12-13
> **darkod said:**
> The first thing to try is in ubuntu in terminal do:
sudo update-grub

You should notice if it detects win7. Reboot and check if it worked. If that doesn't work, we'll see.
  almost there... i'm getting the boot screen now. there are about 6 options for ubuntu(actually just a couple that keep repeating ubuntu 2.6.31 and recovery mode) and two memory test options, but no windows 7..

edit:

this is what i get with sudo update-grub

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-16-generic-pae
Found kernel: /boot/vmlinuz-2.6.31-15-generic-pae
Found kernel: /boot/vmlinuz-2.6.31-14-generic-pae
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by darkod on 2009-12-13
> **Dukkhey said:**
> almost there... i'm getting the boot screen now. there are about 6 options for ubuntu(actually just a couple that keep repeating ubuntu 2.6.31 and recovery mode) and two memory test options, but no windows 7..

OK. The options for ubuntu are different kernels, 31-14, -15 and -16, all with normal and recovery mode entries.
Do you know on which partition your win7 is? If you do, you can try adding the entry manually. But the fact that grub2 is not picking it up, might mean that the boot process for win7 is not right, so even manual entry wouldn't work.
Not to guess, I think it's time to run the boot info script. Download it from my signature, put it on desktop for example and execute in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

That will create results.txt file. Copy the content here and please put CODE tags around it for easier reading (with the text selected click the # button in the toolbar above). That will detail your boot process.

---

### Post by Dukkhey on 2009-12-13
result for boot info script :) 

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x47e247e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    30,860,864    30,860,802  83 Linux
/dev/sda2    *     30,860,865    90,349,559    59,488,695   7 HPFS/NTFS
/dev/sda3         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris
/dev/sda4          90,349,560   149,838,254    59,488,695   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc4e21ee7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="e9006b6b-bb7d-4a15-b62c-b88394a7c204" TYPE="ext4" 
/dev/sda2: UUID="1EEDF746394F8170" TYPE="ntfs" 
/dev/sda4: UUID="2B8C1A87527BC2FA" TYPE="ntfs" 
/dev/sda5: UUID="6c451ca4-7c50-4d11-94d1-bfbda6a60790" TYPE="swap" 
/dev/sdb1: UUID="B6D430AFD43073A9" LABEL="FreeAgent Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e9006b6b-bb7d-4a15-b62c-b88394a7c204

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic-pae
uuid        e9006b6b-bb7d-4a15-b62c-b88394a7c204
kernel        /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic-pae

title        Ubuntu 9.10, kernel 2.6.31-16-generic-pae (recovery mode)
uuid        e9006b6b-bb7d-4a15-b62c-b88394a7c204
kernel        /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic-pae

title        Ubuntu 9.10, kernel 2.6.31-15-generic-pae
uuid        e9006b6b-bb7d-4a15-b62c-b88394a7c204
kernel        /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic-pae

title        Ubuntu 9.10, kernel 2.6.31-15-generic-pae (recovery mode)
uuid        e9006b6b-bb7d-4a15-b62c-b88394a7c204
kernel        /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic-pae

title        Ubuntu 9.10, kernel 2.6.31-14-generic-pae
uuid        e9006b6b-bb7d-4a15-b62c-b88394a7c204
kernel        /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic-pae

title        Ubuntu 9.10, kernel 2.6.31-14-generic-pae (recovery mode)
uuid        e9006b6b-bb7d-4a15-b62c-b88394a7c204
kernel        /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic-pae

title        Chainload into GRUB 2
root        e9006b6b-bb7d-4a15-b62c-b88394a7c204
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        e9006b6b-bb7d-4a15-b62c-b88394a7c204
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set e9006b6b-bb7d-4a15-b62c-b88394a7c204
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
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9006b6b-bb7d-4a15-b62c-b88394a7c204
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9006b6b-bb7d-4a15-b62c-b88394a7c204
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9006b6b-bb7d-4a15-b62c-b88394a7c204
    linux    /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9006b6b-bb7d-4a15-b62c-b88394a7c204
    linux    /boot/vmlinuz-2.6.31-15-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9006b6b-bb7d-4a15-b62c-b88394a7c204
    linux    /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9006b6b-bb7d-4a15-b62c-b88394a7c204
    linux    /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic-pae
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
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e9006b6b-bb7d-4a15-b62c-b88394a7c204 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6c451ca4-7c50-4d11-94d1-bfbda6a60790 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd.img-2.6.31-14-generic-pae
    .0GB: boot/initrd.img-2.6.31-15-generic-pae
    .0GB: boot/initrd.img-2.6.31-16-generic-pae
    .0GB: boot/vmlinuz-2.6.31-14-generic-pae
    .0GB: boot/vmlinuz-2.6.31-15-generic-pae
    .0GB: boot/vmlinuz-2.6.31-16-generic-pae
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
timeout 2
setgrubdevice # This is compulsory
#sgdgfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


#title Inicio normal / Normal Boot 
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs

#title Soporte de accesibilidad / Accesibility Support -->
#configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

#title Normal boot. Kernel is aware of Boot device
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
#initrd $(grub_device)/initramfs

#title Normal boot. Selecting kernel and initrd files depending on grub_device
#kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs_$(grub_device_string)

#title Selecthd test
#configfile $(grub_device)/boot/grub/choose/selecthd.lst

#title findp test
#configfile $(grub_device)/boot/grub/choose/selectpart.lst
#title set SGD variables and boot SGD
#
#configfile $(grub_device)/boot/sgd/menu.lst

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
```

---

### Post by darkod on 2009-12-13
> **Dukkhey said:**
> result for boot info script :) 


You have a strange mix of grub1 and grub2 files. menu.lst is not used by the new grub2.

In terminal open:
sudo gedit /boot/grub/menu.lst

and at the end add:

title Windows 7
rootnoverify (hd0,1)
makeactive
chainloader +1

Save and close the file. Reboot and see how it goes.

---

### Post by Dukkhey on 2009-12-13
> **darkod said:**
> You have a strange mix of grub1 and grub2 files. menu.lst is not used by the new grub2.

In terminal open:
sudo gedit /boot/grub/menu.lst

and at the end add:

title Windows 7
rootnoverify (hd0,1)
makeactive
chainloader +1

Save and close the file. Reboot and see how it goes.

  added the whole thing and rebooted. nothing happened. linux booted normally. :P

---

### Post by darkod on 2009-12-13
> **Dukkhey said:**
> added the whole thing and rebooted. nothing happened. linux booted normally. :P

Sorry, I should have added if it doesn't work, do
sudo update-grub

again and reboot to check if that helps.

---

### Post by Dukkhey on 2009-12-13
> **darkod said:**
> Sorry, I should have added if it doesn't work, do
sudo update-grub

again and reboot to check if that helps.

still nothing. updated grub and rebooted twice. nothing happened. should we swithc to pm, or is it ok if we spam here?:P

---

### Post by darkod on 2009-12-13
> **Dukkhey said:**
> still nothing. updated grub and rebooted twice. nothing happened. should we swithc to pm, or is it ok if we spam here?:P

Well, I don't have many more ideas. :( I'm still confused how did you end up having menu.lst at all. I wonder if you should just delete it. Because you also have grub.cfg and that's what you're supposed to have with grub2.

It seems you were trying something with Super Grub Disk right? :( It just makes confusion, you don't need anything except grub2 from Ubuntu 9.10.

I would try going into /boot/grub and deleting menu.lst (notice if there is grub.cfg there).
Then also open /dev/sdb1 (your 1TB drive) and go into boot/grub folder and delete menu.lst that's there too.

And in future unless you really need some special features from Super Grub Disk and you know what you're doing, do NOT use it. There are people here who advocate it but they're nowhere to be found to help later. :) Just stick to the standard grub2, it makes it easier to help.

After you delete both menu.lst files as stated above, run sudo update-grub once more. See if it lists win7 as found.

---

### Post by darkod on 2009-12-13
Also you need to go into /dev/sda2 and delete grldr file, that's grub loader I guess from Super Grub too. It will probably confuse things since it's at the same location as win7 boot files. In fact, maybe that's why grub2 can't "see" the win7 boot files.

---

### Post by Dukkhey on 2009-12-13
> **darkod said:**
> Also you need to go into /dev/sda2 and delete grldr file, that's grub loader I guess from Super Grub too. It will probably confuse things since it's at the same location as win7 boot files. In fact, maybe that's why grub2 can't "see" the win7 boot files.

true. i downloaded the supergrub progr you were talking about, but i never really ran it. i only unpacked it and read the reame. it's also true that at first i didn't have a menu.lst in the grub directory in the root of sda1 and don't really know when it appeared. the real problem with that file is that i can't really delete it. not even if i boot from the ubuntu cd.

a thought that i had (i'm really not sure about this but it's something that could make sense from a logical perspective) couldn't the files from grub 1 have been created when i executed "sudo grub-install --root-directory=/mnt/ /dev/sda"? should't the comand have been "sudo grub2-install --root-directory=/mnt/ /dev/sda"?

---

### Post by darkod on 2009-12-13
> **Dukkhey said:**
> true. i downloaded the supergrub progr you were talking about, but i never really ran it. i only unpacked it and read the reame. it's also true that at first i didn't have a menu.lst in the grub directory in the root of sda1 and don't really know when it appeared. the real problem with that file is that i can't really delete it. not even if i boot from the ubuntu cd.

a thought that i had (i'm really not sure about this but it's something that could make sense from a logical perspective) couldn't the files from grub 1 have been created when i executed "sudo grub-install --root-directory=/mnt/ /dev/sda"? should't the comand have been "sudo grub2-install --root-directory=/mnt/ /dev/sda"?

No, the command is grub-install. One way to delete that file as root is from terminal, but YOU HAVE TO BE VERY CAREFUL!!!
Boot your hdd ubuntu (not cd), and in terminal you should be able to delete it with:
sudo rm /boot/grub/menu.lst

For grldr on /dev/sda2 and menu.lst on /dev/sdb1 it gets more complicated because most probably those partitions are not mounted by default.

In termnal first make temp folders for them:
mkdir /media/tempsda2
mkdir /media/tempsdb1

Then mount them:
sudo mount /dev/sda2 /media/tempsda2
sudo mount /dev/sdb1 /media/tempsdb1

In Places open those folder and check if the file grldr is in /media/sda2 and the folder boot with inside folder grub with inside file menu.lst is in /media/tempsdb1. If yes, delete them with:
sudo rm /media/tempsda2/grldr
sudo rm /media/tempsdb1/boot/grub/menu.lst

Do you follow the "logic"? :) I haven't done anything like this before but if you are careful with the commands you should be OK. I guess grldr and menu.lst settled there just with unpacking supergrub.

After all of the above is done, update grub2 again with:
sudo update-grub

If any of these files were actually used by your grub2, and it breaks when deleting them, just get your 9.10 cd (not supergrub), boot with Try Ubuntu option and do the commands to restore grub2 as you did earlier. But this time it should not create menu.lst, I think it's from supergrub and making confusion now.

---

### Post by Dukkhey on 2009-12-13
i had no problem deleting the files, but when i executed sudo update-grub it told me that menu.lst does not exist and if i want to create it. i said no.

---

### Post by darkod on 2009-12-13
> **Dukkhey said:**
> i had no problem deleting the files, but when i executed sudo update-grub it told me that menu.lst does not exist and if i want to create it. i said no.

Good, but did it write something like Generating grub.cfg? It needs to update that file too, it needs to know to use it. :)

I suspect it might not even boot without menu.lst if it didn't generate grub.cfg. In that case just reinstall grub2 with those two commands you already used earlier to restore it.

See what happens and reinstall grub2 if needed.

---

