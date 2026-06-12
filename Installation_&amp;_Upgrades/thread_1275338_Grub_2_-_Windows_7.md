---
title: "Grub 2 - Windows 7"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by Cole on 2009-09-25
I have not used Ubuntu since 7.10--so Grub 2 is particularly new for me and as such I am sort of lost.

I installed the Ubuntu partitions manually by resizing my main partition and creating a swap and ext4 partition in the new free space.  Both my Windows 7 boot partition and the main (C:) partition are still in tact and there has been no data loss.

Grub2, however, did not automatically add Windows 7.  I have no idea how to work with its syntax and I am also not very sure if grub handles Windows 7 differently than previous windows releases.

Could anyone tell me how to manually or automatically add my windows 7 partition?

Thanks!

---

### Post by ajgreeny on 2009-09-25
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Everything you need is here.

---

### Post by SlonUA on 2009-12-16
> **Cole said:**
> I have not used Ubuntu since 7.10--so Grub 2 is particularly new for me and as such I am sort of lost.

I installed the Ubuntu partitions manually by resizing my main partition and creating a swap and ext4 partition in the new free space.  Both my Windows 7 boot partition and the main (C:) partition are still in tact and there has been no data loss.

Grub2, however, did not automatically add Windows 7.  I have no idea how to work with its syntax and I am also not very sure if grub handles Windows 7 differently than previous windows releases.

Could anyone tell me how to manually or automatically add my windows 7 partition?

Thanks!

$ sudo update-grub

---

### Post by presence1960 on 2009-12-16
I would run in terminal from 9.10 sudo update-grub as requested by SlonUA.

Reboot and if windows still is not in the GRUB menu do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Mark Phelps on 2009-12-17
When you run update-grub in a terminal, it will report back on every OS (and kernel) it finds, one row at a time.  You should see it report on finding Windows 7, although it might say Windows OS Loader.

---

### Post by ferdez on 2010-02-08
Having the same problem here, after a kernel upgrade to 2.6.31-19...

I'v been using 9.10 for a while and after a kernel upgrade it seems that the upgrade-grub script doesn't run the /etc/grub.d/30_os-prober and so it doesn't find oter OSses... 

And upgrade-grub insists in generating menu.lst that I would think it's no longer necessary with grub2.

---

### Post by presence1960 on 2010-02-08
> **ferdez said:**
> Having the same problem here, after a kernel upgrade to 2.6.31-19...

I'v been using 9.10 for a while and after a kernel upgrade it seems that the upgrade-grub script doesn't run the /etc/grub.d/30_os-prober and so it doesn't find oter OSses... 

And upgrade-grub insists in generating menu.lst that I would think it's no longer necessary with grub2.
I need to see what you have on that machine. Do this:

Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Mark Phelps on 2010-02-08
> **ferdez said:**
> Having the same problem here, after a kernel upgrade to 2.6.31-19...

I'v been using 9.10 for a while and after a kernel upgrade it seems that the upgrade-grub script doesn't run the /etc/grub.d/30_os-prober and so it doesn't find oter OSses... 

And upgrade-grub insists in generating menu.lst that I would think it's no longer necessary with grub2.

Presence's script will show us what you have -- but if I had to guess, I would say you updated from 9.04 to 9.10 because that will not automatically install GRUB2 and running update-grub will simply rewrite the legacy menu.lst file.

---

### Post by kansasnoob on 2010-02-08
In deed run the Boot Info Script and post those results here. To be sure you don't have a "mixed bag" of legacy grub and grub2 files it would also help to see the output of:

```
grub-install -v
```

```
ls /boot/grub
```

---

### Post by ned08 on 2010-02-19
Hi Guys i Have the same problem please find the revelant information below. 

Thanks 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e0ef28c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   399,859,711   399,652,864   7 HPFS/NTFS
/dev/sda3         399,859,712   522,751,999   122,892,288   7 HPFS/NTFS
/dev/sda4         522,755,100   625,137,344   102,382,245   5 Extended
/dev/sda5         616,494,438   625,137,344     8,642,907  82 Linux swap / Solaris
/dev/sda6         522,755,226   523,140,659       385,434  83 Linux
/dev/sda7         523,140,723   616,494,374    93,353,652  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7A9035119034D57B                       ntfs       System Reserved               
/dev/sda2        344A37C34A3780A2                       ntfs                                     
/dev/sda3        9402522202520A1E                       ntfs       backup file                   
/dev/sda5        a699e4ce-95f3-40de-b8aa-e261fe921112   swap                                     
/dev/sda6        e2289dee-7b24-48b6-98b5-338656e6c9a1   ext2                                     
/dev/sda7        bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro)
/dev/sda6        /boot                    ext2       (rw)
/dev/sda3        /media/backup file       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/344A37C34A3780A2  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

============================= sda6/grub/menu.lst: =============================

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
# kopt=root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e2289dee-7b24-48b6-98b5-338656e6c9a1

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        e2289dee-7b24-48b6-98b5-338656e6c9a1
kernel        /vmlinuz-2.6.31-19-generic root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro quiet splash 
initrd        /initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        e2289dee-7b24-48b6-98b5-338656e6c9a1
kernel        /vmlinuz-2.6.31-19-generic root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro  single
initrd        /initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        e2289dee-7b24-48b6-98b5-338656e6c9a1
kernel        /vmlinuz-2.6.31-14-generic root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro quiet splash 
initrd        /initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        e2289dee-7b24-48b6-98b5-338656e6c9a1
kernel        /vmlinuz-2.6.31-14-generic root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro  single
initrd        /initrd.img-2.6.31-14-generic

