---
title: "Grub can't see WIndows partition"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by graphicsxp on 2009-07-31
Hi,
I've installed Windows Server 2008 on a NTFS partition. Then I re-installed GRUB to the MBR and I can boot Ubuntu no problem.
However Windows does not appear in the GRUB list.

At startup I've entered the GRUB prompt and I tried a few things. I've noticed that :

grub> root (hd0,  + tab key

brings up:

possible partitions are:
 partition num: 0, Filesystem tyhpe is ext2fs, partition type 0x83
partition num : 1, Filesystem type unknown, parttion type 0x7
partition num: 4, Filesystem type unknown, partition type 0x82

I believe 0 is my linux parttion. The two others could be the swap and ext parttion. In any case there should be a 4th one, the Windows one ! 

If I boot unbuntu and I launch GParted, I can see all my partitions, however there is an exclamation mark in front of the Windows one: Unable to read contetns of this file system. I think it's because it's ntfs, but at least the partition is seen.

what can I do ?

Thanks

---

### Post by merlinus on 2009-07-31
Post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by graphicsxp on 2009-07-31
Thanks for helping !

> $ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b601b5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         106        9120    72412987+  83  Linux
/dev/sda2            9121       14219    40956928    7  HPFS/NTFS
/dev/sda3           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris

$ cat /boot/grub/menu.lst

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=0e141c13-c296-4beb-b98e-69610c652a15 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0e141c13-c296-4beb-b98e-69610c652a15

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

title        Windows Server 2008
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        0e141c13-c296-4beb-b98e-69610c652a15
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0e141c13-c296-4beb-b98e-69610c652a15 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        0e141c13-c296-4beb-b98e-69610c652a15
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0e141c13-c296-4beb-b98e-69610c652a15 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0e141c13-c296-4beb-b98e-69610c652a15
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0e141c13-c296-4beb-b98e-69610c652a15 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0e141c13-c296-4beb-b98e-69610c652a15
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0e141c13-c296-4beb-b98e-69610c652a15 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        0e141c13-c296-4beb-b98e-69610c652a15
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=0e141c13-c296-4beb-b98e-69610c652a15 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        0e141c13-c296-4beb-b98e-69610c652a15
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=0e141c13-c296-4beb-b98e-69610c652a15 ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        0e141c13-c296-4beb-b98e-69610c652a15
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by merlinus on 2009-07-31
Try changing this

title        Windows Server 2008
[COLOR=Red]rootnoverify    (hd0,0)[/COLOR]
savedefault
makeactive
chainloader    +1

to this

title        Windows Server 2008
[COLOR=Red]rootnoverify    (hd0,1)[/COLOR]
savedefault
makeactive
chainloader    +1

You also might move these lines to below

### END DEBIAN AUTOMAGIC KERNELS LIST 

You also may wish to comment out this line, at least until everything is working

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]hiddenmenu[/COLOR]

---

### Post by graphicsxp on 2009-07-31
you're the man !  

[COLOR=Black]changing to [/COLOR][COLOR=Red][COLOR=Black]rootnoverify    (hd0,1) did work[/COLOR] !

[COLOR=Black]would you mind just explaining a little bit, just so I understand what's going on ?

Thanks a lot !
[/COLOR][/COLOR]

---

### Post by merlinus on 2009-07-31
Windows is on sda2.  Since numbering for these things starts at 0 (zero), it translates to (hd0,1) -- first hdd, second partition.

---

### Post by mhuisenga on 2009-07-31
Merlinus,
I'm having a very similar problem. Widows partition is on (hd0,0) and ubuntu is on 5

Grub goes straight to linux without allowing a boot option.  Can I somehow add an option or how can i select which OS I want to book?

Seperately, easy peasy doesn't recognize my wireless card...

many thanks

---

