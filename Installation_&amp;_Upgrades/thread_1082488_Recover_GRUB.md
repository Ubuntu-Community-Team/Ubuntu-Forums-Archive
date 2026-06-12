---
title: "Recover GRUB"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by chrisj26 on 2009-02-27
I have seen numerous tutorials on how to do this, but it never seems to work for me. I lost GRUB by virtue of having to re-install Windows, and now I can't seem to get GRUB back. I can boot into Ubuntu using Easy BCD but that means i have to scroll thru 2 boot menus. I want to get rid of the NeoGrub (part of EasyBCD) and get just the one installer menu. I'm inexperienced in Ubuntu, but this seems to me like it should be simple. I have tried Unetbootin, SuperGRUBdisk, running a GRUB re-install in Ubuntu. My Ubuntu liveCD is stuffed up but I used a PCLinuxOS liveCD to try and get just GRUB, but no luck. At my last attempt I tried to reinstall GRUB on my Ubuntu partition boot directly from that HDD, but it came with the message BOOTMGR is missing.

---

### Post by caljohnsmith on 2009-02-27
Please be more specific when you say:
[QUOTE=chrisj26]I have tried Unetbootin, SuperGRUBdisk, running a GRUB re-install in Ubuntu. My Ubuntu liveCD is stuffed up but I used a PCLinuxOS liveCD to try and get just GRUB, but no luck.[/QUOTE]
What exactly happens when you try Super Grub Disk (did you get any errors)? What happened or what errors did you get when you used PCLinuxOS Live CD to recover Grub, and what commands did you use? In order to get a clearer picture of your setup, how about booting your PCLinuxOS Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal/konsole and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by chrisj26 on 2009-03-01
I used SuperGrubDisk (the one which automatically fixes the bootloader) and the manual one, and unetbootin as well. The three have the same results. They detect where grub bootloader is(i've actually got a screen where i see the old grub menu) and it runs a few steps and says it is successful (sorry for the lack of info as I can't remember it, but will attempt again and post exact messages) but they all get stuck on the last step where it says installing or writing to MBR and that's where I have no result, it sort of hangs there.Will also post results from bootinfo script. Does it have to be done of the liveCD or can I do it in ubuntu?

---

### Post by caljohnsmith on 2009-03-01
You can run the script from most any Linux install (like your Ubuntu install) or from any Live CD.

---

### Post by chrisj26 on 2009-03-07
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD 
                       /Windows/System32/winload.exe 
                       /WINDOWS/system32/winload.exe 
                       /WINDOWS/SYSTEM32/winload.exe 
                       /windows/system32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdc4 and 
                       looks at sector 77326661 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdc. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 1,250,260,991 1,250,258,944   7 HPFS/NTFS

/dev/sda1 ends after the last cylinder of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    97,822,719    97,820,672   7 HPFS/NTFS
/dev/sdb2          97,822,720   186,812,415    88,989,696   7 HPFS/NTFS
/dev/sdb3         186,812,416   337,596,415   150,784,000   7 HPFS/NTFS
/dev/sdb4         337,596,416   488,394,751   150,798,336   f W95 Ext d (LBA)
/dev/sdb5         337,598,464   488,394,751   150,796,288   7 HPFS/NTFS

/dev/sdb4 ends after the last cylinder of /dev/sdb
/dev/sdb5 ends after the last cylinder of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    54,063,118    54,063,056   7 HPFS/NTFS
/dev/sdc2          78,639,120   156,295,439    77,656,320   7 HPFS/NTFS
/dev/sdc3          54,074,790    63,826,244     9,751,455  82 Linux swap / Solaris
/dev/sdc4          63,826,245    78,638,174    14,811,930  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6E10A1C210A1921F" LABEL="Media Backup" TYPE="ntfs" 
/dev/sdb1: UUID="B2C4DF78C4DF3D73" TYPE="ntfs" 
/dev/sdb2: UUID="E6924D45924D1C05" LABEL="Local Disk II" TYPE="ntfs" 
/dev/sdb3: UUID="D2B4DE8CB4DE7309" LABEL="Videos_2" TYPE="ntfs" 
/dev/sdb5: UUID="9C7ED5297ED4FCC8" LABEL="Local Disk IV" TYPE="ntfs" 
/dev/sdc1: UUID="6AC67CFAC67B837" TYPE="ntfs" 
/dev/sdc2: UUID="40B04FD6B04FD158" LABEL="Media+PES" TYPE="ntfs" 
/dev/sdc3: TYPE="swap" UUID="27d6e766-7917-4316-89e1-38c5e567af18" 
/dev/sdc4: UUID="275773fe-1804-4ce4-a4b6-901aa5c9969b" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/root on / type rootfs (rw)
none on /proc type proc (rw)
none on /dev/pts type devpts (rw,mode=0620)
/dev/sdb2 on /mnt/win_e type ntfs (ro,nosuid,nodev,nls=utf8,umask=0)
/dev/sdb3 on /mnt/win_f type ntfs (ro,nosuid,nodev,nls=utf8,umask=0)
/dev/sdb5 on /mnt/win_g type ntfs (ro,nosuid,nodev,nls=utf8,umask=0)
/dev/sdc1 on /mnt/win_h type ntfs (ro,nosuid,nodev,nls=utf8,umask=0)
/dev/sdc2 on /mnt/win_i type ntfs (ro,nosuid,nodev,nls=utf8,umask=0)
/dev/sdc4 on /mnt/sdc4 type ext3 (rw,nosuid,nodev)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
none on /sys/fs/fuse/connections type fusectl (rw)


