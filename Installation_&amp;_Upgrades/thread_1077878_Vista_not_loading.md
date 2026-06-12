---
title: "Vista not loading"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by tsouts on 2009-02-22
Hi everyone,

I've installed Ubuntu on my PC that already had Vista but now I can't login on on Vista. I get an error: Can't load winload.exe. I've searched the forum but couldn't find an answer that could help me. Any idea anyone?

If you need results from cat /boot/grub/menu.lst & sudo fdisk -l please see below.

Thank you :)

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
# kopt=root=UUID=1c7b54bb-269e-46bb-96c1-016d9139006c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1c7b54bb-269e-46bb-96c1-016d9139006c

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		1c7b54bb-269e-46bb-96c1-016d9139006c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1c7b54bb-269e-46bb-96c1-016d9139006c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		1c7b54bb-269e-46bb-96c1-016d9139006c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=1c7b54bb-269e-46bb-96c1-016d9139006c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1c7b54bb-269e-46bb-96c1-016d9139006c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1c7b54bb-269e-46bb-96c1-016d9139006c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1c7b54bb-269e-46bb-96c1-016d9139006c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1c7b54bb-269e-46bb-96c1-016d9139006c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1c7b54bb-269e-46bb-96c1-016d9139006c
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

------------------------------------------------------------------

Disk /dev/sda: 160.0 GB, 160041885696 bytes
162 heads, 23 sectors/track, 83892 cylinders
Units = cylinders of 3726 * 512 = 1907712 bytes
Disk identifier: 0xa35e266f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       56958   106110891    7  HPFS/NTFS
/dev/sda2           56959       60532     6658362   83  Linux
/dev/sda3           60533       82518    40959918   83  Linux
/dev/sda4           82519       83892     2559762   82  Linux swap / Solaris

```

---

### Post by caljohnsmith on 2009-02-22
Your Grub entry for booting Vista looks fine, so I think your problem is a Vista problem and not a Grub problem at this point. How about posting the output of:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt /mnt/[Ww][Ii][Nn][Dd][Oo][Ww][Ss]/[Ss]ystem32/winload.exe
```
And we can work from there.

---

### Post by monkeybritt on 2009-02-22
go to isohunt or something and dowmload an install iso for vista. burn it to a dvd then boot from it. after checking language on the install screen go to the bottom and click the link to repair your computer if you see the vista partition in the next screen good continue with this if not this wont work. select it and next. choose command prompt from the menu then enter this in this order:
bootrec.exe /fixmbr    hit enter
bootrec.exe /fixboot    hit enter again
bootrec.exe /rebuildbcd  hit enter 
exit         enter

this fix vista startup then reboot you should boot straight into vista if this works continue
boot from you ubuntu live cd
go to terminal 
enter 
sudo grub
root (hd0,0)
setup (hd0)
quit
exit

this will restore grub with the same settings you had before. sadly sometimes (alot of times) vista just sucks and doesnt want to work that is why we have to make those stupid restore disks thank the lord for live cds like knoppix  and ubuntu that give us the oportunity to get our files back before we rewrite everything
hope this helped if not i tried.

---

### Post by caljohnsmith on 2009-02-23
> **monkeybritt said:**
> 
bootrec.exe /fixmbr    hit enter
bootrec.exe /fixboot    hit enter again
bootrec.exe /rebuildbcd  hit enter 
exit         enter

I would not recommend running "bootrec /fixmbr", because that just reinstalls a Windows MBR (Master Boot Record) so you will only be able to boot into Vista, and only if Vista is working by then. There is really no reason to deliberately overwrite Grub with a Windows MBR, and then immediately reinstall Grub afterwards. Also, those Grub commands you gave will not work since Vista is on the first partition sda1; the linux partitions are sda2 and sda3, which are (hd0,1) and (hd0,2) respectively.

---

### Post by monkeybritt on 2009-02-23
i have had it work sometimes i lose vista bootloader and grub will not load it anyway it has worked for me more than once because i cant seem to be happy with vista installs but my wife will not use ubuntu for some reason. just trying to help. also as i posted it might not if winload.exe is bad i would be very interested in knowing how to replace it without being able boot into vista.i was just thinking it mey be possible the mbr was not finding it. i have had  that happen too. sorry to post my inferior ideas.

---

### Post by caljohnsmith on 2009-02-23
> **monkeybritt said:**
> i have had it work sometimes i lose vista bootloader and grub will not load it anyway it has worked for me more than once because i cant seem to be happy with vista installs but my wife will not use ubuntu for some reason. just trying to help. also as i posted it might not if winload.exe is bad i would be very interested in knowing how to replace it without being able boot into vista.i was just thinking it mey be possible the mbr was not finding it. i have had  that happen too. sorry to post my inferior ideas.
I apologize if my previous post seemed too brusque, because I didn't intend it that way. I'm certainly not trying to discourage anyone from sharing their ideas, because I'm no expert at this either. :)

---

### Post by tsouts on 2009-02-23
Hi guys. Thank you for your replies. The result from the terminal is:

```
-rwxrwxrwx 2 root root 988216 2008-07-30 01:12 /mnt/Windows/System32/winload.exe

/mnt:
total 2384161
-rwxrwxrwx 1 root root         24 2006-09-18 22:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-10-26 22:13 Boot
-rwxrwxrwx 1 root root     333203 2008-01-19 07:45 bootmgr
-rwxrwxrwx 1 root root       8192 2008-04-16 18:13 BOOTSECT.BAK
drwxrwxrwx 1 root root          0 2009-02-15 11:40 Config.Msi
-rwxrwxrwx 3 root root         10 2006-09-18 22:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 13:02 Documents and Settings
-rwxrwxrwx 1 root root 1062551552 2009-02-21 21:40 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-07-31 20:05 MSOCache
-rwxrwxrwx 1 root root 1378410496 2009-02-21 21:40 pagefile.sys
drwxrwxrwx 1 root root          0 2008-10-26 22:02 PerfLogs
drwxrwxrwx 1 root root       4096 2009-02-14 17:29 ProgramData
drwxrwxrwx 1 root root      12288 2009-02-14 17:29 Program Files
drwxrwxrwx 1 root root       4096 2008-11-06 20:09 $Recycle.Bin
drwxrwxrwx 1 root root      20480 2009-02-21 22:26 System Volume Information
drwxrwxrwx 1 root root       4096 2008-07-23 00:56 Users
drwxrwxrwx 1 root root      24576 2009-02-15 11:41 Windows

```

I will get tomorrow a copy of Windows Vista and try to see if I can fix them with the 2nd solution.

The only reason I need Vista is a company software that runs only on Windows, and my iphone :( Otherwise I would wipe them off

---

### Post by caljohnsmith on 2009-02-23
It looks like Vista has all its boot files, so that's a good sign. If you need a Vista CD, you can get a legitimate Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). I would recommend booting that, go to the command line, and do:
```

chkdsk /r
bootrec /rebuildbcd
```
Be sure to run the chkdsk command as many times as it takes until it reports no errors. After doing the above commands, try booting Vista from Grub again an let us know how that goes.

---

### Post by tsouts on 2009-02-23
Vista Recovery CD didn't work (No operating system found). Will try Original Vista Installation Disc tomorrow and try to repair

---

### Post by tsouts on 2009-02-24
Hi Guys, I just did a repair from a legitimate Vista installation disc and it worked. Now both OS are working.

Thank you for you help

---

