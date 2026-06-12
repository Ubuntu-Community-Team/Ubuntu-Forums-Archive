---
title: "[SOLVED] Both Ubuntu and Windows fail to boot after bsod"
date: 2008-11-28
forum: General Help
---

### Post by ColdFFF on 2008-11-28
I have a dual boot system running both Ubuntu and Windows XP on separate drives, both of which were working fine until last night.

After booting into xp, and attempting to log in, I came across the lovely blue screen of death forcing me to reboot. I selected windows from my grub menu, and was instantly presented with a message telling me ntldr is missing or corrupt. This was remedied by using the recovery console on my xp disc to copy a fresh ntldr file back into place, but after trying again to reboot, I am told the boot.ini is pointing to the wrong drive, followed by a missing or corrupt hal.dll file.

Trying to boot into Ubuntu has also given me no joy. The Ubuntu loading screen comes up (with the orange load bar), and then I am presented with a terminal like screen (no cursor to run a command), with an unreadable error message spanning 4 lines, which repeats itself every 10 seconds or so. I will try to get the full text of this error later tonight.

I have followed a couple of guides relating to the missing hal.dll file, which included using fixmbr, fixboot, bootcfg /rebuild and expanding hal.dl_ from recovery console. fixmbr and fixboot ran successfully, but made no difference to trying to boot into windows.bootcfg /rebuild fails to find a windows installation, and recommends running chkdsk. expand hal.dl_ fails to work as well. The next step in the guides I have found is to do a repair install of xp.

I'm beginning to think that perhaps the windows drive is damaged, but then why would that affect the Ubuntu drive? Or is it just very bad luck that I get problems on both at the same time?

For reference, I have 4 hard drives in total, booting from the Ubuntu drive first to load the grub menu. I have tried booting directly from my windows drive as well, but receive the same issues. I am load the Ubuntu live cd and access files on all drives. I "run" Windows XP pro and Ubuntu 8.10, both of which were reasonably up to date.

Is there anything I have overlooked? Again, I will try to get the full error message when booting ubuntu later tonight.

Thanks in advance

---

### Post by geirha on 2008-11-28
Does your /boot/grub/menu.lst and /etc/fstab have all filesystems listed by UUID? Which fstab entries are set to have filesystem check during boot?

Just the two first things that pop into mind when reading your problems. 

If the drive is damaged, it might not get loaded during ubuntu's boot, and that might shift some of the device names for the other harddrives, which in turn will try to mount the wrong filesystems if you don't use UUIDs in menu.lst and fstab.

And if the windows filesystems are set to be checked during boot, I'm guessing it might halt on the possibly broken hard drive.

---

### Post by TeXtonyx on 2008-11-28
"I'm beginning to think that perhaps the windows drive is damaged, 
but then why would that affect the Ubuntu drive? Or is it just 
very bad luck that I get problems on both at the same time?"

What bootloader is installed in the MBR of the Windows drive?
Can it boot standalone if you change the bios drive boot order,
or did it? Super Grub Disk, I use the run with help option, lets
you boot any drive that has an OS. If they work, it eliminates bad
memory which would affect all the drives. Run a disk diagnostic
on the Windows drive. Instead of verbal descriptions, there is
more clarity in posting the result of  sudo fdisk -l

I think there is another option, run chkdsk /r /f from the XP boot 
disk. A backup is hand in case something goes wrong. There is a
non-destructive Windows reinstall which put Windows in C:\Windows.000
You won't lose data except for My Documents but most of your
applications will need to be reinstalled. Of course that won't
work if the drive itself is bad. So I think you should try to boot
XP from Super Grub Disk first. If XP boots, then it's not the drive,
though the BSOD indicates a bad drive much more so than hal.dll errors.

---

### Post by ColdFFF on 2008-11-30
Apologies for the lateness of my reply.



After running Super Grub Disk (and finding it failed to boot any os), I decided to try booting Ubuntu as normal to copy the error I was receiving. Naturally no error occurred and Ubuntu booted fine. Fortunately this is more than enough to keep me happy and working, however the girlfriend will kill me if she cant use windows to play The Sims and Spore :/



