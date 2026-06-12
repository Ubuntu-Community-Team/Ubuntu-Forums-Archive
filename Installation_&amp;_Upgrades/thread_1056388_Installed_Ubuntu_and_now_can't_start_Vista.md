---
title: "Installed Ubuntu and now can't start Vista"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by firstsig on 2009-01-31
I started with Vista loaded on the first hard drive and working.  

Installed Ubuntu on the second hard drive, the install worked perfectly.:D

Later, when I tried to boot into Vista if get the "boot manager failed to find OS loader".:(

I've read through thread after thread and checking people with similar issue, I've come to the conclusion that after the grub points to the "Vista Longhorn" loader the Vista loader doesn't know what to do at that point.

Any suggestions would be appreciated!

---

### Post by ugm6hr on 2009-01-31
More detail might be useful.

Boot into Ubuntu, and post the output from the following commands:
```
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by Themaverick on 2009-01-31
if you turned off APIC on your motherboard, you may need to turn it back on to boot windows. at least thats how it was for me with Xp. hope it helps

---

### Post by firstsig on 2009-01-31
Thanks for the help....

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
# kopt=root=UUID=fb9877c1-64f9-4e0f-9850-5c09e433a6d8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=fb9877c1-64f9-4e0f-9850-5c09e433a6d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-rt
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=fb9877c1-64f9-4e0f-9850-5c09e433a6d8 ro single
initrd		/boot/initrd.img-2.6.24-23-rt

title		Ubuntu 8.04.2, kernel 2.6.24-22-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=fb9877c1-64f9-4e0f-9850-5c09e433a6d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-rt
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=fb9877c1-64f9-4e0f-9850-5c09e433a6d8 ro single
initrd		/boot/initrd.img-2.6.24-22-rt

title		Ubuntu 8.04.2, kernel 2.6.24-19-rt
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=fb9877c1-64f9-4e0f-9850-5c09e433a6d8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-rt (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=fb9877c1-64f9-4e0f-9850-5c09e433a6d8 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.2, memtest86+
root		(hd1,0)
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


and the fdisk...

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce9061ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30394   244137984    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfe68315

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29638   238067203+  83  Linux
/dev/sdb2           29639       30394     6072570    5  Extended
/dev/sdb5           29639       30394     6072538+  82  Linux swap / Solaris

---

### Post by caljohnsmith on 2009-01-31
**Firstsig**, since your Ubuntu entries use (hd1,0), that means you must be booting the sda Vista drive on start up. That also means your current Vista entry that uses (hd0,0) should work, so the bottom line is that Vista may actually be missing "bootmgr" and the rest of its boot files. Was there an NTFS/FAT partition on the Ubuntu drive that you deleted when you installed Ubuntu? If so, that could have been where Vista's boot files were. How about posting the output of the following so we can see if your Vista partition is truly missing its boot files:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```

---

### Post by k3rnelmustard on 2009-01-31
@firstsig:

It's possible that vista installed its bootloader to the MBR of /dev/sdb instead of /dev/sda, even though vista itself is on /dev/sda (I've seen windows do things like this multiple times, it gets really confused with multiple drives).  Try changing
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```
to
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
chainloader +1

```

You could also try booting from the other disks MBR by specifying the other disk as the boot device in the BIOS.

---

### Post by firstsig on 2009-01-31
To caljohnsmith:
total 4496930
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2009-01-31 19:59 Boot
-rwxrwxrwx 1 root root     333203 2008-01-19 02:45 bootmgr
-rwxrwxrwx 1 root root       8192 2008-11-15 15:56 BOOTSECT.BAK
-rwxrwxrwx 3 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root          0 2008-11-06 20:43 Dell
drwxrwxrwx 1 root root       4096 2008-11-15 02:05 Dell Drivers
drwxrwxrwx 1 root root          0 2006-11-02 08:02 Documents and Settings
-rwxrwxrwx 1 root root 2145308672 2008-11-06 20:46 hiberfil.sys
-rwxrwxrwx 1 root root        353 2008-05-21 20:18 IPH.PH
-rwxrwxrwx 1 root root 2459136000 2008-11-06 20:46 pagefile.sys
drwxrwxrwx 1 root root          0 2008-05-22 19:20 PerfLogs
drwxrwxrwx 1 root root       8192 2008-11-06 20:34 ProgramData
drwxrwxrwx 1 root root      12288 2008-11-06 20:33 Program Files
drwxrwxrwx 1 root root       4096 2008-11-15 01:11 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-05-20 03:06 System Volume Information
drwxrwxrwx 1 root root          0 2009-01-31 19:54 temp
drwxrwxrwx 1 root root       4096 2008-05-19 21:51 Users
drwxrwxrwx 1 root root      28672 2008-11-06 20:48 Windows