title         Windows 95/98/NT/2000
root          (hd0,0)
makeactive
chainloader   +1
### END DEBIAN AUTOMAGIC KERNELS LIST

============================= sda6/grub/grub.cfg: =============================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2289dee-7b24-48b6-98b5-338656e6c9a1
    linux    /vmlinuz-2.6.31-19-generic root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro   quiet splash
    initrd    /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2289dee-7b24-48b6-98b5-338656e6c9a1
    linux    /vmlinuz-2.6.31-19-generic root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro single 
    initrd    /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2289dee-7b24-48b6-98b5-338656e6c9a1
    linux    /vmlinuz-2.6.31-14-generic root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro   quiet splash
    initrd    /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2289dee-7b24-48b6-98b5-338656e6c9a1
    linux    /vmlinuz-2.6.31-14-generic root=UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 ro single 
    initrd    /initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda6: Location of files loaded by Grub: ===================


 267.7GB: grub/core.img
 267.7GB: grub/grub.cfg
 267.7GB: grub/menu.lst
 267.6GB: initrd.img-2.6.31-14-generic
 267.6GB: initrd.img-2.6.31-19-generic
 267.6GB: vmlinuz-2.6.31-14-generic
 267.6GB: vmlinuz-2.6.31-19-generic

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=bc05eb9e-ff5c-4e6d-9aa8-937a2eccdd65 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=e2289dee-7b24-48b6-98b5-338656e6c9a1 /boot           ext2    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a699e4ce-95f3-40de-b8aa-e261fe921112 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 267.8GB: initrd.img
 267.8GB: initrd.img.old
 267.8GB: vmlinuz
 267.8GB: vmlinuz.old

---

### Post by ferdez on 2010-02-19
Update: although this was really a fresh install of 9.10 I found out that the old grub replaced grub2 sometime after. I'm sure I didn't do it on porpose. I might have made some mistake and forced install of grub, removing grub2. But I'm also inclined to suspect some rogue dependency from some package I installed in the mean time... Anyway, it's solved. I forced the grub2 to install again and now everything works.

Thanks guys.

---

### Post by pavel989 on 2010-05-20
> **slonua said:**
> $ sudo update-grub

thank you!!!!

---

### Post by crowdofone on 2010-06-02
I found that placing an extra entry in /etc/grub.d/40_custom that was a copy of the Windows 7 entry from grub.cfg with the text highlighted in red removed worked for me.

_Original Windows 7 grub.cfg entry_

```

menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid [COLOR="Red"]--set 2cb8b1f1b8b1b9a2[/COLOR]
	chainloader +1
}

```

_Entry added to 40_custom_

```

menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid
	chainloader +1
}

```

Ps. Remember to run either of these after: 

```
grub-mkconfig -o /boot/grub/grub.cfg
```

or

```
update-grub
```

---

### Post by Dolfhin01 on 2010-08-04
Hey Guys,

I feel I'm a little bit over my head in this.

I have a new computer running Windows 7 and Ubuntu, I first installed Windows 7 and after that Ubuntu. The partition scheme is as following :

/dev/sda1 SSD with Ubuntu 10.04
/dev/sdb1 NTFS for Windows and Games
/dev/sdb5 /home for Ubuntu

But my computer boots straight to Ubuntu, very nice but I would like to play Starcraft 2 once in a while so it would be great if I could get the option to boot to Windows.

Can anyone point me in the right direction? I have found some information but I find it very confusing due the huge differences between Grub 1 and Grub 2. 

I ran the boot information script and I got the following :

> [I]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    62,531,583    62,529,536  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   513,638,399   513,636,352   7 HPFS/NTFS
/dev/sdb2         513,640,446 2,930,276,351 2,416,635,906   5 Extended
/dev/sdb5         513,640,448 2,930,276,351 2,416,635,904  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        02c1f5af-d03c-450b-91ea-80fa79a40c17   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E80A20780A2045C2                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        cda442e8-8322-4fb0-a38f-cdea946adb8b   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /home                    ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 02c1f5af-d03c-450b-91ea-80fa79a40c17
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 02c1f5af-d03c-450b-91ea-80fa79a40c17
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 02c1f5af-d03c-450b-91ea-80fa79a40c17
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=02c1f5af-d03c-450b-91ea-80fa79a40c17 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 02c1f5af-d03c-450b-91ea-80fa79a40c17
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=02c1f5af-d03c-450b-91ea-80fa79a40c17 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 02c1f5af-d03c-450b-91ea-80fa79a40c17
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 02c1f5af-d03c-450b-91ea-80fa79a40c17
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=cda442e8-8322-4fb0-a38f-cdea946adb8b /home           ext4    defaults        0       2

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
  30.2GB: boot/grub/grub.cfg
   2.4GB: boot/initrd.img-2.6.32-21-generic
   2.3GB: boot/vmlinuz-2.6.32-21-generic
   2.4GB: initrd.img
   2.3GB: vmlinuz
[/I]

---

