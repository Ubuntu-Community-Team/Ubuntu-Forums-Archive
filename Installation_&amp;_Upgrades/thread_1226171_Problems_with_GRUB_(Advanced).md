---
title: "Problems with GRUB (Advanced)"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Arthur_D on 2009-07-29
Okay, let me tell you the whole story.

I had a desktop computer with a P-ATA drive with Windows XP and Ubuntu 9.04 installed, working quite well.

I ordered myself a new hard drive with S-ATA, and decided to let the P-ATA drive be as it was, except for that I wanted it to be the secondary drive. I plugged in the S-ATA drive, and configured my BIOS to use it as primary boot drive, and the P-ATA as secondary. I installed Windows XP on the new drive, and then Ubuntu 9.10 Pre-Alpha 3 on it as well.

The S-ATA drive is set up with Windows XP on 1 (NTFS), /home on 5 (ext4), swap on 6 (swap) and / on 7 (ext4). Windows XP booted fine, but GRUB didn't show up, so I was a little worried. But I figured XP must have overridden GRUB after I had to use the XP CD to repair the installation after a few incidents with NVIDIA drivers.

So, I tried to use Super Grub Disk to get GRUB back on the S-ATA drive. I selected "Windows Chainloads Grub!" and selected firstly / on 7 (ext4), and afterwards /home on 5 (ext4). But I got just an error message telling me it didn't find any of the GRUB files, and the error message number was 15.

Well, I tried booting anyways, and GRUB showed up. The problem was that it booted from my P-ATA drive, so I went into BIOS to check this out. Everything seemed fine, as the S-ATA drive was first on the boot list. So I tried to change settings to use S-ATA as sole boot drive.

Then I got a GRUB error message with the number 21. I figured I was stuck, and so went here to ask for expert help. Quite hard to follow me, maybe, but if you need clarifications just ask, and I'll try to explain it in a better way.

Thank you for reading all this. ;)

---

### Post by stlsaint on 2009-07-29
well one easy fix would be to do a clean sweep on both drives and do a fresh install of both systems...i also dual boot and i am farily successful! (using 3 operating systems on one drive):D
but should you choose not to i would uninstall ubuntu and re-install so that grub has the chance to re-add its self to winxp bootloader(bcd if using vista)! do this on your sata drive...my experience shows that ubuntu and sata get along great!!

---

### Post by Arthur_D on 2009-07-29
Well, I might go for the second suggestion.
But there should really be an easy fix for this... how many times haven't people problems with getting GRUB back....

---

### Post by presence1960 on 2009-07-29
before you remove any OS's let's see exactly what you have on your machine  and how it boots. If you can't boot into Ubuntu boot the Live CD. Choose "try ubuntu without any changes...", when the desktop loads download the Boot Info Script 0.32 from here to the desktop: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)
Open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on your desktop. This will contain the info on your setup and boot process. Paste the entire contents of the file back here. Then we'll see exactly what is going on there.

---

### Post by presence1960 on 2009-07-29
> **stlsaint said:**
> well one easy fix would be to do a clean sweep on both drives and do a fresh install of both systems...i also dual boot and i am farily successful! (using 3 operating systems on one drive):D
but should you choose not to i would uninstall ubuntu and re-install so that grub has the chance to re-add its self to winxp bootloader(bcd if using vista)! do this on your sata drive...my experience shows that ubuntu and sata get along great!!

you don't have to reinstall to restore GRUB. Just do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.


