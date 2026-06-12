---
title: "[SOLVED] XP does not boot after install"
date: 2008-11-21
forum: General Help
---

### Post by deadgeese on 2008-11-21
I just intalled Ubuntu for the first time on my computer. Install worked great and I can access my NTFS windows partition just fine while running U. However, when I click on the XP boot option from the grub menu the screen blanks and "starting" appears in the top left hand corner...... then, nothing more. YIKES! It takes ctrl+alt+del to escape.

I did a little searching on this but couldn't find a solution. The related topics indicated the results of fdisk -l and the contents of menu.lst were necessary to examine. When I run fdisk -l in the terminal the result is:

Cannot open /dev/sda

The contents of menu.lst is as follows:

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
# kopt=root=UUID=6037b76a-efdd-4e08-92c2-38892683efd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6037b76a-efdd-4e08-92c2-38892683efd1

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
uuid		6037b76a-efdd-4e08-92c2-38892683efd1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6037b76a-efdd-4e08-92c2-38892683efd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6037b76a-efdd-4e08-92c2-38892683efd1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6037b76a-efdd-4e08-92c2-38892683efd1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6037b76a-efdd-4e08-92c2-38892683efd1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


END OF MENU.LST


Can anyone here help me with this?

Thanks in advance,

DG

---

### Post by caljohnsmith on 2008-11-21
First, you need to run "fdisk" as root, so you should use:
```
sudo fdisk -l
```
I'm guessing you got the "Cannot open /dev/sda" error because you didn't use sudo. If the above output shows Windows is sda1, then your entry for Windows in your Grub's menu.lst is OK. I suspect your problem is that your Windows partition boot sector is partially corrupted, because that sometimes happens after doing repartitioning to set up a dual boot. 

To see if that's the issue, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal), make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows from Grub. We can go from there. :)

---

### Post by deadgeese on 2008-11-21
Wow! I mean WOW!  You nailed both the problem and solution in one try, Cal. Your instructions were crystal clear..... I just followed them 1,2,3 and Kazaam! XP is back! But, only so my wife can enjoy her Solitaire. I'm marking this thing SOLVED! I hope it can help others. Thanks, man. Somehow that doesn't seem like enough though.

DG

---

### Post by caljohnsmith on 2008-11-21
I'm really glad that fixed the problem, so hopefully now your marital harmony has been restored to its fullest. Anyway, cheers and have fun with Ubuntu. :biggrin:

:popcorn:

---

### Post by Engus on 2008-11-22
> **caljohnsmith said:**
> First, you need to run "fdisk" as root, so you should use:
```
sudo fdisk -l
```
I'm guessing you got the "Cannot open /dev/sda" error because you didn't use sudo. If the above output shows Windows is sda1, then your entry for Windows in your Grub's menu.lst is OK. I suspect your problem is that your Windows partition boot sector is partially corrupted, because that sometimes happens after doing repartitioning to set up a dual boot. 

To see if that's the issue, how booting your Live CD, open a terminal (Applications > Accessories > Terminal), make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an warning that the "sectors are not identical", then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know exactly what happens when you boot Windows from Grub. We can go from there. :)

I am currently in testdisk on my laptop as I had a similar problem (except vista)  Im just wondering what do i do after choosing "rebuild bs" if the sectors are identical?

---

### Post by caljohnsmith on 2008-11-22
> **Engus said:**
> I am currently in testdisk on my laptop as I had a similar problem (except vista)  Im just wondering what do i do after choosing "rebuild bs" if the sectors are identical?
If the sectors are identical, then that means it won't make any difference to replace the current boot sector with the backup one, so testdisk doesn't give you that option. How about first posting:
```
sudo fdisk -lu
```
And what exactly happens when you try and boot Vista from the Grub menu? Does your hang too on "Starting up...", or do you get further? Any error messages?

---

### Post by Engus on 2008-11-22
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5e253d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   601393274   300696606   83  Linux
/dev/sda2       601393275   625137344    11872035    5  Extended
/dev/sda5       601393338   625137344    11872003+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe7073273

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   207865034   103932486    7  HPFS/NTFS
/dev/sdb2       207865035   234436544    13285755    7  HPFS/NTFS