### Post by perik0 on 2010-08-23
I have read you entries. I have formatted an old partition containing XP. When  reboot the system, grub 2 has deleted the windows entries loosing the windows 7 partition. When entering this option it sais "hall.dll is lost, replace it" (something like that..)
This is my result.txt




                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Slackware 12.0.0
    Boot files/dirs:   /etc/fstab /etc/lilo.conf

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   102,815,999   102,815,937   7 HPFS/NTFS
/dev/sda2    *    102,816,000   263,514,194   160,698,195   7 HPFS/NTFS
/dev/sda3         263,514,319   312,576,704    49,062,386   5 Extended
/dev/sda5         280,189,728   290,680,109    10,490,382  83 Linux
/dev/sda6         290,680,173   310,423,994    19,743,822  83 Linux
/dev/sda7         310,424,058   312,576,704     2,152,647  82 Linux swap / Solaris
/dev/sda8         263,514,321   280,189,664    16,675,344  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        54AAC012327B591E                       ntfs                                     
/dev/sda2        D0343D6E343D5924                       ntfs       XP                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b97756d0-d270-4526-9c2e-1892c10fa1ec   ext3                                     
/dev/sda6        f9e32057-1540-46e2-9a3a-f2e433f263b8   ext3                                     
/dev/sda7        fae73e2a-960b-44d9-ba26-460c026f3a10   swap                                     
/dev/sda8        7b1fffa8-a586-4967-9fc0-a42b5e36e412   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)


=============================== sda5/etc/fstab: ===============================

aufs / aufs defaults 0 0 # AutoUpdate
devpts /dev/pts devpts gid=5,mode=620 0 0 # AutoUpdate
proc /proc proc defaults 0 0 # AutoUpdate
sysfs /sys sysfs defaults 0 0 # AutoUpdate
/dev/hda /mnt/hda iso9660 noauto,users,exec 0 0 # AutoUpdate
/dev/sda1 /mnt/sda1 ntfs-3g auto,noatime,users,suid,dev,exec,locale= 0 0 # AutoUpdate
/dev/sda2 /mnt/sda2 ntfs-3g auto,noatime,users,suid,dev,exec,locale= 0 0 # AutoUpdate
/dev/sda5 /mnt/sda5 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sda6 /mnt/sda6 ext3 auto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sda7 /mnt/sda7 swap auto,defaults 0 0 # AutoUpdate
/dev/fd0 /mnt/floppy vfat noauto,noatime,users,suid,dev,exec 0 0 # AutoUpdate
/dev/sdb1 /mnt/sdb1 vfat auto,noatime,users,suid,dev,exec,quiet,umask=0,check=s,shortname=mixed 0 0 # AutoUpdate
/dev/sdb /mnt/sdb vfat auto,noatime,users,suid,dev,exec,quiet,umask=0,check=s,shortname=mixed 0 0 # AutoUpdate

============================= sda5/etc/lilo.conf: =============================

# LILO configuration file
# generated by 'liloconfig'
#
# Start LILO global section
lba32 # Allow booting past 1024th cylinder with a recent BIOS
boot = /dev/sda
#message = /boot/boot_message.txt
prompt
timeout = 1200
# Override dangerous defaults that rewrite the partition table:
change-rules
reset
# VESA framebuffer console @ 1024x768x256
vga = 773
# Normal VGA console
# vga = normal
# VESA framebuffer console @ 1024x768x64k
# vga=791
# VESA framebuffer console @ 1024x768x32k
# vga=790
# VESA framebuffer console @ 1024x768x256
# vga=773
# VESA framebuffer console @ 800x600x64k
# vga=788
# VESA framebuffer console @ 800x600x32k
# vga=787
# VESA framebuffer console @ 800x600x256
# vga=771
# VESA framebuffer console @ 640x480x64k
# vga=785
# VESA framebuffer console @ 640x480x32k
# vga=784
# VESA framebuffer console @ 640x480x256
# vga=769
# End LILO global section
# Linux bootable partition config begins
image = /boot/vmlinuz
root = /dev/sda1
label = Linux
read-only
# Linux bootable partition config ends

=================== sda5: Location of files loaded by Grub: ===================


 144.2GB: boot/vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, con Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    echo    'Cargando Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    echo    'Cargando Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    echo    'Cargando Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    echo    'Cargando Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set f9e32057-1540-46e2-9a3a-f2e433f263b8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set d0343d6e343d5924
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Linux (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b97756d0-d270-4526-9c2e-1892c10fa1ec
    linux /boot/vmlinuz root=/dev/sda1 ro vga = 773
}
menuentry "Ubuntu 8.10 (8.10) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 7b1fffa8-a586-4967-9fc0-a42b5e36e412
    linux /boot/vmlinuz root=/dev/sda8
}
menuentry "Ubuntu 8.10 (8.10) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set 7b1fffa8-a586-4967-9fc0-a42b5e36e412
    linux /boot/vmlinuz root=/dev/sda8
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f9e32057-1540-46e2-9a3a-f2e433f263b8 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=fae73e2a-960b-44d9-ba26-460c026f3a10 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 151.4GB: boot/grub/core.img
 151.4GB: boot/grub/grub.cfg
 151.5GB: boot/initrd.img-2.6.32-21-generic
 151.4GB: boot/initrd.img-2.6.32-22-generic
 151.4GB: boot/initrd.img-2.6.32-23-generic
 151.3GB: boot/initrd.img-2.6.32-24-generic
 151.4GB: boot/vmlinuz-2.6.32-21-generic
 151.4GB: boot/vmlinuz-2.6.32-22-generic
 151.4GB: boot/vmlinuz-2.6.32-23-generic
 151.4GB: boot/vmlinuz-2.6.32-24-generic
 151.3GB: initrd.img
 151.4GB: initrd.img.old
 151.4GB: vmlinuz
 151.4GB: vmlinuz.old