=========================== sdc4/boot/grub/menu.lst: ===========================

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

#A splash image for the menu
splashimage=(hd1,3)/boot/grub/splashimages/appleblack.xpm.gz

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
# kopt=root=UUID=275773fe-1804-4ce4-a4b6-901aa5c9969b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,3)

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
# defoptions=quiet splash vga=792

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=275773fe-1804-4ce4-a4b6-901aa5c9969b ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=275773fe-1804-4ce4-a4b6-901aa5c9969b ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=275773fe-1804-4ce4-a4b6-901aa5c9969b ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=275773fe-1804-4ce4-a4b6-901aa5c9969b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdc4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=275773fe-1804-4ce4-a4b6-901aa5c9969b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=27d6e766-7917-4316-89e1-38c5e567af18 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc4: Location of files loaded by Grub: ===================


  39.6GB: boot/grub/menu.lst
  39.5GB: boot/grub/stage2
  39.3GB: boot/initrd.img-2.6.24-19-generic
  35.0GB: boot/initrd.img-2.6.24-19-generic.bak
  39.3GB: boot/initrd.img-2.6.24-21-generic
  35.0GB: boot/initrd.img-2.6.24-21-generic.bak
  39.3GB: boot/vmlinuz-2.6.24-19-generic
  34.2GB: boot/vmlinuz-2.6.24-21-generic
  39.3GB: initrd.img
  39.3GB: initrd.img.old
  34.2GB: vmlinuz
  39.3GB: vmlinuz.old