A little background:
Its an hp laptop, that had vista factory intalled on a 120gb HDD,  with the 320gb HDD (freshly formated) plugged in externally I installed Ubuntu onto it from a liveCD.   when I would boot I used grub to choose ubuntu or vista.  then I switched the HD's around so the 320 was internal, and 120 was external.  I had to reinstall grub so that I could boot ubuntu without the vista HD attached.  but now vista doesnt boot.

Vista is still in grub, and when chosen I always get prompted to either start normally or run start-up recovery.  start-up recovery doesnt show vista and tells me to find the drivers (automatically sending me to and X:drive) all the normal windows files are there though.  If i choose to start-up normally,  it starts to load (statusbar) but then i get a blue error screen (lots of writing, but goes away too quickly to read it) then automatically restarts.   back to grub.

---

### Post by caljohnsmith on 2008-11-22
I'm not sure what entry you are using for Vista in your menu.lst, but how about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your current Vista entry with:
```
title Windows Vista
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And let me know exactly what happens when you try it from the Grub menu.

---

### Post by Engus on 2008-11-22
I have 2 vista entries in menu.lst.  I assume this is because of the recovery partition.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
root		(hd1,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
root		(hd1,1)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-11-22
OK, I see at least part of the problem; you normally have to use Grub's mapping technique to boot Vista from any drive that is not the boot drive, so how about replacing your entries with:
```
title Windows Vista (sdb1)
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title Windows Vista (sdb2)
root (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And then try again; I would think that sdb1 is your recovery partition, so probably the second entry above (sdb2) will hopefully work. Let me know how it goes.

---

### Post by Engus on 2008-11-22
i tried both sda1&2   they both come up with:
starting up...
a disk read error occured

also, is the spacing after "map" or "root" important?

---

### Post by caljohnsmith on 2008-11-22
> **Engus said:**
> 
also, is the spacing after "map" or "root" important?
Fortunately, the spacing doesn't matter. Do you have a Windows Vista Install CD, or do you only have that recovery partition on your HDD? If you don't have a Vista CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), boot that, go to the command line, and do:
```
chkdsk /r C:
chkdsk /r D:
```
And run both of those commands as many times as it takes until they each report no errors. After that, reboot, and let me know how far you get when you try and boot Vista again.

---

### Post by Engus on 2008-11-22
I have the recovery dvd (2 disks)  but when i restart with the first one in the drive it starts loading files then goes into recovery manager and wants to format the drive.

is this because the vista hd isnt the main drive?  would changing the boot order so the external is after cd/dvd but before the notebook hd make a difference?

---

### Post by caljohnsmith on 2008-11-22
It sounds like maybe those DVDs are OEM? If that's true, then they probably won't give you much other choice than a complete reinstall, and that shouldn't be necessary unless we exhaust the other possible fixes. How about downloading that Recovery CD that I linked to in my previous post and using that? Also, changing the boot order in BIOS will unfortunately not help.

---

### Post by Engus on 2008-11-22
i downloaded the recovery cd.  when i boot that it wants to install, and even if i put in the product key it doesnt work  "error 0x80070002"   am i missing a step to get to the command line?

---

### Post by Engus on 2008-11-24
just looking for some help on this,  would it be better to start a different thread?

---

### Post by caljohnsmith on 2008-11-24
From the Vista Recovery CD, after you select "Repair Your Computer" from the first main menu, there should be a menu that gives you the choice of "command prompt". To see some screen shots of what to expect, see this:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Let me know how that goes.

---

### Post by Engus on 2008-11-24
i got to that menu, just rushed to much and didnt see the command prompt option.  :rolleyes:

---

### Post by Engus on 2008-11-24
chkdsk /r C:  went through 5 verifiying steps
chkdsk /r D:  came back with something like, " the filesystem is UDF , and is write protected"     
then i tried both sda1&2 again, and they both come up with:
starting up...
a disk read error occured