=============================== sda8/etc/fstab: ===============================

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0 0
/dev/sda8 / ext3 rw 0 0

=================== sda8: Location of files loaded by Grub: ===================


 138.8GB: boot/vmlinuz

---

### Post by oldfred on 2010-08-23
Windows combines its boot into one partition. Your sda2 shows part of win7 files and part of XP files but not all of either. You will have to run windows repairs to fix the windows partition as it is missing /bootmgr /Boot/BCD if it is win7 or boot.ini if it is XP. The missing hal error is often a problem with boot.ini (which you do not even have).

Your slackware says its root is sda1 which is now a NTFS partition??

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by chiabre on 2010-10-10
Hi gusy,
i have just installed maverick on a dual boot pc with win 7....but no way to see the win 7 entry in the grub menu...

i have manually added an entry but no lucky...

can anyone help me?

here my boot info script

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 37.0 GB, 37019566080 byte
255 testine, 63 settori/tracce, 4500 cilindri, totale 72303840 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1          68,397,056    72,302,591     3,905,536  82 Linux swap / Solaris
/dev/sda2    *          2,048    68,397,055    68,395,008  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 1000.2 GB, 1000204886016 byte
255 testine, 63 settori/tracce, 121601 cilindri, totale 1953525168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,259,522,047 1,259,520,000  83 Linux
/dev/sdb2       1,259,522,048 1,953,521,663   693,999,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        562a8329-2f83-46fa-973c-fb3beef6d58b   swap                                     
/dev/sda2        d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bd001e00-a4c8-4a34-bb76-7474f60aae57   ext4                                     
/dev/sdb2        6CEEF28DEEF24EB8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /home                    ext4       (rw,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
set locale_dir=($root)/boot/grub/locale
set lang=it
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7 ro  vga=775 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7 ro single  vga=775 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/31_win7 ###
menuentry “Windows 7” {
set root=(hd1,2)
chainloader +1
}
### END /etc/grub.d/31_win7 ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc1 during installation
UUID=bd001e00-a4c8-4a34-bb76-7474f60aae57 /home           ext4    defaults        0       2
/dev/sda1       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  20.0GB: boot/grub/core.img
  23.9GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
  20.0GB: boot/vmlinuz-2.6.35-22-generic
    .7GB: initrd.img
  20.0GB: vmlinuz

```

---

### Post by presence1960 on 2010-10-10
> **chiabre said:**
> Hi gusy,
i have just installed maverick on a dual boot pc with win 7....but no way to see the win 7 entry in the grub menu...

i have manually added an entry but no lucky...

can anyone help me?

here my boot info script

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 37.0 GB, 37019566080 byte
255 testine, 63 settori/tracce, 4500 cilindri, totale 72303840 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1          68,397,056    72,302,591     3,905,536  82 Linux swap / Solaris
/dev/sda2    *          2,048    68,397,055    68,395,008  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 1000.2 GB, 1000204886016 byte
255 testine, 63 settori/tracce, 121601 cilindri, totale 1953525168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,259,522,047 1,259,520,000  83 Linux
/dev/sdb2       1,259,522,048 1,953,521,663   693,999,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        562a8329-2f83-46fa-973c-fb3beef6d58b   swap                                     
/dev/sda2        d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bd001e00-a4c8-4a34-bb76-7474f60aae57   ext4                                     
/dev/sdb2        6CEEF28DEEF24EB8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /home                    ext4       (rw,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
set locale_dir=($root)/boot/grub/locale
set lang=it
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7 ro  vga=775 quiet  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7 ro single  vga=775 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/31_win7 ###
menuentry “Windows 7” {
set root=(hd1,2)
chainloader +1
}
### END /etc/grub.d/31_win7 ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=d9dfee3a-8e29-4d72-87cc-ed09f1c70cb7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc1 during installation
UUID=bd001e00-a4c8-4a34-bb76-7474f60aae57 /home           ext4    defaults        0       2
/dev/sda1       none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  20.0GB: boot/grub/core.img
  23.9GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
  20.0GB: boot/vmlinuz-2.6.35-22-generic
    .7GB: initrd.img
  20.0GB: vmlinuz

```

It looks like you are missing the boot files necessary to boot windows 7. Here is a look at mine:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   [COLOR="Red"]/bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]
```

Note the boot files in red and compare to yours.

You will need a windows 7 installation disk. **_Boot your machine and go into BIOS. Set the 1 TB disk as first to boot in the hard disk boot order. This is critical as windows writes it's boot loader to the MBR of the first disk to boot!_**

Save changes to CMOS. Continue booting off the windows media. At the prompt select repair windows. Then choose fix problems keeping windows from booting (paraphrased- sorry I don't use windows often). This will repair the boot function of windows. Reboot without the windows disk and see if windows boots. If it does reboot and go back in BIOS and set the 37GB disk as first to boot in the hard disk boot order. Save changes to CMOS and continue booting. Boot into ubuntu. Open a terminal and run ```
sudo update-grub
```This will detect your windows boot files and add it to the GRUB menu. next time you boot you will be able to boot to windows from GRUB.

P.S. If you don't have a windows installation disk you can download an iso and burn it as an image to CD from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/"). You can then boot from this CD and use the recovery console as described above. It is not a full windows disk, but rather contains only the recovery functions. You can not install windows from this disk.

---

### Post by greg7 on 2010-11-07
Hello,
I also have a problem with Grub 2 not seeing Windows 7.
I installed Windows 7 on a NTFS partition and then Linux Mint Debian Edition
on a Ext4 partition. I only have one hdd and the result of Boot Info Script is this:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint Debian Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1          76,405,140   166,513,724    90,108,585   7 HPFS/NTFS
/dev/sda2          24,418,800    33,399,134     8,980,335   5 Extended
/dev/sda5          24,418,863    33,399,134     8,980,272  82 Linux swap / Solaris
/dev/sda3    *     33,399,135    76,405,139    43,006,005  83 Linux
/dev/sda4         166,513,725   976,768,064   810,254,340   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5C9ECC472B535F2E                       ntfs       win7                          
/dev/sda2: PTTYPE="dos" 
/dev/sda3        b05ea6e2-9a44-4a92-b294-121e7be29779   ext4                                     
/dev/sda4        5E8DDC705A00F894                       ntfs       myNTFS                        
/dev/sda5        d60123a1-f2a4-4ce6-8ad9-d29a343f7321   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set b05ea6e2-9a44-4a92-b294-121e7be29779
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
if terminal_output gfxterm ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal gfxterm
fi
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set b05ea6e2-9a44-4a92-b294-121e7be29779
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=10
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set b05ea6e2-9a44-4a92-b294-121e7be29779
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set b05ea6e2-9a44-4a92-b294-121e7be29779
    echo    'Loading Linux 2.6.32-5-686 ...'
    linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=b05ea6e2-9a44-4a92-b294-121e7be29779 ro  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-686
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set b05ea6e2-9a44-4a92-b294-121e7be29779
    echo    'Loading Linux 2.6.32-5-686 ...'
    linux    /boot/vmlinuz-2.6.32-5-686 root=UUID=b05ea6e2-9a44-4a92-b294-121e7be29779 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=39dce7bc-28c6-4d48-a3e1-b2d48712856e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f5355ad1-6de9-497b-a8d4-e2abe7336d4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda3    /    ext4    rw,errors=remount-ro    0    0

=================== sda3: Location of files loaded by Grub: ===================


  19.4GB: boot/grub/core.img
  28.6GB: boot/grub/grub.cfg
  19.4GB: boot/initrd.img-2.6.32-5-686
  19.3GB: boot/vmlinuz-2.6.32-5-686
  19.4GB: initrd.img
  19.3GB: vmlinuz

```I am sorry to post in ubuntuforums.org but this seems to be a problem with
GRUB and not LMDE.
Any help would be appreciated!