Anyway, here is the result of fdisk -l

> Apologies for the lateness of my reply.



After running Super Grub Disk (and finding it failed to boot any os), I decided to try booting Ubuntu as normal to copy the error I was receiving. Naturally no error occurred and Ubuntu booted fine. Fortunately this is more than enough to keep me happy and working, however the girlfriend will kill me if she cant use windows to play The Sims and Spore :/



Anyway, here is the result of fdisk -l

Quote:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38aa8519

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30401 244196001 42 SFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce98ce98

Device Boot Start End Blocks Id System
/dev/sdb1 1 13995 112414806 83 Linux
/dev/sdb2 13996 14593 4803435 5 Extended
/dev/sdb5 13996 14593 4803403+ 82 Linux swap / Solaris

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
16 heads, 63 sectors/track, 159560 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x15131512

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 159559 80417704+ 7 HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38aa8518

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 30400 244187968+ 7 HPFS/NTFS 

A particular point Ive noted is that the drives seem to have been given different names. For example, I am sure /dev/sdc (the Windows drive) was originally /sdb. I may be wrong of course, but is it possible for the drives to be reassigned like that? And if so, could this be causing the grub bootloader to look at the wrong drive for windows and stop it booting?

---

### Post by geirha on 2008-11-30
> **ColdFFF said:**
> 
A particular point Ive noted is that the drives seem to have been given different names. For example, I am sure /dev/sdc (the Windows drive) was originally /sdb. I may be wrong of course, but is it possible for the drives to be reassigned like that? And if so, could this be causing the grub bootloader to look at the wrong drive for windows and stop it booting?

Yes, they may get reassigned like that. Usually it happens if you add or remove a drive, or if you plug a drive into a different port. What's the content of /boot/grub/menu.lst?

One thing you should try is to select windows from the grub menu, but not hit enter. Instead, hit **e** to edit it, select the root (or rootnoverify) line and hit **e** again, then change hdX,Y to something else, then hit **b** to attempt to boot with this temporary change. Since windows is on the first partition, Y should be 0, and X can be any of 0,1,2,3 (since you have 4 drives). Once you find the correct value, boot ubuntu and make the change permanent in /boot/grub/menu.lst.

---

### Post by TeXtonyx on 2008-11-30
You said that Super Grub Disk failed to boot any OS, but that 
Ubuntu apparently booted after that. All your OS but sdb1 are
marked with an * which means they are bootable. Can you change
your boot order in bios and try booting sdc1 and sdd1 directly,
the Windows drives? The drives are hd0, hd1, hd2 and hd3 in bios
I would imagine. So you would try hd2 first and then hd3 in bios.

My reasoning, perhaps in error, is that if the drives won't boot
directly from bios when active, then they won't boot from the
grub menu.lst either. The XP error message is more revealing since
I've had Windows not boot from the menu.lst but boot directly, which
[but give false hal.dll errors from the menu.lst attempt]
then pinpoints the error to wrong menu.lst entries. One might expect 
that sdc1 might not boot because of the bsod, but not both, sdd1 also.  
Also are your SFS and ntfs-sdd drives very nearly the same physical 
size, they are reported as such? I never trust coincidences, ;-)

---

### Post by pcjunkie on 2008-11-30
Hope this helps

[device map]

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

```

[grub]


```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=68666dd9-ba92-4bff-a34e-bf3b33529f7e ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=68666dd9-ba92-4bff-a34e-bf3b33529f7e ro single
initrd		/boot/initrd.img-2.6.24-22-generic


```

### END DEBIAN AUTOMAGIC KERNELS LIST

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Professional x64 Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Recent working Kernel backup:
root



title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=68666dd9-ba92-4bff-a34e-bf3b33529f7e ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet


title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=68666dd9-ba92-4bff-a34e-bf3b33529f7e ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=68666dd9-ba92-4bff-a34e-bf3b33529f7e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386
quiet


```

---

