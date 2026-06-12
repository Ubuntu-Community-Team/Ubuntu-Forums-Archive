---
title: "Windows CD fails to load after Jaunty install"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by sygnate on 2009-04-24
Hey, I've been lurking the forums for a while now and never had to post questions because the search function really answered most of them.

But now I come to you guys humbled because I can't load up windows.

More specifically, when grub loads, I see "Windows XP Pro" as an option, but when I select it, I get the terribly infamous "corrupted hal.dll" error. After doing some digging, the best way is to use the Windows CD or a recovery disc to repair the file.

Now when I insert my XP CD and get past the "Press any key to continue", I remain at a black screen while my hard drive light remains active. I'm guessing that the CD is scanning the linux partitions, but it seems endless and I end up force-rebooting back to ubuntu.

I didn't have this problem when i dual booted Ubuntu 8.10, but after this recent clean install, the problem's come up.

(side note: Both are running 32-bit operating systems)

---

### Post by Sef on 2009-04-24
In Ubuntu, do this:

Applications > Accessories > Terminal 

the copy and paste (or type) the following command:

```
sudo fdisk -l
``` (Small L)

Copy and paste the results here.

---

### Post by sygnate on 2009-04-24
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9e3f9e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        1690    13574893+   5  Extended
/dev/sda3   *        1691       19457   142713427+   7  HPFS/NTFS
/dev/sda5             997        1503     4072446   83  Linux
/dev/sda6            1504        1690     1502046   82  Linux swap / Solaris
/dev/sda7               1          12       96295+  83  Linux
/dev/sda8              13         388     3020188+  83  Linux
/dev/sda9             389         449      489951   83  Linux
/dev/sda10            450         996     4393746   83  Linux

```

---

### Post by Sef on 2009-04-24
I can see a problem.  Windows needs to be on the first primary partition, not on an extended partition.   Possibly you clone the partitions, then reinstall them, but I would see if someone has a better idea.

---

### Post by sygnate on 2009-04-24
If that's the case, wouldn't I need to reformat both my windows and linux partitions? I can always back everything up, but I'd rather find a solution just in case the problem arises again.

If anything, I guess I can just put windows in a virtual machine, but I'd rather run it natively so I don't suffer from any performance hit when running the memory intensive programs like photoshop or certain games.

---

### Post by jimbob on 2009-04-24
I have run into this before and it turned out to be the boot.ini file in XP pointing to the wrong partition.  This can happen when installing other OS's on the drive I guess.  
  
    [http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

You can get to your windows partition and repair it if you have a Gparted disk or System Rescue CD that will give you a terminal window to work from.

---

### Post by sygnate on 2009-04-24
> **jimbob said:**
> 
You can get to your windows partition and repair it if you have a Gparted disk or System Rescue CD that will give you a terminal window to work from.

Sorry if I sound ignorant, but how would I repair the partition from GParted?

Unfortunately I don't have a rescue disc, only the XP install CD. Even so, I doubt a rescue disc would be able to help at this point and the option of a complete format seems ever more effective.

---

### Post by Slim Odds on 2009-04-24
> **sygnate said:**
> Unfortunately I don't have a rescue disc, only the XP install CD. Even so, I doubt a rescue disc would be able to help at this point and the option of a complete format seems ever more effective.

You should always be able to boot from any bootable CD regardless of what's on the hard drives.

If not, you need to look at your BIOS settings, etc.

---

### Post by sygnate on 2009-04-24
> **Slim Odds said:**
> You should always be able to boot from any bootable CD regardless of what's on the hard drives.

If not, you need to look at your BIOS settings, etc.

I've tried changing the boot sequence on the BIOS to CD-ROM first followed by the HDD, and it still fails to boot. Since I'm running a Dell Inspiron 1720, I also tried booting with the "One-Time Select Boot Source" menu by pressing F12.

Other than changing the boot sequence, I haven't altered with any of the BIOS settings prior to the Jaunty install.

This is what my menu.lst looks like after installing Ubuntu 9.04:
```
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
# kopt=root=UUID=0d9e6100-79fa-4e58-b50e-764c34d2c4de ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b8a78e64-f501-4083-a1d9-40843146849b

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		b8a78e64-f501-4083-a1d9-40843146849b
kernel		/vmlinuz-2.6.28-11-generic root=UUID=0d9e6100-79fa-4e58-b50e-764c34d2c4de ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		b8a78e64-f501-4083-a1d9-40843146849b
kernel		/vmlinuz-2.6.28-11-generic root=UUID=0d9e6100-79fa-4e58-b50e-764c34d2c4de ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		b8a78e64-f501-4083-a1d9-40843146849b
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional
rootnoverify	(hd0,2)
makeactive
chainloader	+1

```


=== === ===

This is what my windows boot.ini looks like (It's not my default bootloader, but I've been reading that the "corrupted hal.dll" error can be caused by a faulty boot.ini):
```
[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

After searching, I also found a case similar to mine, but it wasn't of much help: [http://www.linuxquestions.org/questions/susenovell-60/windows-xp-installation-cd-doesnt-boot-after-suse-installation-381216/]("http://www.linuxquestions.org/questions/susenovell-60/windows-xp-installation-cd-doesnt-boot-after-suse-installation-381216/")

(Personal Note: *sigh* why does windows have to be such a necessary evil)

---

### Post by jimbob on 2009-04-24
It looks like Grub found your XP on the third partition [rootnoverify (hd0,2)] so I would try changing all entries in your boot.ini file to [ partition(3) ] according to the link I sent you and see if that will work.  Save a copy of the original just in case.

I'm sorry I can't tell you how to do it from the XP CD but if you have an Ubuntu live CD you can install it live and do it from there.

---

