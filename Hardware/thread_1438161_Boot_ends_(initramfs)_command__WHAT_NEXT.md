---
title: "Boot ends (initramfs) command  WHAT NEXT"
date: 2010-03-24
forum: Hardware
---

### Post by eaglemystic69 on 2010-03-24
Hi,

Im on a HPG71, 9.10 fresh install, dual boot with Windows7 installed 1st. Jaunty/ grub works fine on 2 other machines . . . not Karmic.  Im mainly a GUI guy. . . .

Below are the recommended outputs I have seen asked in threads. 

This gets me in manually everytime (for two weeks):
1. ls 
2. set prefix=(hdX,Y)/boot/grub 
3*. set root=(hdX,Y) 
4. set 
5. ls /boot 
6. insmod /boot/grub/linux.mod 
7*. linux /vmlinuz root=/dev/sdxY ro 
8. initrd /initrd.img 
9. boot 
=====================================
/boot/grub/menu.lst . . . came up empty


=====================================
sudo hexdump -s 0x410 -n 2 /dev/sda5
0000410 00be 
0000412


=====================================
sudo blkid
/dev/sda1: UUID="E09ADDD29ADDA4F6" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="8C80C01180C00424" LABEL="Windows7" TYPE="ntfs" 
/dev/sda4: UUID="5C483C78483C534E" LABEL="Storage" TYPE="ntfs" 
/dev/sda5: UUID="e24d7934-1843-4bda-924c-d655df287c84" TYPE="ext4" 


=====================================
fstab output
proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=e24d7934-1843-4bda-924c-d655df287c84 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/Windows7 ntfs-3g defaults,locale=en_US.UTF-8 0 0


=====================================
Apologies for not knowing howto make this in its own scrolled window.
Boot Info Script 0.55 dated February 15th, 2010 

Boot Info Summary: 

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #5 for /boot/grub.

sda1: __________________________________________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /bootmgr /Boot/BCD

sda2: __________________________________________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________

File system: Extended Partition
Boot sector type: -
Boot sector info: 

sda5: __________________________________________________

File system: ext4
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda5 and 
looks at sector 69311051 of the same hard drive for 
core.img, but core.img can not be found at this 
location.
Operating System: Ubuntu 9.10
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 

=========================== Drive/Partition Info: =============================

Drive: sda __________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe7e8e0a0

Partition Boot Start End Size Id System

/dev/sda1 * 2,048 409,599 407,552 7 HPFS/NTFS
/dev/sda2 433,755 61,866,314 61,432,560 7 HPFS/NTFS
/dev/sda3 61,882,380 124,391,294 62,508,915 5 Extended
/dev/sda5 * 61,882,443 124,391,294 62,508,852 83 Linux
/dev/sda4 124,391,295 625,137,344 500,746,050 7 HPFS/NTFS


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL 

/dev/sda1 E09ADDD29ADDA4F6 ntfs SYSTEM 
/dev/sda2 8C80C01180C00424 ntfs Windows7 
/dev/sda4 5C483C78483C534E ntfs Storage 
/dev/sda5 e24d7934-1843-4bda-924c-d655df287c84 ext4 

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

/dev/sda5 / ext4 (rw,errors=remount-ro)
/dev/sda4 /media/Storage fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 /media/Windows7 fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

---

### Post by eaglemystic69 on 2010-03-26
Can anyone help me.  I'ld rather not reinstall my customized system to remedy the issue.

---

### Post by Brandon Williams on 2010-03-29
Please give a bit more detail about what the problem is that you're trying to solve. Is it that the machine will not boot on its own, but that it will boot just fine if you type in the list of 9 commands from your first post at the grub command prompt? If so, it would be good for you to run 'sudo update-grub' and then post your /boot/grub/grub.cfg file here so that we can verify the contents. Also, please post your /etc/default/grub file.

---

### Post by eaglemystic69 on 2010-03-29
Thanks Brandon for the help, its been months using the 9 commands to get in.  The other suggestions at "https://help.ubuntu.com/community/Grub2" did not permanently fix the issue.  And I did not know were to start with the grub.cfg file.

I see "insmod ext2" and know (hd0,5) is now ext4.  Does that matter.  

##################################
GRUB.CFG

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
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
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e24d7934-1843-4bda-924c-d655df287c84
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=e24d7934-1843-4bda-924c-d655df287c84 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e09addd29adda4f6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8c80c01180c00424
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

#########################################
#########################################
/boot/grub/grub.cfg

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by Brandon Williams on 2010-03-29
Based on all the detail you've provided, it looks like this should be working. At least nothing stands out as being obviously incorrect. Have you tried reinstalling grub to the mbr? After you boot into the system and log in, run 'sudo grub-install /dev/sda' and then 'sudo update-grub'.

The one other thing that occurs to me is that I see you have both the generic and the generic-pae kernels installed. Which one does /vmlinuz link to? If /vmlinuz links to boot/vmlinuz-2.6.31-19-generic, then you might want to remove linux-image-2.6.31-20-generic-pae, which is currently set as your default kernel. I doubt this is it, but it's worth double-checking.

---