---

### Post by graphx3d on 2011-01-02
I'm having difficulty as well... I installed 10.10 after I had windows installed and when I boot the machine, I can't see the grub screen on boot to even change the OS to boot:

Here's the /etc/default/grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=795"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

I have in /etc/grub.d a file called 11_Windows with the following script in it:

#!/bin/sh -e
echo "Adding Windows">&2
cat<<EOF
menuentry "Windows 7" {
set root=(hd0)
chainloader +1
}
EOF

When I sudo update-grub I get the following output:

error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
error: cannot seek `/dev/sdb'.
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Adding Windows
error: cannot seek `/dev/sdb'.
Found memtest86+ image: /boot/memtest86+.bin
ERROR: nvidia: wrong # of devices in RAID set "nvidia_afedfeci" [1/2] on /dev/sdb
ERROR: nvidia: wrong # of devices in RAID set "nvidia_bdcidbdc" [1/2] on /dev/sda
ERROR: removing inconsistent RAID set "nvidia_bdcidbdc"
done

Also, Windows7 is on /dev/sda (2 partitions, separate drive than Ubuntu, 100 MB & 250 GB, windows boot drive and windows respectively).

Does anyone know what the issue is and or how I can fix it so I can:
1. see the grub boot screen?
2. add windows to eh grub2 boot menu?

Please & Thank you in advance for any help you could provide. If there is anything else I can provide info wise, please let me know.
Thanks,
Steve

---

### Post by grantmeaname on 2011-01-15
I'm having the same problem on a friend's computer as everyone else in the thread. The computer in question has sda1 as ubuntu and sda3 as Windows, with no other partitions.

When I run update-grub, I get the following output:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

