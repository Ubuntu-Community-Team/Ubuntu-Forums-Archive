---
title: "Dual Hard Drive setup"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by FraggedLocust on 2009-07-05
I recently set up a new hard drive with windows, and wiped my old hard drive and put Ubuntu on it. My main problem is that when I edited menu.lst, XP complains that the NT bootloader is missing. Shouldn't grub be able to simulate/run windows' bootloader?

Here's what I have so far for menu.lst
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
timeout		3

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
# kopt=root=UUID=8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
```

---

### Post by x22 on 2009-07-05
> title		Windows XP
> root		(hd1,0)
> makeactive
> chainloader	+1

assuming XP is on first HD, first partition, then
"root (hd0,0)" would be the thing

---

### Post by NewbieNik on 2009-07-05
It may also be pointing at the wrong partition.

When you say you set up your new HD with windows, how did you go about this?
There is a possibility that your MBR was on the drive you wiped, in which case you would need to run the windows set-up again in repair mode and run the fixmbr command. (See Microsoft for this as it is a Windows, not an Ubuntu issue)
Unfortunately, this will break your linux install as it will re-point the boot records to Windows rather than grub. There are ways of fixing grub again, but Can, Worms and Open all apply.

Or you could:-
Take out your ubuntu disk and see if windows boots, if not then you could run the fixmbr on that drive (Leaving Ubuntu out of the loop), then replace the ubuntu drive once you are happy Windows loads OK.
REMEMBER.....BACK UP EVERYTHING.
If you lose data I will not accept responsibility although I promise I will feel slightly sorry for you

---

### Post by presence1960 on 2009-07-05
Let's cut to the chase here. Download to your desktop the Boot Info Script from here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Then open a terminal and run this command : ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on your desktop. This contains all the info about your setup & boot info. Paste the contents of the file here. Once pasted here highlight all text and click # on the toolbar to place code tags around the text.

I can tell you now the entry you were told to enter in menu.lst for windows is incorrect because windows & ubuntu are on separate hard disks- therefore you need map lines in that entry.

If you need to restore NTLDR you do not have to unplug your Ubuntu drive. Just change the windows disk to first boot in the order of hard disk boot in BIOS. It is totally unnecessary to open up your box. But the boot info script will tell us if that (restore NTLDR) is necessary as well as a plethora of other info about your machine.

---

### Post by QIII on 2009-07-05
XP also has a bit of a quirk in that it likes to be the 0 hd.

It is not always necessary, but adding

map (hd0) (hd1)
map (hd1) (hd0)

just after the root line MAY help.

---

### Post by presence1960 on 2009-07-05
> **QIII said:**
> XP also has a bit of a quirk in that it likes to be the 0 hd.

It is not always necessary, but adding

map (hd0) (hd1)
map (hd1) (hd0)

just after the root line MAY help.

those lines become necessary when windows is not on the disk booting- like when you have separate hard disks, usually people have the ubuntu disk booting first. They are also necesary in the same situation with Win 2000, XP, Vista & win 7 RC.

---

### Post by QIII on 2009-07-05
Yes.  I should have been more generic.  The OP was talking about XP, so I concentrated on that.

And both of the conditions you described are true, hence my advice.

Again, I probably should have explained why I responded to the OP as I did.

---

### Post by presence1960 on 2009-07-05
> **QIII said:**
> Yes.  I should have been more generic.  The OP was talking about XP, so I concentrated on that.

And both of the conditions you described are true, hence my advice.

Again, I probably should have explained why I responded to the OP as I did.

I know what you meant, I have read many of your posts and find your knowledge good. I only posted that for the benefit of others reading this that really don't know this stuff.

---

### Post by QIII on 2009-07-05
I was really only scolding myself for not explaining myself to someone who likely didn't understand why I wrote what I did.

I hate it when others do that.

I really hate it when I do that!

---

### Post by presence1960 on 2009-07-05
we all do that sooner or later, that's the nature of the beast in a no contact words only forum.

---

### Post by FraggedLocust on 2009-07-06
Okay, I think I'm able to further clarify my problem.

Hard disk 1 -- the old Windows Drive, now with Ubuntu using GRUB.
- Booting from hd(0,0)
Hard Disk 2 -- the new Windows Drive, still trying to boot using the windows bootloader. (that it can't find)
- Booting from an unknown hd(X,X) location (most likely hd(1,0))

My BIOS is set up so that the windows Drive is the primary master. And when it boots, it does it's error thing. But if I interrupt the boot process and boot from the ubuntu drive, GRUB runs properly and can boot ubuntu, but selecting the windows option brings up the error.

Here's selected parts of results.txt as presence1960 requested:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d631d63

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   154,191,869   154,191,807  83 Linux
/dev/sda2         154,191,870   160,826,714     6,634,845   5 Extended
/dev/sda5         154,191,933   160,826,714     6,634,782  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c0c3c0b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,121,279   625,121,217   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8c0f7436-7efa-4714-9d7c-3fe0a9b7dffc" TYPE="ext3" 
/dev/sda5: UUID="6744cf76-14b7-4fc9-b643-92aff9deaf18" TYPE="swap" 
/dev/sdb1: UUID="081CD0A61CD09054" TYPE="ntfs" 


```

---

### Post by presence1960 on 2009-07-06
you have no boot files in your XP partition, see here in red:

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    [COLOR="Red"]Boot files/dirs: [/COLOR]  

I would try this to restore windows bootloader: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Hopefully that will restore them, if not your windows is never going to boot. 
If not you may have to reinstall windows. You are missing boot.ini & NTLDR. Try that fix and see what happens when you boot off the Windows drive, hopefully that fixes it and windows will boot. If successful we can get your GRUB set up but first you need to get windows squared away.

P.S> next time paste the entire contents of the RESULTS.txt file so we can see all the info about your setup and boot info.

here is what your windows partition should look like in regards to boot files in the RESULTS.txt file:

 File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

compare the last line boot files/dirs to yours.

---

### Post by FraggedLocust on 2009-07-07
Running fixboot and fixmbr seems to have wiped out GRUB, which I assumed would happen, but now either drive is showing NT Loader missing, and I can't boot into Ubuntu.

I have a SuperGRUB disk, could I restore the grub and the windows loader from that?

---

### Post by presence1960 on 2009-07-07
> **FraggedLocust said:**
> Running fixboot and fixmbr seems to have wiped out GRUB, which I assumed would happen, but now either drive is showing NT Loader missing, and I can't boot into Ubuntu.

I have a SuperGRUB disk, could I restore the grub and the windows loader from that?

It looks like you have a bad install of Windows. Since fix boot & fixmbr didn't restore the boot files you are probably going to have to rreinstall Windows.

Give super grub disk a shot. I know it will restore GRUB, hopefully it can restore your missing windows files. If not reinstall windows.

---