---

### Post by firstsig on 2009-01-31
k3rnelmustard,

I tried your suggestion and tried to start Vista, got "Error 13: Invalid or unsupported executable format....:(

Any other suggestions?

---

### Post by firstsig on 2009-01-31
caljohnsmith

Yes, the Vista drive is booting on start up.  Vista was install first, then Ubuntu on the second drive. I wanted to keep them seperate. There could have been a NTFS/FAT partition on the Ubuntu drive when it was installed.

---

### Post by ugm6hr on 2009-01-31
> **firstsig said:**
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Change this to:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader	+1

```

Hopefully, this should confuse Vista into thinking it is the first boot HD.

EDIT: Not really sure about this.  It is unusual that Ubuntu is labelled as hd1 while remaining 1st boot device.  Still - worth a try...

---

### Post by firstsig on 2009-01-31
ugm6hr,

Gave that a try...same issue :( 

Let me go over this...

The computer boots into Grub....
I get the boot up choices...
Ubuntu boots and works GREAT ! :D

When I select the Vista option it says...\windows\system32\winload.exe corrupt or missing

The file is on the disk...the Vista boot manager just can't find it. :(

---

### Post by ugm6hr on 2009-01-31
Is it possible that the Vista system file got corrupted during the repartioning?

A quick google reveals that this happens a lot with partitioning etc:
[http://www.google.co.uk/search?q=\windows\system32\winload.exe+corrupt+or+missing&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox](http://www.google.co.uk/search?q=\windows\system32\winload.exe+corrupt+or+missing&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox)

I'm afraid I don't know any more to help...

---

### Post by caljohnsmith on 2009-01-31
**Firstsig**, I think you clearly have a Windows problem and not a Grub problem at this point. Also, since Vista is on the first boot drive (hd0) where it wants to be, it shouldn't be necessary to use Grub's mapping technique to fool Vista into being on (hd1), because Vista wants to boot from the first boot drive (hd0) normally. Therefore, I would recommend sticking with your original Vista entry that uses (hd0,0) and does not include the mapping lines. 

In order to try and fix Vista, how about booting your Vista Install CD, go to the command line, and do:
```
bootrec /rebuildbcd
chkdsk /r
```
And run the chkdsk command as many times as it takes until it reports no errors. Then reboot, try Vista from the Grub menu again, and let us know how far you get.

---

### Post by firstsig on 2009-01-31
ugm6hr,

I thank you for your assistance....Do you think I'll need to reinstall Vista?  And if so, could it mess up my Ubuntu?  

I hate that I need Vista to log in to the MS small business server at work :(

---

### Post by firstsig on 2009-01-31
caljohnsmith,

I already tried this a couple of times today following another thread.  Didn't change the situation. Any other suggestions?

---

### Post by caljohnsmith on 2009-01-31
Have you tried doing a "Vista Repair" from the Vista Install CD? That's about the only other thing I can think of that might realistically work short of doing a full reinstall.

---

### Post by firstsig on 2009-01-31
I tried the Visa repair first. And after again after the bootrec /rebuildbcd
chkdsk /r...no difference.

If I reinstall Vista could it mess up the Ubuntu install?

---

### Post by caljohnsmith on 2009-01-31
> **firstsig said:**
> 
If I reinstall Vista could it mess up the Ubuntu install?
Since you have Grub installed to the MBR (Master Boot Record) of the Vista drive, yes, unfortunately Vista will temporarily take away your dual boot after you reinstall it. But to get Grub back is usually easy, you can follow this guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Good luck and let us know how it goes.

---

### Post by firstsig on 2009-01-31
Many thanks to everyone who tried to my situation! The Ubuntu community is the best!

---

### Post by firstsig on 2009-02-04
caljohnsmith,

Well, just to update everyone. I had to reformat the first HD and then reload Vista.  Followed caljohnsmith's advice and the directions at the link he provided.  Now I have dual boot Vista and Ubuntu!  Thanks again for everyone's suggestions and assistance!

---

### Post by caljohnsmith on 2009-02-04
That's great news, firstsig; I'm glad you have your dual-boot setup working now. Cheers and enjoy Ubuntu and Vista. :)

---

