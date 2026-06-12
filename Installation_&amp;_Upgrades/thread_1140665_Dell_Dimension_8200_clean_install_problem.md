---
title: "Dell Dimension 8200 clean install problem"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by stangjc on 2009-04-27
I'm having trouble trying to install Ubuntu 9.04 on my dell dimension 8200. Every time it hangs up on the start splash screen after I select the language only showing the pointer, even on safe graphic mode and oem install. I don't wont to go back to windows!!! Please help.

---

### Post by Sef on 2009-04-27
Instead of installing, go down to "Check Disk for Errors" (or something similar.)   Make sure that the disk and iso are good.

---

### Post by stangjc on 2009-04-28
I did check the disk and none were found. I used the same disk to do installs on three other computers that I built with no problems. For some reason it just don't like this POS dell computer. Any other advice?

---

### Post by paulop on 2009-08-18
Hi stangjc, I'm having exactly the same problems as you with my Dimension 8200. Did you manage to solve the issue and get it to install? I've see other users say they can get 9.04 installed OK on an 8200 so it must be feasible. I tried various different boot options by using the F6 key but no luck yet.

---

### Post by presence1960 on 2009-08-18
if your dell will boot from a usb try making a bootable USB with [unetbootin]("http://unetbootin.sourceforge.net/") or

Try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Talar on 2010-06-26
I'm having a similar problem. Installing with the alternate installer seemed to work at first, but the system wont boot up after install. I'll let you know if I figure it out.

Edit: Starting it up with the 9.10 live cd works much better, probably has to do with the graphics card and acceleration effects.

---

### Post by presence1960 on 2010-06-26
> **Talar said:**
> I'm having a similar problem. Installing with the alternate installer seemed to work at first, but the system wont boot up after install. I'll let you know if I figure it out.

Edit: Starting it up with the 9.10 live cd works much better, probably has to do with the graphics card and acceleration effects.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Talar on 2010-09-04
It has been a while, but I have now decided to attack the problem again. Trying to boot the system with a 10.10b disc gives the same problem, I can briefly see some symbol in the bottom of the screen, then the screen just goes black and doesn't seem to get any video input at all.

presence1960, I followed your instructions using a 9.10 livecd and have pasted the output below.




```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00006804

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   625,141,759   624,640,002   5 Extended
/dev/sda5             501,760   625,141,759   624,640,000  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e6db77a8-100c-481c-a478-955a91c245d3   ext2                                     
/dev/sda5        0IB2XP-6M8D-qbMg-Bx8x-V71V-10gm-vHJtPW LVM2_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


============================= sda1/grub/grub.cfg: =============================

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
insmod lvm
insmod ext2
set root='(ubuntu-root)'
search --no-floppy --fs-uuid --set 2cdd44fd-1c6e-44ce-a381-83d61d3359b7
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
search --no-floppy --fs-uuid --set e6db77a8-100c-481c-a478-955a91c245d3
set locale_dir=($root)/grub/locale
set lang=C.UTF-8
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
	search --no-floppy --fs-uuid --set e6db77a8-100c-481c-a478-955a91c245d3
	linux	/vmlinuz-2.6.32-21-generic root=/dev/mapper/ubuntu-root ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e6db77a8-100c-481c-a478-955a91c245d3
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=/dev/mapper/ubuntu-root ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e6db77a8-100c-481c-a478-955a91c245d3
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e6db77a8-100c-481c-a478-955a91c245d3
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: vmlinuz-2.6.32-21-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  70 65 72 00 46 61 69 6c  65 64 20 74 6f 20 69 6e  |per.Failed to in|
00000010  69 74 69 61 6c 69 7a 65  20 64 72 69 76 65 72 20  |itialize driver |
00000020  69 6e 74 65 72 66 61 63  65 00 00 00 44 72 69 76  |interface...Driv|
00000030  65 72 20 69 6e 74 65 72  66 61 63 65 20 72 65 6a  |er interface rej|
00000040  65 63 74 65 64 20 64 72  69 76 65 72 5f 70 61 72  |ected driver_par|
00000050  61 6d 20 27 25 73 27 00  44 72 69 76 65 72 20 69  |am '%s'.Driver i|
00000060  6e 74 65 72 66 61 63 65  20 72 65 70 6c 61 63 65  |nterface replace|
00000070  64 20 69 6e 74 65 72 66  61 63 65 20 6e 61 6d 65  |d interface name|
00000080  20 77 69 74 68 20 27 25  73 27 00 00 49 6e 76 61  | with '%s'..Inva|
00000090  6c 69 64 20 57 50 41 20  70 61 72 61 6d 65 74 65  |lid WPA paramete|
000000a0  72 20 76 61 6c 75 65 20  66 6f 72 20 64 6f 74 31  |r value for dot1|
000000b0  31 52 53 4e 41 43 6f 6e  66 69 67 50 4d 4b 4c 69  |1RSNAConfigPMKLi|
000000c0  66 65 74 69 6d 65 00 00  49 6e 76 61 6c 69 64 20  |fetime..Invalid |
000000d0  57 50 41 20 70 61 72 61  6d 65 74 65 72 20 76 61  |WPA parameter va|
000000e0  6c 75 65 20 66 6f 72 20  64 6f 74 31 31 52 53 4e  |lue for dot11RSN|
000000f0  41 43 6f 6e 66 69 67 50  4d 4b 52 65 61 75 74 68  |AConfigPMKReauth|
00000100  54 68 72 65 73 68 6f 6c  64 00 00 00 49 6e 76 61  |Threshold...Inva|
00000110  6c 69 64 20 57 50 41 20  70 61 72 61 6d 65 74 65  |lid WPA paramete|
00000120  72 20 76 61 6c 75 65 20  66 6f 72 20 64 6f 74 31  |r value for dot1|
00000130  31 52 53 4e 41 43 6f 6e  66 69 67 53 41 54 69 6d  |1RSNAConfigSATim|
00000140  65 6f 75 74 00 00 00 00  46 61 69 6c 65 64 20 74  |eout....Failed t|
00000150  6f 20 69 6e 69 74 69 61  6c 69 7a 65 20 63 6f 6e  |o initialize con|
00000160  74 72 6f 6c 20 69 6e 74  65 72 66 61 63 65 20 27  |trol interface '|
00000170  25 73 27 2e 0a 59 6f 75  20 6d 61 79 20 68 61 76  |%s'..You may hav|
00000180  65 20 61 6e 6f 74 68 65  72 20 77 70 61 5f 73 75  |e another wpa_su|
00000190  70 70 6c 69 63 61 6e 74  20 70 72 6f 63 65 73 73  |pplicant process|
000001a0  20 61 6c 72 65 61 64 79  20 72 75 6e 6e 69 6e 67  | already running|
000001b0  20 6f 72 20 74 68 65 20  66 69 6c 65 20 77 00 3b  | or the file w.;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 40 3b 25 00 00  |...........@;%..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Talar on 2010-09-16
Eventually got it working. Ubuntu 10.10 Beta Alternate install with nomodeset got me a working installation, seems to be a driver problem with the Geforce3 Ti500 card.

---