```

in most cases reinstalling should be the option of last resort.

---

### Post by Arthur_D on 2009-07-29
Well, I got it working, silly me.
Now I just need to get my two Windows XP installations back into GRUB. And I need Ubuntu 9.10 Pre-Alpha 3 on my S-ATA drive to use the 100 GB's worth of space on the other partition as home folder.
And eventually, I may need help installing ndiswrapper again to get my wireless card to work (I ran into trouble when running 'make').

Thanks a lot for your support; sorry for not trying more before asking for help.

---

### Post by presence1960 on 2009-07-29
> **Arthur_D said:**
> Well, I got it working, silly me.
Now I just need to get my two Windows XP installations back into GRUB. And I need Ubuntu 9.10 Pre-Alpha 3 on my S-ATA drive to use the 100 GB's worth of space on the other partition as home folder.
And eventually, I may need help installing ndiswrapper again to get my wireless card to work (I ran into trouble when running 'make').

Thanks a lot for your support; sorry for not trying more before asking for help.

no problem. Enjoy Ubuntu!

---

### Post by themusicdan on 2009-07-29
If you need any help getting Windows back in your grub, this thread may be of some assistance. I had more problems with Windows overwriting Ubuntu than the other way around, but just thought I would try to help. :)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by stlsaint on 2009-07-29
> **presence1960 said:**
> you don't have to reinstall to restore grub. Just do this:

```
1. Boot your computer up with ubuntu cd
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for ubuntu.
6. Type "setup (hd0)", to install grub to mbr, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install grub to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable cd.


```

in most cases reinstalling should be the option of last resort.



thanks for the heads up presence1960!!!

---

### Post by Arthur_D on 2009-08-10
I still get problems with Grub; I seem to have Grub 2 installed (though in Grub, it said it was 1.9.something), and therefore I couldn't find the menu.lst file the Ubuntu wiki said I had to find. Any ideas?

---

### Post by oldfred on 2009-08-10
Grub2 is part of the new 9.10, but is still in testing. It seems you still should boot with grub on your old drive with 9.04 and grub .97.  menu.lst is only part of old grub and what most instructions will have. grub2 uses a config file  that you do not edit but edit a separate file for special settings. I have not tried that yet.

You can chain boot from grub to grub2 and to your new windows on the new drive from the old drive with the standard grub and menu.lst.

---

### Post by Arthur_D on 2009-08-10
Great idea, but not sure on how to do that. I'm comfortable with the old Grub and dual-booting on the same drive, but not quadruple-booting on 2 drives.
Could you or anyone else please point me in the right direction?

Many thanks to all of you that have responded so far. :)

---

### Post by louieb on 2009-08-10
For some reason Grub legacy thinks a PATA drives will always be 1st in the boot order even when its not. Should be able to use the device.map file to set Grub straight.   

My PCs are either all PATA or all SATA so I haven't had to fix this.  
Heres a good thread that discusses dual booting with 2 drives.    [Dualboot Two Hard Drives - confused57]("http://ubuntuforums.org/showthread.php?t=179902")

When I do have GRUB questions and just want to see what works and what doesn't  I'll just boot a  [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") and play around till I find something that works.

Also take a look at the dual boot link in signature. Herman has a great deal of information about GRUB and how to use and fix it.

---

### Post by presence1960 on 2009-08-10
> **Arthur_D said:**
> I still get problems with Grub; I seem to have Grub 2 installed (though in Grub, it said it was 1.9.something), and therefore I couldn't find the menu.lst file the Ubuntu wiki said I had to find. Any ideas?
well lets see exactly what you have on your system and what your boot process looks like. Boot into Ubuntu (or if you can't boot the Live CD)when the desktop loads download the [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/") to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted here highlight all text pasted and click the # sign on the toolbar to place code tags around the text. We will see exactly what you have going on there.

P.S.  I quadruple boot from 1 SATA and 1 IDE HDD. I have Ubuntu 9.04, Sabayon 4.1, Mint 5 & Windows 7 RC. They all have a different version of GRUB (except Windows). The best bet is to use Ubuntu GRUB on MBR and chainload the other distros off of that. See [here]("http://ubuntuforums.org/showthread.php?p=7760690#post7760690") for more info.  But first thing's first let's see what you have.

---

### Post by Arthur_D on 2009-08-12
Okay, here is the result from running the boot_info_script:
```
============================= Boot Info Summary: ==============================

 => Grub2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for t/grub.
 => Grub2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for t/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f800000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   164,103,974   164,103,912   7 HPFS/NTFS