### Post by ColdFFF on 2008-12-01
More progress :) I am now past the stage where hal.dll is missing (although not yet a fully working install of windows). It turns out that the bios boot order had altered itself after the bsod (apparently this is a feature?), and now all boot options work. Windows still fails to boot, as it hangs on the loading splash screen.

Still, this further than before, and I'm on to the next step to resolving my problems.

> **TeXtonyx said:**
> Also are your SFS and ntfs-sdd drives very nearly the same physical size, they are reported as such? I never trust coincidences, ;-)

Infact they are supposed to be exactly the same size, both 250gb Seagate drives with the same model number, but of course one was formatted by the windows installer a long time ago and it hasn't used up all the available space for the partition - I think its left 8mb unused.

---

### Post by caljohnsmith on 2008-12-01
Does Windows hang when you boot its drive directly on start up, or when you boot Windows from the Grub menu? If it is the latter case, how about posting your Grub's menu.lst:
```
cat /boot/grub/menu.lst
```
And we can check to make sure your Windows entry is correct.

---

### Post by ColdFFF on 2008-12-01
Both from grub and directly. Just in case:

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
timeout		5

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

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
# kopt=root=UUID=f9ecd2bf-7a1e-4749-8b0d-5c765da41c8f ro

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
# defoptions=quiet splash vga=771

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
title 		Ubuntu 8.10
root 		(hd0,0)
kernel 		/boot/vmlinuz-2.6.27-7-generic root=UUID=f9ecd2bf-7a1e-4749-8b0d-5c765da41c8f ro quiet splash
initrd 		/boot/initrd.img-2.6.27-7-generic
quiet


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Alternate Ubuntu starts:
root

title 		Ubuntu 8.10 (recovery mode)
root 		(hd0,0)
kernel 		/boot/vmlinuz-2.6.27-7-generic root=UUID=f9ecd2bf-7a1e-4749-8b0d-5c765da41c8f ro single
initrd 		/boot/initrd.img-2.6.27-7-generic

title 		Ubuntu 8.10, memtest86+
root 		(hd0,0)
kernel 		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by caljohnsmith on 2008-12-01
Have you run "chkdsk" on Windows yet? You mentioned chkdsk in your first post, but I don't think you mentioned if you actually ran it or not. If not, I would try:
```
chkdsk /r
```
And run it as many times as necessary until it reports no errors. And since you mentioned in post #4 that Windows is on sdc, please also post:
```
sudo mount /dev/sdc1 /mnt
ls -l /mnt
cat /mnt/boot.ini

```
Note "-l" is a lowercase L, not a one.

---

### Post by ColdFFF on 2008-12-01
Since I reset the boot order (stopping further hal.dll messages), the windows drive is now actually sdd1. Thus:

```
coldfff@coldfff-desktop:~$ sudo mount /dev/sdd1 /mnt
coldfff@coldfff-desktop:~$ ls -l /mnt
total 617
-rwxrwxrwx 1 root root      0 2007-10-31 14:49 AUTOEXEC.BAT
drwxrwxrwx 1 root root   4096 2008-10-07 00:06 $AVG8.VAULT$
-rwxrwxrwx 1 root root   3678 2008-11-28 14:37 bootex.log
-rwxrwxrwx 1 root root    223 2008-12-01 14:45 boot.ini
-rwxrwxrwx 1 root root    366 2008-12-01 14:17 boot.ini~
-rwxrwxrwx 1 root root      0 2007-10-31 14:49 CONFIG.SYS
drwxrwxrwx 1 root root      0 2008-02-05 11:01 CUDA
drwxrwxrwx 1 root root   4096 2008-08-01 12:29 Documents and Settings
drwxrwxrwx 1 root root 135168 2008-11-17 23:11 Downloads
-rwxrwxrwx 1 root root  13824 2008-08-24 12:17 dvb.GRF
drwxrwxrwx 1 root root   4096 2008-10-05 14:44 eclipse
drwxrwxrwx 1 root root      0 2007-11-01 09:39 EPSON
-rwxrwxrwx 1 root root      0 2007-10-31 14:49 IO.SYS
-rwxrwxrwx 1 root root      0 2007-10-31 14:49 MSDOS.SYS
-rwxrwxrwx 1 root root  47564 2004-08-04 13:00 NTDETECT.COM
-rwxrwxrwx 1 root root 250048 2008-05-12 13:45 ntldr
drwxrwxrwx 1 root root      0 2007-10-31 15:33 NVIDIA
drwxrwxrwx 1 root root      0 2008-06-17 18:06 ProgramData
drwxrwxrwx 1 root root  36864 2008-11-24 22:49 Program Files
drwxrwxrwx 1 root root      0 2007-11-01 09:42 RECYCLER
drwxrwxrwx 1 root root   4096 2008-10-06 22:34 System Volume Information
drwxrwxrwx 1 root root      0 2008-11-13 19:55 Temp
drwxrwxrwx 1 root root 118784 2008-11-24 10:56 WINDOWS
coldfff@coldfff-desktop:~$ cat /mnt/boot.ini
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

```