```
Also i have removed neogrub now in the hope of being able to get my original ubuntu grub!

---

### Post by chrisj26 on 2009-03-11
Also the exact point in unetbootin it hangs in is 'Running "embed /boot/grub/e2fs_stage1_5(hd0)"'
It's also the same stage, it hangs at when trying all other above mentioned methods.

---

### Post by meierfra. on 2009-03-11
> Also i have removed neogrub now in the hope of being able to get my original ubuntu grub! 

Are you still able to boot into Ubuntu? If yes how?

Grub seems to be  installed correctly in the MBR of  /dev/sda and in the boot sector of /dev/sdc4.

What happens when you boot from /dev/sda (your 640GB drive)? Does the grub menu appear?  Do you get any error messages?

To be able to boot from the Ubuntu drive (/dev/sdc) you need to set the boot flag to the ubuntu partition:
Open a terminal in ubuntu (or the ubuntu Live CD)

```
sudo fdisk /dev/sdc
a
4
w
```

---

### Post by chrisj26 on 2009-03-11
it fails to load  my ubuntu splash screen. i do get the gtub menu but if i select Vista it says BOOTMGR is missing and if i select Ubuntu it comes up with Error 17: could not mount the selected partition. But GRUB could never have been originally mounted on this as it was purchased after Ubuntu was installed. It could only have been on dev/sdc or dev/sdb

---

### Post by chrisj26 on 2009-03-11
Sorry I just realized my last post was pretty unclear. I can't boot into Ubuntu. But i do get the GRUB loader- which is a big step!It doesn't allow me to boot into either Vista or Ubuntu (with the error messages from my previous post)which makes me think GRUB doesn't have information as to where they are located- but I'm a noob n that's just what it may be. Also I'm curious why we mustr have grub on dev/sda as this can not have been the original set up. I don't think my GRUB overwrote the MBR of Vista or I wouldn't be able to have Vista. I think it installed GRUB on my Ubuntu partition. Do you still think I need to flag Ubuntu

---

### Post by mhgsys on 2009-03-11
check out what I've posted here:

[http://ubuntuforums.org/showthread.php?t=1092259](http://ubuntuforums.org/showthread.php?t=1092259)

good luck restoring.

---

### Post by chrisj26 on 2009-03-11
I've already tried this. It's unable to complete as stated earlier.

---

### Post by meierfra. on 2009-03-11
> Also I'm curious why we must have grub on dev/sda as this can not have been the original set up.

No you don't have to have Grub in the MBR of /dev/sda.   But the Ubuntu installer assumes that /dev/sda is the boot drive and so  installs grub to the MBR of /dev/sda.


>  But i do get the GRUB loader- which is a big step!I

Good news. Are you  now booting from the  Ubuntu drive ?
Anyway, try this to boot into Ubuntu:

At the grub menu at boot up, press "c" to get to the Grub command line.

Type 

> find /boot/grub/menu.lst

This should return something of the form "(hdX,3)", probably (hd0,3).
Press "Esc" to get back to the Grub menu.
Select "Ubuntu", but do not press "enter". Press "e" instead. At the new screen press "e" again. 
Change

root (hd1,3)

to

root (hdX,3)

(Replace "X" by the number returned  by "find  /boot/grub/menu.lst")


Press "Enter" and then "b" to boot into ubuntu.
If this worked you have to edit menu.lst to make the changes permanent:

In a terminal in ubuntu, 

```
gksudo gedit /boot/grub/menu.lst
```

Change 

# groot=(hd1,3)

to

# groot=(hdX,3)

(again replace "X" by the number returned by "find /boot/grub/menu.lst")

Save the file. Back in the terminal

```
sudo update-grub
```


> but if i select Vista it says BOOTMGR is missin


Add the following to the end  of the file:


title		Windows Vista/Longhorn (loader)  (hd1)
root		(hd1,0)
map (hd1) (hd0)
map (hd0)  (hd1)
chainloader	+1

title		Windows Vista/Longhorn (loader) (hd2)
root		(hd2,0)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader	+1


Reboot and try both entries.  If one of them works, you can remove the other from menu.lst. If none of them works, report any error messages you got.

---

### Post by chrisj26 on 2009-03-12
Now it does not boot with the GRUB menu. so i loaded up my PClinuxos live cd and re-installed grub n for the first time ever it installs grub successfully! but the same message comes saying : Loading grub stage 1.5 Error 17. I don't know what has happened now.I am goin 2 attempt Unetbootin now and will post back if i can boot into grub + ubuntu and then follow your instructions...thanks meierfra

---

### Post by chrisj26 on 2009-03-12
Still no luck! I can't imagine what happened between now and then!

---

### Post by sahabcse on 2009-03-12
For fixing the grub follow below url


===================================
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
==================================

---

### Post by chrisj26 on 2009-03-12
I have done that install numerous times. Also It cannot find my grub menu. Is that the reason that I'm having this problem?

---

### Post by meierfra. on 2009-03-12
> Now it does not boot with the GRUB menu. 

Did you do anything which might have cause the Grub menu to no longer appear?  Did you boot from the same drive  as the last time? 
Inconsistent behaviour usually indicates some kind of hardware problem.
And could you please tell me which drive you are booting from? 

Since you reinstalled grub, could you run the boot_info_script  and post "RESULTS.txt" again?

---

### Post by chrisj26 on 2009-03-12
Well I updated my BIOS, and for some miraculous reason which I don't care for I was getting the GRUB menu again although unable to load each of the OSes. So I edited the grub menu as you said meierfra and voila- FANTASTIC!!! thanks alot guys especially meierfra!now i just have to get my bootloader themes back

---

### Post by meierfra. on 2009-03-12
> Well I updated my BIOS, and for some miraculous reason which I don't care for I was getting the GRUB menu again although unable to load each of the OSes.


Great News. Good luck with the boot loader themes.

---

### Post by chrisj26 on 2009-03-12
Already done!

---

### Post by 3l3vans on 2009-03-12
have you tried using a live distro and re installing grub?


grub files are pretty easy to manipulate, it sounds to me like your menu.lst doesn't have the right locations for your operating systems. boot a live cd and use your favorite text editor (graphical or command line) to open the file /boot/grub/menu.lst

i can't explain EXACTLY what you should edit but htere should be notes in there explaining how it works and how to enter a windows partition.this is what mine looks like.




# GRUB configuration file 
# generated by grubconfig on dyne:bolic Fri Mar 13 00:50:14 2009
#
# for documentation about this bootloader see:
# [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
#
# Start GRUB global section
timeout 30
color light-gray/blue black/light-gray
# End GRUB global section

# Start dyne:bolic entry
title dyne:II DHORUBA
root (hd0,0)
kernel /dyne/2618ck1d.krn root=/dev/ram0 rw load_ramdisk=1 max_loop=64 vga=791
initrd /dyne/initrd.gz

# for a windlows partition use the following entry
#title Windblows
#rootnoverify (hd0,0)
#chainloader +1

title		Ubuntu 8.04.2, kernel 2.6.24-23-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=76890dbc-d5fb-4169-9dc5-6b30df87bb86 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-rt
quiet



if you look in the middle there are notes on how your windows entry should look. if you don't get it right the first time you can come back and change this file as many times as you like. once you get your head around it, its pretty easy to manipulate...good luck!

---