/dev/sda2         164,103,975   234,436,544    70,332,570   5 Extended
/dev/sda5         164,104,038   232,460,549    68,356,512  83 Linux
/dev/sda6         232,460,613   234,436,544     1,975,932  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07130713

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   390,636,539   390,636,477   7 HPFS/NTFS
/dev/sdb2         390,636,540   625,137,344   234,500,805   5 Extended
/dev/sdb5         390,636,603   585,954,809   195,318,207  83 Linux
/dev/sdb6         585,954,873   589,858,604     3,903,732  82 Linux swap / Solaris
/dev/sdb7         589,858,668   625,137,344    35,278,677  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2084A0A684A08040" TYPE="ntfs" 
/dev/sda5: UUID="46ec99b1-f458-408e-a402-f40e9bde3ae3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="c8cab7b0-db4c-4da3-a0e9-b2ef0bda97e5" TYPE="swap" 
/dev/sdb1: UUID="C640894F40894761" TYPE="ntfs" 
/dev/sdb5: UUID="2744bb9c-102a-4b83-a563-3d8594f150c1" TYPE="ext4" 
/dev/sdb6: UUID="5de1fe81-f145-40b7-a200-2c6ea5dfa494" TYPE="swap" 
/dev/sdb7: UUID="ae19d715-5ecf-4062-978a-98d74b314e5b" TYPE="ext4" 

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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\ubnldr.mbr="UNetbootin" 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=46ec99b1-f458-408e-a402-f40e9bde3ae3

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        46ec99b1-f458-408e-a402-f40e9bde3ae3
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        46ec99b1-f458-408e-a402-f40e9bde3ae3
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        46ec99b1-f458-408e-a402-f40e9bde3ae3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        46ec99b1-f458-408e-a402-f40e9bde3ae3
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        46ec99b1-f458-408e-a402-f40e9bde3ae3
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        46ec99b1-f458-408e-a402-f40e9bde3ae3
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, memtest86+
uuid        46ec99b1-f458-408e-a402-f40e9bde3ae3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c8cab7b0-db4c-4da3-a0e9-b2ef0bda97e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 112.8GB: boot/grub/menu.lst
 112.7GB: boot/grub/stage2
 112.8GB: boot/initrd.img-2.6.27-11-generic
 112.8GB: boot/initrd.img-2.6.28-11-generic
 112.8GB: boot/initrd.img-2.6.28-13-generic
 112.8GB: boot/vmlinuz-2.6.27-11-generic
 112.7GB: boot/vmlinuz-2.6.28-11-generic
 112.8GB: boot/vmlinuz-2.6.28-13-generic
 112.8GB: initrd.img
 112.8GB: initrd.img.old
 112.8GB: vmlinuz
 112.7GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 

=========================== sdb7/boot/grub/menu.lst: ===========================

title Windows XP
boot menu
rootnoverify (hd0,0)
makeactive
chainloader +1

title Windows XP (S-ATA)
boot menu
rootnoverify (hd1,0)
makeactive
chainloader +1