### Post by merlinus on 2009-07-31
Post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```Can't help with your wireless issue, though.  Perhaps post about it in networking and wireless forum.

---

### Post by mhuisenga on 2009-07-31
also, i think the ubuntu is on (hd0,4) not 5, this is what it says during startup. however, there is no listing for sda4...

   mhuisenga@mhuisenga-laptop:~$ sudo fdisk -l
  [sudo] password for mhuisenga: 
  
  Disk /dev/sda: 160.0 GB, 160041885696 bytes
  255 heads, 63 sectors/track, 19457 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Disk identifier: 0xd4890dc3
  
     Device Boot      Start         End      Blocks   Id  System
  /dev/sda1   *           2       11406    91610662+   7  HPFS/NTFS
  /dev/sda2           19150       19457     2474010   27  Unknown
  /dev/sda3           11407       19149    62195647+   5  Extended
  /dev/sda5           11407       18827    59609151   83  Linux
  /dev/sda6           18828       19149     2586433+  82  Linux swap / Solaris
  
  Partition table entries are not in disk order
  
  Disk /dev/sdb: 8036 MB, 8036285952 bytes
  255 heads, 63 sectors/track, 977 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Disk identifier: 0x000a2fe9
  
     Device Boot      Start         End      Blocks   Id  System
  /dev/sdb1   *           1         976     7839698    b  W95 FAT32
  mhuisenga@mhuisenga-laptop:~$ cat /boot/grub/menu.lst
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
  default             0
  
  ## timeout sec
  # Set a timeout, in SEC seconds, before automatically booting the default entry
  # (normally the first entry defined).
  timeout                        0
  
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
  # title               Windows 95/98/NT/2000
  # root               (hd0,0)
  # makeactive
  # chainloader   +1
  #
  # title               Linux
  # root               (hd0,1)
  # kernel           /vmlinuz root=/dev/hda2 ro
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
  # kopt=root=UUID=1fb575c2-7aa3-4da0-9ca7-ee4e144455e2 ro
  
  ## default grub root device
  ## e.g. groot=(hd0,0)
  # groot=1fb575c2-7aa3-4da0-9ca7-ee4e144455e2
  
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
  
  title                  Easy Peasy 1.0, kernel 2.6.27-8-eeepc
  uuid                 1fb575c2-7aa3-4da0-9ca7-ee4e144455e2
  kernel              /boot/vmlinuz-2.6.27-8-eeepc root=UUID=1fb575c2-7aa3-4da0-9ca7-ee4e144455e2 ro quiet splash 
  initrd               /boot/initrd.img-2.6.27-8-eeepc
  quiet
  
  title                  Easy Peasy 1.0, kernel 2.6.27-8-eeepc (recovery mode)
  uuid                 1fb575c2-7aa3-4da0-9ca7-ee4e144455e2
  kernel              /boot/vmlinuz-2.6.27-8-eeepc root=UUID=1fb575c2-7aa3-4da0-9ca7-ee4e144455e2 ro  single
  initrd               /boot/initrd.img-2.6.27-8-eeepc
  
  title                  Easy Peasy 1.0, memtest86+
  uuid                 1fb575c2-7aa3-4da0-9ca7-ee4e144455e2
  kernel              /boot/memtest86+.bin
  quiet
  
  ### END DEBIAN AUTOMAGIC KERNELS LIST
  
  # This is a divider, added to separate the menu items below from the Debian
  # ones.
  title                  Other operating systems:
  root
  
  
  # This entry automatically added by the Debian installer for a non-linux OS
  # on /dev/sda1
  title                  Microsoft Windows XP Home Edition
  root                  (hd0,0)
  savedefault
  chainloader      +1
  
  
  # This entry automatically added by the Debian installer for a non-linux OS
  # on /dev/sda2
  title                  Windows Vista/Longhorn (loader)
  root                  (hd0,1)
  savedefault
  chainloader      +1

---

### Post by merlinus on 2009-07-31
> 
/dev/sda2           19150       19457     2474010   27  Unknown
What is on this partition?  Also, you have two window entries at the end of menu.lst, one for xp on sda1 and one for vista on sda2, but that appears to be some unknown filesystem to fdisk.

Not having an sda4 is fine, because sda3 is an extended partition, and numbering for linux after that starts at 5.

---

### Post by mhuisenga on 2009-07-31
I'm not sure exactly waht sda2 is, but its a 2 GB fat32 labeled "servicev002" from what i can tell in partion editor.

My gues is that this is the drive where the Lenovo "quick start" utilities are located. These new machines have a quick boot utility that allows web access/skype etc without goign through full boot up

Does this make senes?

---

### Post by mhuisenga on 2009-07-31
im not worried about the Vista partition, only need XP working

---

### Post by merlinus on 2009-07-31
Change this

# This entry automatically added by the Debian installer for a non-linux OS
  # on /dev/sda1
  title                  Microsoft Windows XP Home Edition
  [COLOR=Red]root                  (hd0,0)[/COLOR]
  savedefault
chainloader      +1

to

# This entry automatically added by the Debian installer for a non-linux OS
  # on /dev/sda1
  title                  Microsoft Windows XP Home Edition
  [COLOR=Red]rootnoverify                  (hd0,0)[/COLOR]
  savedefault
[COLOR=Red]makeactive[/COLOR]
  chainloader      +1

and delete this
  
  # This entry automatically added by the Debian installer for a non-linux OS
  # on /dev/sda2
  title                  Windows Vista/Longhorn (loader)
  root                  (hd0,1)
  savedefault
  chainloader      +1

---

### Post by mhuisenga on 2009-07-31
Thanks, but how can i change/edit this?
Mike

---

### Post by merlinus on 2009-07-31
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by mhuisenga on 2009-07-31
ok, i made the change, saved, checked to see that the change was successfully made. 
But Grub still boots from (hd0,4) automatically, bummer

is there anything else i can do?

---

### Post by merlinus on 2009-07-31
Change this

## timeout sec
  # Set a timeout, in SEC seconds, before automatically booting the default entry
  # (normally the first entry defined).
  [COLOR=Red]timeout                        0[/COLOR]

to this

## timeout sec
  # Set a timeout, in SEC seconds, before automatically booting the default entry
  # (normally the first entry defined).
  [COLOR=Red]timeout                        10[/COLOR]

That will give you 10 seconds to change the default by arrowing down to windows.

---

### Post by mhuisenga on 2009-07-31
Exactly what I was looking for!

Thanks Merlinus, very helpful!!

---

### Post by merlinus on 2009-07-31
Glad it is working.  Have fun!

---