But my results.txt file generated by the script can find the Windows partition (and in fact, the windows partition is where much of the user's data is stored, and there's never been a problem with reading it. According to the boot Info Script, though,  ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    30,799,871    30,797,824  83 Linux
/dev/sda3          30,800,325   976,771,119   945,970,795   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        bb24d041-bd6d-42f6-8bbc-6dbccfc70897   ext4                                     
/dev/sda3        00B8457CB8457168                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set bb24d041-bd6d-42f6-8bbc-6dbccfc70897
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set bb24d041-bd6d-42f6-8bbc-6dbccfc70897
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set bb24d041-bd6d-42f6-8bbc-6dbccfc70897
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=bb24d041-bd6d-42f6-8bbc-6dbccfc70897 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set bb24d041-bd6d-42f6-8bbc-6dbccfc70897
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=bb24d041-bd6d-42f6-8bbc-6dbccfc70897 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set bb24d041-bd6d-42f6-8bbc-6dbccfc70897
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set bb24d041-bd6d-42f6-8bbc-6dbccfc70897
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda1 :
UUID=bb24d041-bd6d-42f6-8bbc-6dbccfc70897	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=00B8457CB8457168	/media/OS	ntfs-3g	defaults,locale=en_US.UTF-8	0	0



=================== sda1: Location of files loaded by Grub: ===================


   7.0GB: boot/grub/core.img
  13.2GB: boot/grub/grub.cfg
   3.0GB: boot/initrd.img-2.6.35-22-generic
   3.9GB: boot/initrd.img-2.6.35-24-generic
   7.3GB: boot/vmlinuz-2.6.35-22-generic
   7.3GB: boot/vmlinuz-2.6.35-24-generic
   3.9GB: initrd.img
   3.0GB: initrd.img.old
   7.3GB: vmlinuz
   7.3GB: vmlinuz.old
```

Grub only "looks on the same drive in partition #1"... does that mean it's not looking at /sda5?

---

### Post by presence1960 on 2011-01-15
```
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /Windows/System32/winload.exe[/COLOR]
```

You are missing the rest of the boot files necessary to boot windows 7. See red above. What happened to sda2? That was probably the System reserved partition which contained the rest of your boot files.

here is my output from my windows 7. Notice the difference:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]

```

---

### Post by presence1960 on 2011-01-15
```
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /Windows/System32/winload.exe[/COLOR]
```

You are missing the rest of the boot files necessary to boot windows 7. See red above. What happened to sda2? That was probably the System reserved partition which contained the rest of your boot files.

here is my output from my windows 7. Notice the difference:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe[/COLOR]

```

---

### Post by Quackers on 2011-01-15
How many people are asking for help in this thread? 12? Please start your own threads! Although your symptoms may seem similar to somebody else's, the cause may be very different.

---

### Post by grantmeaname on 2011-01-16
sorry, posting problem.

---

### Post by grantmeaname on 2011-01-16
Alright. I found a saved copy of the Recovery partition that was previously /dev/sda2 on an external hard drive; running the bootscript confirms that it contains the missing files.
```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD
```

 I have no interest in returning to that partitioning scheme, though. Can I simply copy */bootmgr* and */Boot/BCD*, or even the entire contents of the partition, onto the windows partition, sda3? If not, do I need to resize or shrink sda3 and then copy the recovery partition back on?

---

### Post by grantmeaname on 2011-01-16
Alright. I found a saved copy of the Recovery partition that was previously /dev/sda2 on an external hard drive; running the bootscript confirms that it contains the missing files.
```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD
```

 I have no interest in returning to that partitioning scheme, though. Can I simply copy */bootmgr* and */Boot/BCD*, or even the entire contents of the partition, onto the windows partition, sda3? If not, do I need to resize or shrink sda3 and then copy the recovery partition back on?

---

### Post by kansasnoob on 2011-01-16
> **grantmeaname said:**
> Alright. I found a saved copy of the Recovery partition that was previously /dev/sda2 on an external hard drive; running the bootscript confirms that it contains the missing files.
```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD
```

 I have no interest in returning to that partitioning scheme, though. Can I simply copy */bootmgr* and */Boot/BCD*, or even the entire contents of the partition, onto the windows partition, sda3? If not, do I need to resize or shrink sda3 and then copy the recovery partition back on?

Possibly! Look here:

[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

I'm already getting quite tired (I'm old) but regardless this may require some additional instruction so please be patient :D

---

### Post by kansasnoob on 2011-01-16
> **Quackers said:**
> How many people are asking for help in this thread? 12? Please start your own threads! Although your symptoms may seem similar to somebody else's, the cause may be very different.

+1! I've been bad about doing so recently but IMHO we should kindly ask that new problems be posted as new threads.

It saves us a lot of time ;)

---

### Post by Quackers on 2011-01-16
grantmeaname, you probably need to move the boot flag from sad1 to sda3 (with either gparted or diskpart) and then either, run startup repair from the Windows vista/7 repair disc 3 times, or go to the command prompt in the recovery console and run ```
bootrec.exe /fixmbr
```
This should get Windows booting again. If it needs a chkdsk, run it.
Once Windows is happy, you can re-install grub from the live cd/usb to get Ubuntu booting again.

---

### Post by krisdg on 2012-03-05
hi,

I get the same problem, after installing ubuntu 11.10
i messed up my windows7 partition who is on sda1

so i put the windows7 DVD to repair the system...
it seem to be ok now, the bootmgr is there again

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /Boot/BCD /ntldr /ntdetect.com

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 têtes, 63 secteurs/piste, 243201 cylindres, total 3907029168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 3,320,419,806 3,320,417,759   7 NTFS / exFAT / HPFS
/dev/sdb2       3,320,420,350 3,907,028,991   586,608,642   5 Extended
/dev/sdb5       3,883,188,224 3,907,028,991    23,840,768  82 Linux swap / Solaris
/dev/sdb6       3,320,420,352 3,874,801,663   554,381,312  83 Linux
/dev/sdb7       3,874,803,712 3,883,184,127     8,380,416  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 têtes, 63 secteurs/piste, 14946 cylindres, total 240121728 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique)*: 512*octets / 512*octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63   240,091,424   240,091,362   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0C0EBE250EBE082A                       ntfs       
/dev/sdb1        E818BEA418BE7164                       ntfs       
/dev/sdb5        28c6713a-91ef-4259-9b6a-8f17113d3303   swap       
/dev/sdb6        022e463a-8185-4378-a619-ff1837cd5cb6   ext4       
/dev/sdb7        f6f9fba0-c8d1-4915-9a87-723f8fc61cfd   swap       
/dev/sdc1        8E4CEB904CEB717F                       ntfs       mybookworld
/dev/sdd1        B2D8EFFCD8EFBD2B                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos6)'
  search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
  set locale_dir=($root)/boot/grub/locale
  set lang=fr_FR
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, avec Linux 3.0.0-16-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
	linux	/boot/vmlinuz-3.0.0-16-generic-pae root=UUID=022e463a-8185-4378-a619-ff1837cd5cb6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic-pae
}
menuentry 'Ubuntu, avec Linux 3.0.0-16-generic-pae (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
	echo	'Chargement de Linux 3.0.0-16-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-16-generic-pae root=UUID=022e463a-8185-4378-a619-ff1837cd5cb6 ro recovery nomodeset 
	echo	'Chargement du disque mémoire initial ...'
	initrd	/boot/initrd.img-3.0.0-16-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, avec Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=022e463a-8185-4378-a619-ff1837cd5cb6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, avec Linux 3.0.0-16-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
	echo	'Chargement de Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=022e463a-8185-4378-a619-ff1837cd5cb6 ro recovery nomodeset 
	echo	'Chargement du disque mémoire initial ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, avec Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=022e463a-8185-4378-a619-ff1837cd5cb6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, avec Linux 3.0.0-12-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
	echo	'Chargement de Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=022e463a-8185-4378-a619-ff1837cd5cb6 ro recovery nomodeset 
	echo	'Chargement du disque mémoire initial ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 022e463a-8185-4378-a619-ff1837cd5cb6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0C0EBE250EBE082A
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdd1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root B2D8EFFCD8EFBD2B
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=022e463a-8185-4378-a619-ff1837cd5cb6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=f6f9fba0-c8d1-4915-9a87-723f8fc61cfd none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/initrd.img-3.0.0-16-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  2
               =                boot/vmlinuz-3.0.0-16-generic-pae              2
               =                initrd.img                                     2
               =                initrd.img.old                                 3
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

================================ sdd1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(3)partition(1)\WINDOWS=Windows /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  ec 42 0d 73 e0 e5 36 76  cc 0b b9 56 96 5d 49 f7  |.B.s..6v...V.]I.|
*
000001b0  ec 42 0d 73 e0 e5 36 76  cc 0b b9 56 96 5d 00 fe  |.B.s..6v...V.]..|
000001c0  ff ff 82 fe ff ff 02 28  8b 21 00 c8 6b 01 00 fe  |.......(.!..k...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 30 0b 21 00 00  |...........0.!..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

the system files seem to be good :

```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

```

grub.cfg :

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0C0EBE250EBE082A
	chainloader +1
}
```

the line in the option menu on startup is there
but when i try to load windows 7 there is an error saying "read error"

can somebody help me ??

thx

Kris

---

### Post by oldfred on 2012-03-05
You have grub2's boot loader installed to ever MBR, but it looks like only the one in sda may be correct as it refers to partition 6, all the others refer to partition 5 and your install is in sdb6.

Have you tried booting from sda, a 500GB drive. You may have to try both 500GB in BIOS. I have two 160GB drives and it took me a while to know which was which in BIOS.

If not you should reinstall grub2's boot loader to sdb and use the windows repair CD to reinstall the Windows boot loader to sda. With multiple drives you want each drive to be fully bootable on its own in case the other fails. Be sure to use Ubuntu liveCD that is same version as your install, the newest grub2 only updates with the same version.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sdb6 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb6 if not correct:
sudo fdisk -l
#confirm that linux is sdb6
sudo mount /dev/sdb6 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Then set BIOS to boot from sdb.

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

If you do reboot from sda, then you still should reinstall to sdb.
#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by krisdg on 2012-03-05
thx for your reply

i reinstalled grub on sdb from running linux (no live) thru grub's sda
i tried to load windows (sda1) but i get the blinking cursos with no loading.. so i think my windows mbr is still corrupted...

i think i m going to try boot-repair and restore windows7 mbr
if it doesnt work i ll try a couple of command prompt thru W7 DVD

commands i found [HERE]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Windows+Bootloader+from+the+DVD")

i ll let you know what happens

++

---

### Post by oldfred on 2012-03-05
When you chainload Windows from grub it bypasses the Windows MBR and jumps to the Windows PBR or partition boot sector. Windows MBR just jumps to the PBR so once grub passes booting to the Windows PBR it is just like Windows booting from the MBR to PBR. 

You may need to repair the PBR with a fixBoot command or run chkdsk. Windows 7 has auto repair but you normally have to run it three times to run all the commands. If issues with chkdsk you may have to run it more than once. You have to run chkdsk until there are no errors as it does not fix everything on one pass.

---

### Post by krisdg on 2012-03-08
hi !

here is the thing :

i messed up my sda again with diskpart "clean" command.
i had to search for hours to get my partition table back.
i ran testdisk and some other stuff like that, nothing happend.
i tought i was good for a format and reinstall.
finally i get it back with loading a current_mbr.img saved with boot-repair. lucky me i saved it before !

now i had to put the boot flag to sda so that my W7 dvd finds my windows installation. Tried to repair several times but when i load thru sda i still get the grub's loading menu.

i load ubuntu back thru sda and set grub-pc installation to sdb
then ran a grub-update

when i command debconf -show grub-pc
the install devices is correctly set to sdb

i guess i have to put the boot flag to sdb and set it to boot to the correct drive (sdb) in the BIOS (not to hard to find, sdb=WDC /sda=Maxtor) // ok that works fine without putting the flag to sdb. i can now load grub/ubuntu from sdb

is there another way to completely remove grub from sda ?
thru ubuntu maybe...

thx for helping me ;-)