=========================== sdb7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd1,7)
search --no-floppy --fs-uuid --set ae19d715-5ecf-4062-978a-98d74b314e5b
if loadfont /usr/share/grub/ascii.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-3-generic" {
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set ae19d715-5ecf-4062-978a-98d74b314e5b
    linux    /boot/vmlinuz-2.6.31-3-generic root=UUID=ae19d715-5ecf-4062-978a-98d74b314e5b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-3-generic
}
menuentry "Ubuntu, Linux 2.6.31-3-generic (recovery mode)" {
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set ae19d715-5ecf-4062-978a-98d74b314e5b
    linux    /boot/vmlinuz-2.6.31-3-generic root=UUID=ae19d715-5ecf-4062-978a-98d74b314e5b ro single 
    initrd    /boot/initrd.img-2.6.31-3-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_otheros ###

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
menuentry "Microsoft Windows XP Home Edition" {
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2084a0a684a08040
    drivemap -s (hd0) $root
    chainloader +1
}

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda5)" {
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 46ec99b1-f458-408e-a402-f40e9bde3ae3
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro quiet splash 
    initrd /boot/initrd.img-2.6.28-13-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda5)" {
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 46ec99b1-f458-408e-a402-f40e9bde3ae3
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro single 
    initrd /boot/initrd.img-2.6.28-13-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)" {
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 46ec99b1-f458-408e-a402-f40e9bde3ae3
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro quiet splash 
    initrd /boot/initrd.img-2.6.28-11-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)" {
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 46ec99b1-f458-408e-a402-f40e9bde3ae3
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro single 
    initrd /boot/initrd.img-2.6.28-11-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (on /dev/sda5)" {
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 46ec99b1-f458-408e-a402-f40e9bde3ae3
    linux /boot/vmlinuz-2.6.27-11-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro quiet splash 
    initrd /boot/initrd.img-2.6.27-11-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda5)" {
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 46ec99b1-f458-408e-a402-f40e9bde3ae3
    linux /boot/vmlinuz-2.6.27-11-generic root=UUID=46ec99b1-f458-408e-a402-f40e9bde3ae3 ro single 
    initrd /boot/initrd.img-2.6.27-11-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda5)" {
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 46ec99b1-f458-408e-a402-f40e9bde3ae3
    linux /boot/memtest86+.bin  
}


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
menuentry "Microsoft Windows XP Home Edition" {
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c640894f40894761
    drivemap -s (hd0) $root
    chainloader +1
}
### END /etc/grub.d/30_otheros ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=ae19d715-5ecf-4062-978a-98d74b314e5b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c8cab7b0-db4c-4da3-a0e9-b2ef0bda97e5 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=5de1fe81-f145-40b7-a200-2c6ea5dfa494 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 304.5GB: boot/grub/grub.cfg
 304.4GB: boot/grub/menu.lst
 304.5GB: boot/initrd.img-2.6.31-3-generic
 304.5GB: boot/vmlinuz-2.6.31-3-generic
 304.5GB: initrd.img
 304.5GB: vmlinuz
```

Since it's incredibly long, I've attached the original file as well, in case it's easier to read it that way.

---

### Post by presence1960 on 2009-08-12
Assuming your sda (120 GB) drive boots first (you can check in BIOS to make sure it does, if it does not then set it to boot first). Next boot the Jaunty 9.04 Live CD and choose "try Ubuntu without any changes...", when the desktop loads do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)" or root (hd1,4) Use whatever #4 spits out 
6. Type "setup (hd0)" or setup (hd1) if #4 spits out (hd1,4) to install  GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Then reboot (remove the CD). You should be able to boot into Jaunty. Next we will chainload karmic from jaunty's GRUB. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```

scroll down to :
```
 ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

```

add these underneath the above text skipping one line then entering the following:

```
title          Ubuntu karmic
rootnoverify   (hd1,6)
chainloader    +1

title          Windows XP on sda1
rootnoverify   (hd0,0)
chainloader    +1

title          Windows XP on sdb1
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1
```

Click save on the toolbar and close. Reboot. If you can't boot karmic do this using the karmic Live CD
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,6) or root (hd0,6) Look at output from #4 use (hdx,6)
6. Type "setup (hd1,6) or setup (hd0,6) to put Karmic GRUB 2 on karmic's partition 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

 Above pay attention to the output of #4. You will get 2 choices. You want to use whatever choice has (hdx,6). You will use that in #5 & #6 above. That is your karmic partition. You will be putting karmic's GRUB on the first sector of that partition NOT MBR. This will allow you to chainload karmic from jaunty's GRUB.

The way you have it set up now your GRUB is looking on windows XP for karmic & jaunty. You want it to look on jaunty's & Karmic's partitions.

---

