---
title: "Dualboot Issue: Windows Drive Found, Not Booting"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by Tinman131 on 2009-06-20
Hey all - 

Alright, so I bought a second hard-drive for my machine running XP Home.  I installed Hardy Heron on the second hard-drive without a hitch.  When I configured grub to find the other hard drive--the one with XP--so I could have the option to boot from either drive, I stuck the following code in at the bottom of menu.lst:

title Microsoft Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

After this, and changing the hidden and timeout lines, it worked fine--it brought up the memtest and "safe-mode" options as well.  There at the bottom was "Win XP," so I tried to boot from that.  When I did, however, I was taken to my motherboard (Dell) diagnostics program.  Closing the program simply restarted my machine.  To test some stuff, I simply tried to boot from the WinXP drive alone (Heron drive was unattached), but was still taken to the mobo diagnostics page.

Any idea what's causing this?

Note: more details to come in a few minutes.

[EDIT]: As per merlinus' request, here are the results of fdisk and the text of my menu.lst:

sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031cbc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           9       72261   de  Dell Utility
/dev/sdb2   *          10        9264    74340787+   7  HPFS/NTFS
/dev/sdb3            9265        9725     3702982+  db  CP/M / CTOS / ...

(The following bit is kind of long, obviously--sorry!)
# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
timeout        30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=46ffabfc-b617-4bda-a0ca-6ba1baceff86 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=46ffabfc-b617-4bda-a0ca-6ba1baceff86 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=46ffabfc-b617-4bda-a0ca-6ba1baceff86 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=46ffabfc-b617-4bda-a0ca-6ba1baceff86 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=46ffabfc-b617-4bda-a0ca-6ba1baceff86 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by ajgreeny on 2009-06-20
> Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           9       72261   de  Dell Utility
/dev/sdb2   *          10        9264    74340787+   7  HPFS/NTFS
/dev/sdb3            9265        9725     3702982+  db  CP/M / CTOS / ...From this your windows stanza in menu.lst should read 
```
title           Microsoft Windows XP
root            (hd1,1)
savedefault
makeactive
chainloader     +1 	
```
and I don't think it needs the two map lines you have added.  Give that a try and it may work for you.
Just out of interest, what on earth is the sdb3 partition all about?  Isit another dell utility partition of some kind as I don't recognise the end of that line in your fdisk output.

---

### Post by presence1960 on 2009-06-20
if ajgreeny's windows entry does not boot add the map lines back because windows needs to think it is on the first boot device.

---

### Post by lindsay7 on 2009-06-21
You need to make the changes that ajgreeny gave you and you may need the map lines that presense1960 points out.

I also think that your bios hard drive booting priority may have gotten changed when you added the new drive and this could be causing some of the problem.  Regardless the changes to the grub menu need to be made, but if you still have problems you may need to try to change the hard drive boot priority setting in  your bios settings. You may need to chage this setting so the the other drive starts first.

So, make the chages as pointed out and if needed go into the bios and try changing the hard drive boot order.

---

### Post by Tinman131 on 2009-06-23
Hokay, sorry about the delay.  A busy weekend!

I'm going to implement the suggestions and see what I can come up with.  I hope this works--the last time I tried messing around with the boot sequence, I ended up with an error 17 and had to reinstall everything.  Yikes!

Note: I fixed the Windows mobo diagnostics thing ... so now, if need be, I can manually switch between Windows and Linux.  That'd mean opening my case, though, and I'd really rather not do that.

I'll let you know what I find!  Other suggestions are welcome.  :-)

---

### Post by Tinman131 on 2009-06-23
Okay, it works!  Thanks a bunch, guys.  

Now I have another question.

Linux still treats the Windows drive like a secondary drive (shows up under the system) and I can mount it on my desktop.  Furthermore, some things I install on my Windows machine end up as links on my Linux desktop (like ... I patched a program and now the patch shows up on my Linux machine--I can't remove it, either) that go nowhere and can't be modified.  

Has anyone ever heard of this happening before?

[You know, sometimes I wonder why I even wanted access to Windows again in the first place...]

---

