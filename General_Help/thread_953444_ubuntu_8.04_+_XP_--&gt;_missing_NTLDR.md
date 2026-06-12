---
title: "ubuntu 8.04 + XP --&gt; missing NTLDR"
date: 2008-10-20
forum: General Help
---

### Post by Zakarum on 2008-10-20
Hi there. 

I got a little problem with my Grub  I had Wxp installed on my laptop, i did a new Ubuntu instalation and was ok until here...

ubuntu 8.04 is running fine as usual, but by default the XP partition was not listed on the menu.lst so i added it manually(i did it on previous versions and was always Ok.)

But now when i try to access to my XP partition it says something like "cannot find NTDLR". As far i heard this problem is usually solved with the XP instalation disc, but my fear is.... If i restore it with the XP cd, the Grub will still working or the xp boot will replace the linux GRub?

Thank you.

PS: No flames please >D

---

### Post by PocketDog on 2008-10-20
I read a thread about this very thing this morning funnily enough, and it was a simple solution I haven't seen before, so it stuck in my mind. Does [**this**](http://ubuntuforums.org/showthread.php?t=845602&highlight=ntldr) help?

---

### Post by caljohnsmith on 2008-10-20
Please first post:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
And we can work from there. :)

---

### Post by Zakarum on 2008-10-21
Here we go. 

sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x71a7ead9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   244139804   122069871   83  Linux
/dev/sda2       244139805   249569774     2714985    5  Extended
/dev/sda3   *   249571328   488392703   119410688    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda5       244139868   249569774     2714953+  82  Linux swap / Solaris


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
color cyan/blue white/blue

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
# kopt=root=UUID=d2cf947e-2a0a-4d95-b327-86eb606edce3 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d2cf947e-2a0a-4d95-b327-86eb606edce3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d2cf947e-2a0a-4d95-b327-86eb606edce3 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d2cf947e-2a0a-4d95-b327-86eb606edce3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d2cf947e-2a0a-4d95-b327-86eb606edce3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP Professional
root 		(hd0,2)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

Thx. 

@pocket that topic is for 2 hdds, right?

---

### Post by caljohnsmith on 2008-10-21
Since your Windows is on sda3, your Grub menu entry for it should work; I think then that it's clear you have a Windows problem and not a Grub problem at this point since you got the "missing ntldr" error. Probably you are just missing your Windows boot files is all, which will be easy to fix. Was Windows originally installed to sda3, or did you move it there or install it there yourself? 

Please post the output of:
```
sudo mount /dev/sda3 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L, not a one. Does that directory listing show the following three files:
```
boot.ini
ntldr
NTDETECT.COM
```
If not, your Windows boot files were probably originally placed in some other partition, and then subsequently you unintentionally deleted them when you installed Ubuntu. Let me know if you don't have those boot files, and we can work from there.

---

### Post by Zakarum on 2008-10-21
Nope, the files are not there. 

ls -l /mnt
total 2095170
drwxrwxrwx 1 root root      12288 2008-10-15 21:45 Archivos de programa
drwxrwxrwx 1 root root       4096 2008-10-01 16:43 Documents and Settings
drwxrwxrwx 1 root root          0 2008-10-02 11:35 Intel
-rwxrwxrwx 1 root root 2145386496 2008-10-17 20:08 pagefile.sys
drwxrwxrwx 1 root root          0 2008-10-01 17:29 RECYCLER. 
-rwxrwxrwx 2 root root        268 2008-10-08 19:35 sqmdata00.sqm
-rwxrwxrwx 2 root root        244 2008-10-08 19:35 sqmnoopt00.sqm
drwxrwxrwx 1 root root       4096 2008-10-01 17:16 System Volume Information
drwxrwxrwx 1 root root          0 2008-10-14 19:13 Temp
-rwxrwxrwx 1 root root       5224 2008-10-11 12:43 WIFIWAY2.TXT
drwxrwxrwx 1 root root      36864 2008-10-14 22:51 WINDOWS

PS: I tried to put the files manually there but was unsuccessfull. 

Thank you

---

### Post by caljohnsmith on 2008-10-21
So just out of curiosity, how did Windows end up on sda3? I've attached the three boot files you need to my post, and they contain a modified boot.ini since your Windows is on sda3. If you download the "Windows_boot_files.tar.gz" to your desktop, then just do the following to put them in your Windows directory:
```
mount /dev/sda3 /mnt   (just to make sure sda3 is still mounted on /mnt)
cd ~/Desktop
tar xvf Windows_boot_files.tar.gz
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Reboot, choose Windows in the Grub menu, and let me know what happens or if you get any errors. :)

---

### Post by Zakarum on 2008-10-21
I've already tried with another boot files from another computer. I have not the laptop here so i can't put the exact error i got when i manually put the files into /mnt, but it was something like that:
(after  select de windows entry)
Windows XP
Windows Default

The first one simply said that the" partition was not correct" and the second one that "there was a somekind of disk error, consult the Win documentation blah blah".

---

### Post by caljohnsmith on 2008-10-21
Yes, I understood that you tried the boot files from another computer, but like I mentioned in my previous post, I especially modified the boot.ini file that I attached to work for your system since you have Windows on sda3. So unless the other computer had Windows also on sda3, and also with an extended partition as sda1 or sda2 like your setup, the boot.ini file from that computer won't work for you. That's probably exactly why it gave you a "partition not correct" error.

---

### Post by Zakarum on 2008-10-22
It worked! Thank you very much :>

The problem was probably... I bought the laptop some weeks ago with Vista preinstalled. I did a new partition and installed XP and then i formatted and installed Ubuntu on the Vista partition... that was the problem, right?

---

### Post by caljohnsmith on 2008-10-22
> **Zakarum said:**
> It worked! Thank you very much :>

The problem was probably... I bought the laptop some weeks ago with Vista preinstalled. I did a new partition and installed XP and then i formatted and installed Ubuntu on the Vista partition... that was the problem, right?
That's great news it's working now. Most likely what happened is when you installed XP, it put its boot files in the Vista partition, so when you installed Ubuntu over Vista, the boot files were deleted. Anyway, it's not a big issue as you can see, the main thing is just making sure the boot.ini uses the correct "partition(X)" parameter. Cheers and have fun Ubuntu-ing. :)

---