### Post by Arthur_D on 2009-08-15
presence1960, many thanks for this very very nice walkthrough! I can't thank you enough for writing such an informative post. But I have a couple of small problems.

After doing all of what you said first, I could not boot Karmic, as you predicted. Got an error saying: Error 13: Invalid or unsupported executable format

So then I proceeded to boot up my Karmic CD with the live boot, but sudo grub returns sudo: grub: command not found. Did you really mean booting up the Karmic install on sdb1 from the live CD? In that case, I'm sorry for the misunderstanding.

EDIT: I also get trouble booting all the other installs. I get this error: Error 18: Selected cylinder exceeds maximum supported by BIOS
Any clue? This sounds bad. :(

---

### Post by raymondh on 2009-08-15
> **Arthur_D said:**
> 

EDIT: I also get trouble booting all the other installs. I get this error: Error 18: Selected cylinder exceeds maximum supported by BIOS
Any clue? This sounds bad. :(

Arthur_D,

This is just in reference to your error 18.

In vintage BIOS' and motherboards, there is a cylinder limit that the BIOS will only go to a certain extent to look for an operating system. This is most common in pre '00 vintage set-up's ... and is prevalent when we install larger HD's.  The limit is usually between 8GB to 137GB depending on your computers' vintage.  

See Herman's site (and the 'how to make a separate /boot' section) for a better explanation and possible workarounds.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html) 

Good luck.

---

### Post by presence1960 on 2009-08-15
> **raymondhenson said:**
> Arthur_D,

This is just in reference to your error 18.

In vintage BIOS' and motherboards, there is a cylinder limit that the BIOS will only go to a certain extent to look for an operating system. This is most common in pre '00 vintage set-up's ... and is prevalent when we install larger HD's.  The limit is usually between 8GB to 137GB depending on your computers' vintage.  

See Herman's site (and the 'how to make a separate /boot' section) for a better explanation and possible workarounds.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html) 

Good luck.
+1 Raymond
Error 18 requires a separate /boot partition so that your boot files are within the boundary specified by your BIOS. There is no other work around. Look at the bright side though- you probably have learned quite a bit about Linux so far. It is a shame we didn't know about error 18 prior to all this, but like I said you gained some knowledge that you otherwise would not now have about booting.

---

### Post by Arthur_D on 2009-09-02
Sorry for the late reply guys, and thanks for helping me out.
But I got a couple of more questions. Herman's site mentions resizing the Linux partition. Well, my Windows partition is first on the hard disk, so resizing it at the start would be harmful, or is there a fair chance is should go well? Furthermore, should I make a /boot partition on the new hard disk or the old one (which might be a bit old and could possibly fail in some time)?

---

### Post by Arthur_D on 2009-09-09
*Bump*

---

### Post by raymondh on 2009-09-09
Have you tried moving Ubuntu within the first 137GB?  That will simplify.

I do agree, moving the front of any partition has it's risks as most data is stored there.  Back-up.  However, it is still possible .... as I have used gparted to do such.  If you do decide to try :

1.  Back-up
2.  Have a original windows install disc (just in case)
3.  Defrag windows

[http://gparted.sourceforge.net/larry/move/move.htm](http://gparted.sourceforge.net/larry/move/move.htm)
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Good luck Arthur.  Read/research/ask for a second opinion.

---

### Post by Arthur_D on 2009-09-09
Thank you very much!
I'll definately try that.

I'll report here when I'm done. :)

---

### Post by Arthur_D on 2009-09-10
Okay, resizing went fine, but when I try to follow Herman's tutorial, I can't go on because grub isn't found on the LiveCD! What do I do then?

---

### Post by raymondh on 2009-09-10
> **Arthur_D said:**
> Okay, resizing went fine, but when I try to follow Herman's tutorial, I can't go on because grub isn't found on the LiveCD! What do I do then?

Arthur_D,

Am trying to follow the thread again.

Have you tried to restore GRUB as per post # 5 (from presence1960)?  If so, what are the errors?

Kindly share which specific tutorial (from herman) are you following.

---

### Post by Arthur_D on 2009-09-10
Yes I did, and then I got the error 18.
So then I was kindly asked to try the method described [here]("http://members.iinet.net.au/%7Eherman546/p15.html#18"), which points to [this]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_boot_partition") section. I was trying to do this: > You will need to re-install GRUB, see: [                                                                  Re-install GRUB with a GRUB shell]("http://members.iinet.net/%7Eherman546/p15.html#Re-install_Grub_with_Live_CD") eg; with Live CD
                                                                 You will need to set your new /boot partition as the root device in GRUB and install GRUB to MBR in your first hard disk.
                                                                                                                                                                                                                                                  ```
sudo grub
```[FONT=Bitstream Vera Sans Mono][/FONT]
And then I got the message that the command 'grub' wasn't found.

Thank you for taking the time trying to help.

---

### Post by raymondh on 2009-09-10
Arthur,

Let me research.  Am amazed because I have reinstalled GRUB many times from the liveCD.  Although, I have never used a /boot partition.  Will be back with whatever I find.

---

### Post by geoslob on 2009-09-10
Thanks presence1960!  I had a PXE server mess up my Ubuntu laptop and your quick and precise explanation had me running again in 5 minutes or less.  

1. Boot your computer up with ubuntu cd
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for ubuntu.
6. Type "setup (hd0)", to install grub to mbr, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install grub to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable cd.

That's all I needed.  But so many Linux gurus assume that if you're not also a guru you should go pound sand and "screw you, run Microsoft" or something just as condescending.  I've been using Microsoft products since DOS 2.1 (I think, maybe earlier) and I want to switch to open source Linux but all the 'experts' seem to assume one is capable of writing one's own Linux distro or else they should go back to Microsoft.  That's what it looks like from a noob's point of view.  (And I realize I may get flamed just for saying this.)

If only all Linux issues could be resolved by people who are willing to 'spread the wealth', Linux would rule the world....but then maybe it'd be like Microsoft and it would suck.  What to do, what to do?

---

### Post by presence1960 on 2009-09-10
> **Arthur_D said:**
> Yes I did, and then I got the error 18.
So then I was kindly asked to try the method described [here]("http://members.iinet.net.au/%7Eherman546/p15.html#18"), which points to [this]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_boot_partition") section. I was trying to do this: 
And then I got the message that the command 'grub' wasn't found.

Thank you for taking the time trying to help.

Arthur since your setup has changed can you run the boot info script and post the output. this way we have up to date info on your setup and boot process please.

---

### Post by presence1960 on 2009-09-10
> **geoslob said:**
> Thanks presence1960!  I had a PXE server mess up my Ubuntu laptop and your quick and precise explanation had me running again in 5 minutes or less.  

1. Boot your computer up with ubuntu cd
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for ubuntu.
6. Type "setup (hd0)", to install grub to mbr, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install grub to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable cd.

That's all I needed.  But so many Linux gurus assume that if you're not also a guru you should go pound sand and "screw you, run Microsoft" or something just as condescending.  I've been using Microsoft products since DOS 2.1 (I think, maybe earlier) and I want to switch to open source Linux but all the 'experts' seem to assume one is capable of writing one's own Linux distro or else they should go back to Microsoft.  That's what it looks like from a noob's point of view.  (And I realize I may get flamed just for saying this.)

If only all Linux issues could be resolved by people who are willing to 'spread the wealth', Linux would rule the world....but then maybe it'd be like Microsoft and it would suck.  What to do, what to do?

Glad you got it working, enjoy Ubuntu.

I think if you hang around here for a while you will come to see that a majority of our members are willing to help no matter what your skill level.

The only time I refuse to help someone is when I am aware they are running pirated software. I feel very strongly about that.

---

### Post by raymondh on 2009-09-11
> **presence1960 said:**
> Arthur since your setup has changed can you run the boot info script and post the output. this way we have up to date info on your setup and boot process please.

Thanks presence1960 :)

---

