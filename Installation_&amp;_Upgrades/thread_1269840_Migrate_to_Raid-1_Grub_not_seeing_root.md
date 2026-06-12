---
title: "Migrate to Raid-1 Grub not seeing root"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by rtjacob on 2009-09-18
I recently setup Ubuntu 9.04 Server and had it installed on a single drive with /dev/sda1 as my root.. I got another drive and wanted to set it up as a mirror using raid level 1.. I have done this before back in the 2.4 kernel days and lilo, but I have had issues getting the array to boot.. 

What I did was partition the new drive with a /boot (/dev/sdb1) and / (/dev/sdb2) partition.. Set them both up as raid1 (I think I could have done them as one, but that's beside the point I think).. I create two raid devices /dev/md_d0 (/boot), /dev/md_d1 (/) using mdadm --create /dev/mdX --raid=level-1 --devices=2 missing /dev/sdbX.. The arrays started just fine, and I used cp -avx to move the data from /dev/hda1 onto the new arrays..  I edited the fstab on /dev/md_d1 to reflect the new / and /boot being md devices.. 

I then tried to move onto setting up grub.. I am unable to get the disk to boot except when I have the UUID of the old /dev/hda1 (still installed and untouched with the exception of the fstab being the same as the array (i.e. md_d1 as root)) in the kernel root= option.. I don't know what I am supposed to put in there... I have tried root=/dev/md_d1, and the uuid of the array (although it doesn't show up in /dev/disks/by-uuid..


```

$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : active raid1 sdb1[1]
      160512 blocks [2/1] [_U]
      
md_d1 : active raid1 sdb2[1]
      78389056 blocks [2/1] [_U]

``````

$ mount 
/dev/md_d1 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/md_d0 on /boot type ext3 (rw,relatime,errors=remount-ro)

```-- Some lines removed from the mount command

```

$ cat menu.lst
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
fallback     1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=5dcdf282-4639-4166-b650-167786116612 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5dcdf282-4639-4166-b650-167786116612

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


title        Ubuntu 9.04, kernel 2.6.28-15-server (/dev/sdb)
kernel        /vmlinuz-2.6.28-15-server root=/dev/md1 ro quiet splash 
initrd        /initrd.img-2.6.28-15-server

title        Ubuntu 9.04, kernel 2.6.28-15-server (/dev/sda)
root        (hd0,0)
kernel        /vmlinuz-2.6.28-15-server ro quiet splash 
initrd        /initrd.img-2.6.28-15-server

# original boot
title        Ubuntu 9.04, kernel 2.6.28-15-server
uuid        5dcdf282-4639-4166-b650-167786116612
kernel        /vmlinuz-2.6.28-15-server root=UUID=5dcdf282-4639-4166-b650-167786116612 ro quiet splash 
initrd        /initrd.img-2.6.28-15-server

title        Ubuntu 9.04, kernel 2.6.28-15-server (recovery mode)
uuid        5dcdf282-4639-4166-b650-167786116612
kernel        /vmlinuz-2.6.28-15-server root=UUID=5dcdf282-4639-4166-b650-167786116612 ro  single
initrd        /initrd.img-2.6.28-15-server

title        Ubuntu 9.04, kernel 2.6.28-11-server
uuid        5dcdf282-4639-4166-b650-167786116612
kernel        /vmlinuz-2.6.28-11-server root=UUID=5dcdf282-4639-4166-b650-167786116612 ro quiet splash 
initrd        /initrd.img-2.6.28-11-server
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid        5dcdf282-4639-4166-b650-167786116612
kernel        /vmlinuz-2.6.28-11-server root=UUID=5dcdf282-4639-4166-b650-167786116612 ro  single
initrd        /initrd.img-2.6.28-11-server

title        Ubuntu 9.04, memtest86+
uuid        5dcdf282-4639-4166-b650-167786116612
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

