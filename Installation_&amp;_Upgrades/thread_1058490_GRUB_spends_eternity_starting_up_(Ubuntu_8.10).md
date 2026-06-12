---
title: "GRUB spends eternity starting up (Ubuntu 8.10)"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Veteropinguis on 2009-02-02
MSI 975X Platinum Motherboard
nVidia 8600 GT
250 GB Seagate SATA HDD
2 GB Kingston RAM
3.2 GHz Pentium 4

Using GParted, I split up my hard drive. I used the 8.10 alternate CD to install Ubuntu to my 30 GB partition I set aside for Ubuntu. Everything went fine...until now, when I'm trying to boot in to Ubuntu.

My motherboard gave a happy beep, GRUB loaded fine, but now it's been starting up for the last 15-20 minutes. It doesn't take this long on my ancient Toshiba Satellite, which is less powerful all around.

Last time I tried to dual-boot, I couldn't boot in to Ubuntu -I left it alone for over 48 hours and it never budged- but I couldn't boot in to Windows either. I'm really hoping that I don't have to reinstall Windows again.

I know that the CD I'm using is undamaged, because I just used it on my laptop to replace Mint 6. So far everything on the laptop is running fine, though my laptop is pure Ubuntu.

What could the problem be? I can't get in to Ubuntu so I can't give any terminal info.

Here's exactly what it says on my screen right now:

Boot from (hd0,4) ext3        edff0bd1-d2ed-4e23-96fc-3a37004ef8ca
Starting up...
_ <- flashing

I'm a total Linux noob, actually, so the simpler the explanation, the better. I'm nervous about rebooting, which is why I haven't yet. I don't want to kill some process that's going on by rebooting.

Thanks a bunch.

---

### Post by wilbbe01 on 2009-02-02
You won't harm anything by rebooting.  It probably still won't work though.  Boot off of a live disk and run a few commands and paste the output.

Click on "Places" then click on every disk listed there, one at a time until you can see your 2 or 3 partitions listed on the desktop.

Find the one that has ubuntu installed on it.
Copy the text out of the file in the following location on that drive and paste it here
/boot/grub/menu.lst

Next run this command and paste the output here as well
This will help someone tell you what information your grub file should have in it
```
sudo fdisk -l
```

---

### Post by tuxxy on 2009-02-02
YOu could try restore GRUB from the LiveCD

---

### Post by Veteropinguis on 2009-02-02
menu.lst:

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
# kopt=root=UUID=edff0bd1-d2ed-4e23-96fc-3a37004ef8ca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=edff0bd1-d2ed-4e23-96fc-3a37004ef8ca

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		edff0bd1-d2ed-4e23-96fc-3a37004ef8ca
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=edff0bd1-d2ed-4e23-96fc-3a37004ef8ca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		edff0bd1-d2ed-4e23-96fc-3a37004ef8ca
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=edff0bd1-d2ed-4e23-96fc-3a37004ef8ca ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		edff0bd1-d2ed-4e23-96fc-3a37004ef8ca
kernel		/boot/memtest86+.bin
quiet

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


fdisk:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25902   208057783+   7  HPFS/NTFS
/dev/sda2           25903       30401    36138217+   5  Extended
/dev/sda5           25903       30210    34603978+  83  Linux
/dev/sda6           30211       30401     1534176   82  Linux swap / Solaris

Disk /dev/sdb: 503 MB, 503709696 bytes
255 heads, 63 sectors/track, 61 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0098dc62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          62      491872+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(60, 254, 63) logical=(61, 60, 63)

Disk /dev/sdc: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   623257122   679486963    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(623257121, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(679486962, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   567173161  1190466982   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(567173160, 0, 2)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(1190466981, 0, 3)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?         858         858           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(857, 0, 3)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(857, 0, 2)
Partition 3 does not end on cylinder boundary.
/dev/sdc4               1  1145037824  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(1145037823, 0, 3)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

I have probably done something very stupid...

---

### Post by wilbbe01 on 2009-02-02
Grub looks like it is probably set up right.  However I am not sure on the partition stuff at the bottom, as that looks a bit screwy to me.  I'll see if I can find something for you to try now.  Maybe someone else has an idea of how to fix the partition table if that is indeed screwy.

---

### Post by Veteropinguis on 2009-02-02
Thanks a ton. I've mucked around so much trying to get a dual-boot set up I figure I must have messed up something...

---