I'm considering backing up what i need from the vista hd, and then reinstalling vista.   I'd rather not have to reinstall all my programs and since vista takes a lot longer to install then ubuntu.  but what would be the best way to dual boot install vista on an external and not screw up the main one?

---

### Post by caljohnsmith on 2008-11-25
I think we may be close to getting your Vista to work, so if you're willing to try a few more things, I think that would be a better option than doing a complete reinstall just yet (but of course it's up to you). If that sounds OK, then how about posting the following:
```

sudo mount /dev/sdb1 /mnt
ls -l /mnt
```
Also, when you tried to do the "Rebuild BS" with testdisk, did you choose sdb1 or sdb2? If you are unsure, please try again on sdb1, because it looks like that is your Vista partition. Also, can you set your BIOS to boot the sdb Vista drive on start up? How about trying that and let me know if Vista boots OK. If not, can you disconnect your external 320 GB Ubuntu drive? If you can disconnect the Ubuntu drive, you could then boot up that Vista Recovery CD and do a "[Startup Repair]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")". Let me know how it goes. :)

---

### Post by Engus on 2008-11-25
total 4625079
-rwxrwxrwx 1 root root    2097152 2008-10-24 11:41 7225344.sys
drwxrwxrwx 1 root root       4096 2008-02-08 03:05 boot
-rwxrwxrwx 1 root root     333203 2008-01-20 20:50 bootmgr
-rwxrwxrwx 1 root root        388 2008-03-26 13:54 DCMBRBIN
-rwxrwxrwx 2 root root       1024 2008-11-08 05:03 diskfile1
drwxrwxrwx 1 root root          0 2006-11-02 09:42 Documents and Settings
-rwxrwxrwx 2 root root     415180 2008-10-24 11:47 driverbmp.bin
-rwxrwxrwx 1 root root        512 2008-03-26 13:54 FARSBOOT.BIN
-rwxrwxrwx 1 root root      30972 2008-03-26 13:54 FARSBOOT.BIO
drwxrwxrwx 1 root root          0 2008-07-02 03:14 HP
-rwxrwxrwx 1 root root     196608 2008-10-23 19:15 index.sys
drwxrwxrwx 1 root root          0 2008-09-23 17:31 Intel
-rwxrwxrwx 1 root root        381 2008-07-01 07:44 IPH.PH
-rwxrwxrwx 1 root root        356 2008-07-25 22:26 LGSInst.Log
-rwxrwxrwx 1 root root      15360 2008-11-08 05:03 logicinf.bin
-rwxrwxrwx 1 root root      22183 2008-10-24 13:19 log.log
drwxrwxrwx 1 root root          0 2008-09-05 08:20 McAfeetm
-rwxrwxrwx 1 root root     904704 2006-12-02 00:37 msdia80.dll
drwxrwxrwx 1 root root          0 2008-07-01 08:06 MSOCache
-rwxrwxrwx 1 root root 4606914560 2008-11-08 05:03 pagefile.sys
drwxrwxrwx 1 root root          0 2008-01-20 21:04 PerfLogs
drwxrwxrwx 1 root root       8192 2008-10-15 00:27 ProgramData
drwxrwxrwx 1 root root       8192 2008-10-02 22:47 Program Files
drwxrwxrwx 1 root root      20480 2008-11-04 19:40 Program Files (x86)
drwxrwxrwx 1 root root      28672 2008-11-07 14:35 QUARANTINE
drwxrwxrwx 1 root root       4096 2008-10-27 14:51 $RECYCLE.BIN
-rwxrwxrwx 1 root root        518 2008-10-15 00:20 RHDSetup.log
-rwxrwxrwx 1 root root    5242880 2008-05-08 11:17 spc_init
-rwxrwxrwx 1 root root    4194304 2008-10-22 15:36 spc_kern
-rwxrwxrwx 1 root root  115343360 2008-06-23 17:32 spc_root
drwxrwxrwx 1 root root      16384 2008-10-15 00:16 SWSetup
drwxrwxrwx 1 root root       4096 2008-10-15 00:15 System.sav
drwxrwxrwx 1 root root      20480 2008-11-07 14:43 System Volume Information
-rwxrwxrwx 1 root root          0 2008-10-22 15:36 tasks.ini
drwxrwxrwx 1 root root       4096 2008-11-22 04:42 Temp
-rwxrwxrwx 2 root root        606 2008-10-15 00:14 updatedatfix.log
drwxrwxrwx 1 root root       4096 2008-07-21 12:05 Users
drwxrwxrwx 1 root root      24576 2008-11-05 02:09 Windows
-rwxrwxrwx 1 root root     188547 2008-06-30 10:30 wubildr
-rwxrwxrwx 1 root root       8192 2008-06-30 10:30 wubildr.mbr