I'll continue to run chkdsk /r as well. I think the last run through didn't report any errors, but I'll run again to double check.

---

### Post by ColdFFF on 2008-12-01
Confirmed chkdsk /r does not report errors. Rebooting back into Ubuntu now, and the windows drive has switched back to sdc from sdd :confused:

---

### Post by caljohnsmith on 2008-12-01
> **ColdFFF said:**
> Confirmed chkdsk /r does not report errors. Rebooting back into Ubuntu now, and the windows drive has switched back to sdc from sdd :confused:
The fact that the Windows drive is sometimes labeled sdc and other times sdd makes me think you might have an issue with how the Windows drive is configured in your BIOS. You might want to check your BIOS to see what settings you have related to that HDD; look for settings like "auto-detect", LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Try changing them one at a time and see if it helps, and I would recommend writing down whichever settings you change so you can revert back if necessary.

I'm also thinking you might have some sort of hardware issue at this point, so if I were in your shoes, I would run some HDD diagnostic tests on your Windows drive to check its health. If you want to do that from Ubuntu, just do:
```
sudo apt-get install smartmontools
```
Then do the following to save the current health status parameters of your HDD to a file on your desktop (be sure to change "sdc" to "sdd" if necessary in all the following commands):
```
sudo smartctl -a /dev/sdc > ~/Desktop/Windows_drive_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sdc
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sdc | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sdc > ~/Desktop/Windows_drive_health_after_test.txt
sudo smartctl -H /dev/sdc
```
And please post the two files from your desktop to your next message so I can take a look at the results. :)

---

### Post by TeXtonyx on 2008-12-01
----------------------------------


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

--------------------------------

This says "on /dev/sdc1" but hd1 = sdb not sdc.
So I think later you said Windows was on sdd
which means these settings aren't right.

But you also said I think, that you had two bootable XP
partitions, so you need two of these entries between the
dotted lines above, one for each Windows OS, and the
settings will be a little different and its easier if you
have two different titles, like XP Pro and XP Professional. 

The segment between the dotted lines is set to boot sdb
which I think was the bsod Windows partition which explains
why it doesn't work because Windows is broken. 

After you try other suggested measures, I think a Repair
install is in order. Try the first Repair option which lets
you Fixboot, Fixmbr, and bootcfg/rebuild in that order. Then 
there is a second Repair option later, with the XP install cd.
Sometimes bsod means bad sectors on the drive if you find
your system unable to complete the Repair installation later.

---

### Post by caljohnsmith on 2008-12-01
> **TeXtonyx said:**
> 
This says "on /dev/sdc1" but hd1 = sdb not sdc.
So I think later you said Windows was on sdd
which means these settings aren't right.

Just a small thing, but I think you might be forgetting that Grub sees the order of drives on start up as the same as the BIOS boot order, not the same as how the drives are ordered in /dev once you boot into Ubuntu. :) In other words, on start up, (hd1) is simply the second drive in the BIOS boot order, and that could be any of his drives depending on how he has his BIOS set. But if we assume he only has one Windows installation, and if using (hd1) boots Windows, then (hd1) would be his Windows drive regardless of whether the Windows drive is sdc or sdd in Ubuntu. I think you might be forgetting post #17 from this thread:

