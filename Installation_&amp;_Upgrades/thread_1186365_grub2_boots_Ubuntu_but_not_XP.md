---
title: "grub2 boots Ubuntu but not XP"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by clickwir on 2009-06-13
sudo apt-get install grub2
worked ok, using it CHAINLOADED from GRUB, changed ROOT to UUID and it loads GRUB2 and GRUB2 loads linux fine.

But when trying to load XP, I get a flashing cursor in the top left and nothing else. Locked up it appears, left it for 10 mins and nothing happened. No keyboard input.

Linux mach 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux

---

### Post by presence1960 on 2009-06-13
boot into ubuntu and run in terminal > sudo fdisk -l post the output here as well as the output of > gksu gedit /boot/grub/menu.lst BTW they are lowercase L in those commands.

---

### Post by clickwir on 2009-06-13
Sure, I can get that.

> sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00e300e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76586   615177013+  83  Linux
/dev/sda2           76587       77825     9952267+   5  Extended
/dev/sda5           76587       77825     9952236   82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d20f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x055d055d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14593   117218241    7  HPFS/NTFS


> cat /boot/grub/menu.lst

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4	



title		Chainload into GRUB 2
uuid		(hd0,0)
kernel		/boot/grub/core.img

title		--------------------------------------------------------------------
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		--------------------------------------------------------------------
root

title		Debian GNU/Linux, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro quiet splash
initrd		/boot/initrd.img-2.6.28-12-generic

title		Debian GNU/Linux, kernel 2.6.28-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro single
initrd		/boot/initrd.img-2.6.28-12-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


edit: I snipped some of the commented out lines from menu.lst. Was having trouble saving the post otherwise.

---

### Post by presence1960 on 2009-06-13
ok, if Windows is on your 400 GB sdb drive then your windows entry is correct. if that does not work then boot into BIOS and check the boot order of your hard drives. Make sure sdb 400 GB is second in the order. Then try again.

If windows is on sdc then we need new entries for Windows ..let me know

P.S. I would take out makeactive and savedefault ...they are not needed. I know a lot of people use them but they are unnecessary.

---

### Post by clickwir on 2009-06-13
Yes, the windows I want to boot is on sdb.

sdc does have an old windows on it, but I just had that around to get some data from, I don't want to boot from it (I don't think it would boot even if I tried, I should probably just take that drive out anyway)

Windows boots fine from GRUB1. It's just GRUB2 that cannot boot windows. GRUB2 menu shows both Windows installs fine, but neither actually try to boot. Just get a flashing _ in the upper left of the all black screen and no keyboard input works. I have to hard RESET my system and try booting again.

Here's my GRUB2 config file.

> cat /boot/grub/grub.cfg 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,1)
search --fs-uuid --set 32c7d694-de63-430f-af12-70dcf76b8d3c
if font /usr/share/grub/ascii.pff ; then
set gfxmode=800x600
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
set root=(hd0,1)
search --fs-uuid --set 32c7d694-de63-430f-af12-70dcf76b8d3c
menuentry "Ubuntu, linux 2.6.28-13-generic" {
	linux	/boot/vmlinuz-2.6.28-13-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro #GRUB_DISABLE_LINUX_UUID=true vga=788 quiet splash
	initrd	/boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu, linux 2.6.28-13-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-13-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro single #GRUB_DISABLE_LINUX_UUID=true vga=788
	initrd	/boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu, linux 2.6.28-12-generic" {
	linux	/boot/vmlinuz-2.6.28-12-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro #GRUB_DISABLE_LINUX_UUID=true vga=788 quiet splash
	initrd	/boot/initrd.img-2.6.28-12-generic
}
menuentry "Ubuntu, linux 2.6.28-12-generic (single-user mode)" {
	linux	/boot/vmlinuz-2.6.28-12-generic root=UUID=32c7d694-de63-430f-af12-70dcf76b8d3c ro single #GRUB_DISABLE_LINUX_UUID=true vga=788
	initrd	/boot/initrd.img-2.6.28-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	set root=(hd1,1)
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	set root=(hd2,1)
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
### END /etc/grub.d/40_custom ###

---

### Post by clickwir on 2009-06-13
I tried changing the last entry to read like this:

> menuentry "Windows XP" {
chainloader (hd1,1)+1
}


Got the same result. No errors, just hangs.

I got that slightly different syntax from here: [http://wiki.zenwalk.org/index.php?title=Welcome_to_GRUB2--replacing_Grub_legacy_or_LILO_with_GRUB2](http://wiki.zenwalk.org/index.php?title=Welcome_to_GRUB2--replacing_Grub_legacy_or_LILO_with_GRUB2)

It looks right either way, to me. But neither works. :shrug:

---

### Post by presence1960 on 2009-06-13
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
set root=(hd1,1)
chainloader +1
```

try changing set root line to set root=(hd1,0)

P.S. That is for the sdb1 windows entry in GRUB2

---

### Post by presence1960 on 2009-06-13
sorry, I just did some research on GRUB 2 and found that hard disk numbering starts at 0, but partition numbering starts at 1. Therefore (hd1,1) as you have it is correct.

---

### Post by clickwir on 2009-06-13
Yea, I was confused about that too. Seemed odd to start one at 0 and another at 1. But, oh well.

I was just booted into Windows from the main GRUB1 just fine.

Any other thoughts?

---

### Post by clickwir on 2009-06-19
As far as I can tell, GRUB2 is mature and should be able to chainload Windows fine. I saw some old stuff on chainloading not working, but that looks like it's been long since fixed.

Any other idea's?

---