I did that and then ran testdisk again.  the first time i ran it (last week) i did it with what i thought was the vista section(its listed first so i assume sbd1) because the second one was labeled"[HP_Recovery]".  this time i did "rebuild bs" with the second one, and the boot sectors werent identical so i ran "write".  I'm gonna restart and see if that helped any before trying the other steps you posted.

---

### Post by Engus on 2008-11-26
I still got the error:
starting up...
a disk read error occured

if i changed BIOS to boot from the external grub still loads. sbd2 gives me a blinking cursor (black screen, nothing happens) and sbd1 shows:
Error 13
invalid or unsupported executable  format

---

### Post by caljohnsmith on 2008-11-26
OK, how about restoring a Windows MBR to your Vista drive, and then see if you can boot the Vista drive directly on start up. Just do the following:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
```
Reboot, try and boot the Vista drive, and let me know exactly what happens. If that doesn't work, can you change the jumper settings on the Vista HDD to maybe "cable-select" and see if that makes a difference? And if that doesn't work, would it be too much trouble to switch the drives again so that the Vista drive is internal (sda), and try booting the Vista drive again? Did you ever have Vista booting when you switched it to be the external drive (I assume not)? Is the current external Vista drive in a USB enclosure, or how is it hooked up?

---

### Post by Engus on 2008-11-26
> **caljohnsmith said:**
> Reboot, try and boot the Vista drive, and let me know exactly what happens.**It started loading vista, but then stopped, showed a blue error screen, but restarted right away so i didnt see what it said** 
If that doesn't work, can you change the jumper settings on the Vista HDD to maybe "cable-select" and see if that makes a difference? **I dont know what that means or how to do it**
And if that doesn't work, would it be too much trouble to switch the drives again so that the Vista drive is internal (sda), and try booting the Vista drive again? **I tried that before asking on here. it didnt work then but we may have changed something so I'll try again**
Did you ever have Vista booting when you switched it to be the external drive (I assume not)? Is the current external Vista drive in a USB enclosure, or how is it hooked up?**I had it working as external before i reinstalled grub onto the ubuntu HD.  Its in a USB connected enclosure  **

and I just want to thank you for how much you've been in here helping me.  seeing how helpful people are on here is a nice addition to how much I like ubuntu.:popcorn:

---

### Post by AndrewS on 2008-12-01
Hi

I have a similar problem, in that after messing around with parted (shrinking partitions mainly) the installing Fedora 10 (which lost me both my Ubuntu installations in grub...) then deleting the F10 partition and re-installing Ubuntu 8.10, I can't use XP.  All I get in grub is an entry for a Windows loader - if I select that, the system crashes.

Re-running gparted, there was a warning against the NTFS partition which caused me to follow the suggestion from caljohnsmith above.  I can now see the NTFS partition label (which I couldn't before) but the warning triangle is still there.  The Information says that NTFS is inconsistent, and to run "chkdsk /f" and re-boot TWICE.  However, I think chkdsk is a Windows program, and I can't boot into Windows...  Can testdisk fix this?

NOTE:  I can also access the files in the NTFS partition in 8.10 if that helps.

Any help much appreciated.

TIA

Andrew

---