---

### Post by oldfred on 2012-03-08
You can use the Windows repairCD to run the fixMBR command. From repair console in Windows:

# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

I think Boot-Repair will also install a Windows work alike boot loader Syslinux to the MBR.

Grub does not use boot flag, but a few BIOS (mostly Intel motherboards) require a boot flag on a primary partition to let you boot at all.

---

### Post by krisdg on 2012-03-08
ok i ll try that.. i m running a chkdsk /r right now
but it takes a while...

---

### Post by krisdg on 2012-03-08
hi again,

here's what i did :

Option Three: Nuclear Holocaust
Back at the main page of the recovery center, go ahead and select "Command Prompt" yet again from that list. 

The first order of business is to make sure the MBR and bootsector contain the right references to the Windows bootloader:

bootrec.exe /fixmbr
bootsect.exe /nt60 all /force
Now we get rid of the old BCD registry, and create a new one instead.

Note: We're assuming that the boot drive is drive C: below. If your computer is configured differently, be sure to use the appropriate drive letter here instead.

attrib -h -s C:\boot\BCD

del C:\boot\BCD
bcdedit /createstore c:\boot\bcd.temp
bcdedit.exe /store c:\boot\bcd.temp /create {bootmgr} /d "Windows Boot Manager"
bcdedit.exe /import c:\boot\bcd.temp
bcdedit.exe /set {bootmgr} device partition=C:
bcdedit.exe /timeout 10
attrib -h -s C:\boot\bcd.temp
del c:\boot\bcd.temp
Now we have a clean, working Vista bootloader. But we need to add a Windows entry to it:

bcdedit.exe /create /d "Microsoft Windows" /application osloader
bcdedit.exe should return a message with a GUID for the newly-created entry, something like this:
The entry {c0dfc4fa-cb21-11dc-81bf-005056c00008} was successfully created.

You'll need to use the value that bcdedit.exe returned for you below, along with the drive letter for the drive that Windows is installed to:

Again, make sure to replace C: with whatever the correct drive is for your Windows Vista/7 installation.

bcdedit.exe /set {c0dfc4fa-cb21-11dc-81bf-005056c00008} device partition=C:
bcdedit.exe /set {c0dfc4fa-cb21-11dc-81bf-005056c00008} osdevice partition=C:
bcdedit.exe /set {c0dfc4fa-cb21-11dc-81bf-005056c00008} path \Windows\system32\winload.exe
bcdedit.exe /set {c0dfc4fa-cb21-11dc-81bf-005056c00008} systemroot \Windows
And, last of all, tell the bootmgr bootloader to list the new entry or else it'll remain hidden:

bcdedit.exe /displayorder {c0dfc4fa-cb21-11dc-81bf-005056c00008}

everything worked fine with no errors at all.
but i still cant get into my W7
always get that blinking cursors...
i m running out of ideas now
i pretty much tested everything

the w7 repair tool created a recovery folder with a boot.sdi and a winre.wim file.

there a some new files in the system volume information too

the chkdsk also ran without errors

i think i m out of options now

---

### Post by oldfred on 2012-03-08
You have gone beyond what I know about repairing Windows 7. I do not see what else you can do. 

Some have used this which may repair or make it more complicated.

[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by krisdg on 2012-03-12
thx for your reply.

i saved my files and made a fresh install of W7.
everything is back now.I just have to reinstall 2 years of programs  lol.

i got my files back anyway.

i think the windows 7 boot system is the worst i have ever seen !

they should take example on grub's system ;-)

---

### Post by Mark Phelps on 2012-03-12
> **krisdg said:**
>  ...i saved my files and made a fresh install of W7.
everything is back now.I just have to reinstall 2 years of programs  lol.

In the Windows 7 forums (sevenforums.com), they have tutorials that walk you through doing a Repair Install -- which, unlike what you did, would have left your data and apps INTACT.

If you want detailed help fixing ANOTHER OS's problems, it's often best to go to the forums that specialize in that other OS -- this is every bit as true of other Linux distros as it is of Windows OSs.

---

