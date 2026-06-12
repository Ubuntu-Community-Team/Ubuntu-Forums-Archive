---
title: "Add &quot;Macrium Recreate&quot; partition to GRUB, but &quot;FILE NOT FOUND.&quot;"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by beonubu on 2009-05-01
Hi, absolute newbie to posting so thanks ahead of time.

0) Dell D600 laptop, 1.6ghz, 40gb, 512mb;
1) Xubuntu 8.04 and WinXPpro running side by side really beautifully;
2) Win-partition mounted plus fuse from Ubu' and "Ext2IFS_1_11a.exe" installed in Win' so both have -full- access to each other;
3) Wine going, (even my own Purebasic-compiled) programs over on XP run hyper-quick on Ubu'.

Xubu' gets an a-plus in my book, took a lot of searching on this forum before getting it going, probably easy really but I was slow.

Still am.

Like to be able to recover a partition (Ubu or Win) using the "Macrium Reflect" software images, but without resorting to using the 'live cd' expertly made by the software itself: that is, copying the 'live cd' to a partition on the hard drive (and making it bootable ?) and letting GRUB run it when I have need. Hopefully never, but...

I'm getting "FILE NOT FOUND" when I select the MACRIUM-REFLECT line from the GRUB menu on boot up - hey, I'm happy after my editing that it even showed up on GRUB !

The 'live cd' is great, but why not try to recover using a small on-board partition, leaving the cd-drive free for the image file ? So I copied the complete contents of the ISO onto a mini-partition of the hard-drive, and gave it a shot.

Couldn't find a thread on this, can anyone point me in the right direction, or am I hopelessly missing the point ?

Here are part of my [menu.lst], my [sudo fdisk -l], the contents of [recreate/isolinux/isolinux.cfg] and an image of what's on the RE-CREATE partition, in case that helps. Does it matter that the RE-CREATE partition is FAT12 ? Did I miss something in making the 'live cd' that means it really has to be a cd ? Can I modify one of the files in the mini-partition to make it run from a hard-drive rather than the cd ? Am I simply pointing GRUB to the wrong file ?

Thanks again, this forum has been awesome so far, maybe this discussion is beyond me but I like the idea of self-recovery ! Sorry if it's verbose, nervous ?

Cheers.
Enc:
------------------------------------------------------------------------------------------
[MENU.lst]
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=496de904-6f6 ... ... ...
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

...
recovery modes et cetera
...

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

## This entry was added by 'ME' on 2009.05.01 to try enabling GRUB to start the MACRIUM
## RE-CREATE partition of the hard-drive, to recover Ubu' or Win' images if/when needed,
## without resorting to using the 'live' cd made by the MACRIUM RECREATE software makes...
title		Macrium Re-Create (Recovery !!!)
root		(hd0,5)
kernel		/ISOLINUX/LINUX26
initrd		/ISOLINUX/INITRD.BIN


------------------------------------------------------------------------------------------
[sudo fdisk -l]
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00040004

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1077     8650971    7  HPFS/NTFS
/dev/sda2            1078        4864    30419077+   f  W95 Ext'd (LBA)
/dev/sda5            1078        4252    25503156    7  HPFS/NTFS
/dev/sda6            4255        4256       16033+   1  FAT12
/dev/sda7            4257        4682     3421813+  83  Linux
/dev/sda8            4683        4864     1461883+  82  Linux swap / Solaris
------------------------------------------------------------------------------------------

[.../isolinux/isolinux.cfg]
default 1
prompt 1
timeout 1
display menu.txt

label 1
  kernel linux26
  append ramdisk_size=128000 initrd=initrd.bin init=/sbin/init root=/dev/ram0 console=tty2 vga=788 loglevel=2 E187A615 015B43567543A12 

label 2
  kernel linux26
  append ramdisk_size=128000 initrd=initrd.bin init=/sbin/init root=/dev/ram0 console=tty2 vga=791 loglevel=2 E187A615 015B43567543A12 
------------------------------------------------------------------------------------------

---

