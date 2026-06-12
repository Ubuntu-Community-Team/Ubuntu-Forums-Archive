---
title: "Need help on booting Vista"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by awca22 on 2009-03-08
today i installed ubuntu on my pc and i worked with it for a few hours and when i wantedd to go back to vista in the grub it shows
Ubuntu kernel (something i dont remember)
ubuntu safe mode or something like that
memtes
vista

when i press vista it only show that it is starting
what should i do?

look  copied from the menu.lst

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00c7a1f2-7319-4259-8b73-3934dede2e0e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00c7a1f2-7319-4259-8b73-3934dede2e0e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

I have 2 hard drives /dev/sda/ here i only have files music and movies
the second one is /dev/sdb/ in dev/sdb1 is installed ubuntu and in dev/sdb2 is vista

how do i fix it?

---

### Post by Neo_The_User on 2009-03-08
OK... What happens when you select vista in the GRUB boot loader menu? (Stage 1.5)

---

### Post by awca22 on 2009-03-08
it just stucks it look like if its moving but i waited like 10 min and didnt continued!

---

### Post by awca22 on 2009-03-08
if i cant solve this i must wipe out the ubuntu partition cause in windows its all my work files! sorry 4 my bad english

---

### Post by awca22 on 2009-03-08
please someone help me!!! :(

---

### Post by Mark Phelps on 2009-03-08
First of all, you need to understand that this is a self-help forum -- not a paid help desk!!  So, posting every few minutes is not going to get you better service.

As to the help ...

Your GRUB menu looks correct.

Did you attempt to install on the Vista volume or otherwise try to resize it?  IF so, the Vista OS is probably corrupt -- and unfortunate side-effect of using Linux utilities to resize Vista OS partitions.

Are you booting from your Vista drive or your Ubuntu drive? I'm guessing the Ubuntu drive.  If that's correct, do the following:
1) Powerdown your PC
2) Disconnect the Ubuntu drive
3) Reboot the PC, change the BIOS to boot from the Vista drive
4) See if Vista comes up now -- I'm guessing it won't.  If it does, report that as to what happens next is different.

Presuming Vista still does not boot:
1) Go to the NeoSmart.com forums and download their Vista Recovery CD image (I'm presuming you're running 32-bit).
2) Burn the Boot CD image using Brasero or K3B (in Ubuntu)  (you'll have to reconnect your Ubuntu drive, and reset the BIOS to boot from that drive before you do this)
3) Disconnect the Ubuntu drive again, and reset to boot from the Vista drive
4) Boot from the recovery CD you burned and run Startup Repair
5) Reboot the PC. Vista should boot now.

If all this has gone OK:
1) Reconnect the Ubuntu drive and reset the BIOS to boot from that drive
2) You should be able to boot into either OS now

And ... remember ... we're all volunteers here ... so show some patience and dont' expect an answer in a few minutes.

---

### Post by klytu on 2009-03-08
> **awca22 said:**
> please someone help me!!! :(

Try to stay calm. :-) We'll try to help. If you haven't wiped out your Ubuntu partition yet, we need some more info to help you. Please type the following in a terminal window (the terminal launcher is in the Applications>Accessories menu) and post the output:

```
sudo fdisk -l
```

Also what is the full contents of the files "/boot/grub/menu.lst" and "/boot/grub/device.map" ? You can either copy and paste the contents of the files into your post or you can attach them to your post.

---

### Post by awca22 on 2009-03-08
Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x954f8836

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda2               2       19457   156280320    5  Extendida
/dev/sda5               2       19457   156280288+   7  HPFS/NTFS

Disco /dev/sdb: 164.6 GB, 164696555520 bytes
255 cabezas, 63 sectores/pista, 20023 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x71f971f9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        6374    51199123+   5  Extendida
/dev/sdb2   *        6375       20023   109633536    7  HPFS/NTFS
/dev/sdb5               1        5471    43945744+  83  Linux
/dev/sdb6            5472        6374     7253316   82  Linux swap / Solaris

---

### Post by awca22 on 2009-03-08
well vista is installed on the same drive ubuntu is. thats why i cant disconnect it..

---

### Post by klytu on 2009-03-08
> **awca22 said:**
> Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x954f8836

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda2               2       19457   156280320    5  Extendida
/dev/sda5               2       19457   156280288+   7  HPFS/NTFS

Disco /dev/sdb: 164.6 GB, 164696555520 bytes
255 cabezas, 63 sectores/pista, 20023 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x71f971f9

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        6374    51199123+   5  Extendida
/dev/sdb2   *        6375       20023   109633536    7  HPFS/NTFS
/dev/sdb5               1        5471    43945744+  83  Linux
/dev/sdb6            5472        6374     7253316   82  Linux swap / Solaris

Good so far. Need the contents of the other files as well: 

/boot/grub/menu.lst
/boot/grub/device.map

---

### Post by awca22 on 2009-03-08
this is from device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdd

and menu.lst is at the first post

---

### Post by awca22 on 2009-03-08
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdd
Taken from device.map

the menu.lst is at the first post

sorry double post

---

### Post by klytu on 2009-03-08
> **awca22 said:**
> this is from device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdd

and menu.lst is at the first post

You chopped off all the default options from the first menu.lst post and posted an excerpt. Please post the whole menu.lst file. Thanks ..

---

### Post by awca22 on 2009-03-08
menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=00c7a1f2-7319-4259-8b73-3934dede2e0e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=00c7a1f2-7319-4259-8b73-3934dede2e0e

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
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00c7a1f2-7319-4259-8b73-3934dede2e0e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00c7a1f2-7319-4259-8b73-3934dede2e0e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

This is the complete

---

### Post by klytu on 2009-03-08
> **awca22 said:**
> menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=00c7a1f2-7319-4259-8b73-3934dede2e0e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=00c7a1f2-7319-4259-8b73-3934dede2e0e

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
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00c7a1f2-7319-4259-8b73-3934dede2e0e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=00c7a1f2-7319-4259-8b73-3934dede2e0e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		00c7a1f2-7319-4259-8b73-3934dede2e0e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista/Longhorn (loader)
root		(hd1,1)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

This is the complete

OK. This looks good. I think the problem you are having may be because Vista is not located on your first physical hard drive. The other possibility is that you resized your original Vista partition with a Linux utility rather than with Vista's built-in partitioning tool. If you have an original Vista disk, you can use the tools on it to fix the Vista partition.

EDIT: Just read Mark Phelps' post which appear after mine for some reason. Follow his advice. Letting the BIOS boot from your Vista drive will rule out whether the issue is that Vista isn't booting from the first hard drive. And his remaining steps should restore your Vista partition if it became corrupt during a re-size with a Linux utility.

---