[http://ubuntuforums.org/showthread.php?p=6197790](http://ubuntuforums.org/showthread.php?p=6197790)

---

### Post by ColdFFF on 2008-12-01
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

Before
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3250820A
Serial Number:    9QE0RD70
Firmware Version: 3.AAE
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec  1 18:01:37 2008 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (  24)	The self-test routine was aborted by
					the host.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   085   006    Pre-fail  Always       -       60722275
  3 Spin_Up_Time            0x0003   097   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       894
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   052   045   030    Pre-fail  Always       -       4123359744371
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4505
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       956
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   054   050   045    Old_age   Always       -       46 (Lifetime Min/Max 35/48)
194 Temperature_Celsius     0x0022   046   050   000    Old_age   Always       -       46 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   070   060   000    Old_age   Always       -       99180625
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               80%      4505         -
# 2  Extended offline    Aborted by host               90%      4505         -
# 3  Extended offline    Aborted by host               80%      4505         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

After
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10 family
Device Model:     ST3250820A
Serial Number:    9QE0RD70
Firmware Version: 3.AAE
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec  1 19:16:22 2008 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   085   006    Pre-fail  Always       -       60722275
  3 Spin_Up_Time            0x0003   097   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       894
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   052   045   030    Pre-fail  Always       -       4123360143526
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4507
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       956
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   054   050   045    Old_age   Always       -       46 (Lifetime Min/Max 35/48)
194 Temperature_Celsius     0x0022   046   050   000    Old_age   Always       -       46 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   068   060   000    Old_age   Always       -       96474667
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      4507         -
# 2  Extended offline    Aborted by host               80%      4505         -
# 3  Extended offline    Aborted by host               90%      4505         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

I have yet to have a mess around with changing bios settings, but I'll have a go at that next.

Just for clarification, I have only 1 Windows install. Changing the menu.lst so it looks for windows on another hd is what was causing the hal.dll error. When it looks on hd1 it will load to the splash screen before it freezes out.

---

### Post by caljohnsmith on 2008-12-01
That's good news, based on those SMART test results, it looks like your HDD is healthy. I guess I would try your BIOS settings next like you mentioned, and if that doesn't work, I think your next best option would probably be doing a "Windows Repair" from the Windows Install CD. Good luck and let me know how it goes though.

---

### Post by TeXtonyx on 2008-12-01
> **ColdFFF said:**
> [CODE]
Just for clarification, I have only 1 Windows install. Changing the menu.lst so it looks for windows on another hd is what was causing the hal.dll error. When it looks on hd1 it will load to the splash screen before it freezes out.

-----------------------------------------

I thought you had two ntfs or Windows install because of fdisk,
-------------------------
Device Boot Start End Blocks Id System
/dev/sdc1 * 1 159559 80417704+ 7 HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38aa8518

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 30400 244187968+ 7 HPFS/NTFS
------------------------------

It says that you have ntfs on sdc1 and sdd1 taken from post #4
Well, no matter, it will all come out in the wash.

---

### Post by ColdFFF on 2008-12-01
I have both Ubuntu and Windows working (in a fashion) now. Thanks in particular to TeXtonyx and caljohnsmith for the sheer amount of effort put in to helping me, especially when most of the issues were with Windows, and thanks to everyone else who chimed in with their support.

> **TeXtonyx said:**
> 
I thought you had two ntfs or Windows install because of fdisk,
-------------------------
Device Boot Start End Blocks Id System
/dev/sdc1 * 1 159559 80417704+ 7 HPFS/NTFS
...
Device Boot Start End Blocks Id System
/dev/sdd1 * 1 30400 244187968+ 7 HPFS/NTFS

Yeah, I cant explain that one either. I guess both drives are bootable giving the impression both had an OS on.

---

