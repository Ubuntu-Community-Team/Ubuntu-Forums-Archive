---
title: "Grub/Dual Boot/NTLDR issues"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by peteyoferic on 2009-02-15
I know this is a common issue, but the answers in the archive tend to be very specific to a person's computer setup.  I'll give you a rundown of my issue.  Did a fresh install of XP-Pro, on a partition which took up half a 40GB drive.  After that install was complete I installed UBUNTU 8.10 on the remaining space on the drive (used the guided/free space option)  At first when I tried to boot up it would go directly to Windows...without the grub menu options.  So I searched forums and found instructions which I can't for the life of me remember...but they were pretty common on the website..and involved changing the HD numbers in Grub...anyway...it worked for bringing up grub and I was in Linux now (yay!) But when I tried to get back to my Windows install...no go, NTLDR is missing error...after the grub menu.  
The files still exist on the Windows partition (boot.ini, NTDETECT.COM and NTLDR etc) I can see them via linux...so its not an issue with that...I'm SURE it's something to do with Grub not looking in the right place for the windows install...I'm not a super computer pro...so any instructions please make them noob friendly.  I noticed in other postings that responders want the results of two commands...so I'll post those here:

fdisk -l

 Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22528fa0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10198    81915403+   7  HPFS/NTFS
/dev/sda2           10199       19929    78164257+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24692468

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2089    16779861    7  HPFS/NTFS
/dev/sdb2            2090        4998    23366542+   5  Extended
/dev/sdb5            2090        4872    22354416   83  Linux
/dev/sdb6            4873        4998     1012063+  82  Linux swap / Solaris

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76bb4d86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+   7  HPFS/NTFS

and Menu.lst:


title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		81db8eee-1a84-43f3-840d-8cc5562ee9db
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=81db8eee-1a84-43f3-840d-8cc5562ee9db ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		81db8eee-1a84-43f3-840d-8cc5562ee9db
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=81db8eee-1a84-43f3-840d-8cc5562ee9db ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		81db8eee-1a84-43f3-840d-8cc5562ee9db
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Please, if it's something to do with reconfiguring GRUB or whatever...can you spell out the commands for me as thoroughly as possible...not trying to be dumb here...just want to use linux :) 

Many thanks!

---

### Post by Pumalite on 2009-02-15
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

### Post by caljohnsmith on 2009-02-15
How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
```
Reboot, and let me know exactly what happens when you choose Windows from Grub. We can work from there if you want.

---

### Post by peteyoferic on 2009-02-15
> **caljohnsmith said:**
> How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Windows entry to:
```
title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
```
Reboot, and let me know exactly what happens when you choose Windows from Grub. We can work from there if you want.

Hi, Ok...did what you asked, and the result was the same NTLDR error after I selected windows in grub (NTLDR is missing press cntrl, alt...etc)...
I did notice that in the menu.lst there are other options underneath where I change root called map (of which there are two lines...one says (hd0) (hd1) and the other is reversed (1 first, then zero)  Do those possibly need to be modified as well?  

I know the windows files are there...windows used to load fine after linux was installed, it was only the grub modification (which allowed me to get into linux) which seemed to lose windows for me.

---

### Post by caljohnsmith on 2009-02-15
I think it would be helpful to get more info about your setup related to booting, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by Pumalite on 2009-02-15
Read the link that I gave you carefully.
(I thought there was a post with your thanks. I must be dreaming)

---

### Post by peteyoferic on 2009-02-15
> **Pumalite said:**
> Read the link that I gave you carefully.
(I thought there was a post with your thanks. I must be dreaming)

Hello pumalite, sorry I didn't respond to your earlier post...it appears that that link is only fixing issues if you're missing the Windows boot files (which I can see are in the correct place in the windows partition) or if XP is installed on an extended partition...which it is not, it's on a primary partition.  Correct me if I'm wrong but this seems to be a different problem...or is it more the testdisk portion of the link you think might work?

---

### Post by peteyoferic on 2009-02-15
> **caljohnsmith said:**
> I think it would be helpful to get more info about your setup related to booting, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

Hello and thanks, here's the results of the boot_info_script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22528fa0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,830,869   163,830,807   7 HPFS/NTFS
/dev/sda2         163,830,870   320,159,384   156,328,515   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x24692468

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    33,559,784    33,559,722   7 HPFS/NTFS
/dev/sdb2          33,559,785    80,292,869    46,733,085   5 Extended
/dev/sdb5          33,559,848    78,268,679    44,708,832  83 Linux
/dev/sdb6          78,268,743    80,292,869     2,024,127  82 Linux swap / Solaris


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x76bb4d86

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   160,071,659   160,071,597   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="48ECCC7AECCC63B2" LABEL="VideoDrive1" TYPE="ntfs" 
/dev/sda2: UUID="B0E84BF3E84BB67E" LABEL="VideoDrive2" TYPE="ntfs" 
/dev/sdb1: UUID="8408F26E08F25E9C" TYPE="ntfs" 
/dev/sdb5: UUID="81db8eee-1a84-43f3-840d-8cc5562ee9db" TYPE="ext3" 
/dev/sdb6: UUID="cb93898e-bc8d-4a67-acab-a984d61dacf4" TYPE="swap" 
/dev/sdc1: UUID="D6BC44BBBC44983F" LABEL="MediaDrive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=81db8eee-1a84-43f3-840d-8cc5562ee9db ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=81db8eee-1a84-43f3-840d-8cc5562ee9db

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
uuid		81db8eee-1a84-43f3-840d-8cc5562ee9db
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=81db8eee-1a84-43f3-840d-8cc5562ee9db ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		81db8eee-1a84-43f3-840d-8cc5562ee9db
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=81db8eee-1a84-43f3-840d-8cc5562ee9db ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		81db8eee-1a84-43f3-840d-8cc5562ee9db
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=81db8eee-1a84-43f3-840d-8cc5562ee9db /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=cb93898e-bc8d-4a67-acab-a984d61dacf4 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  26.9GB: boot/grub/menu.lst
  26.8GB: boot/grub/stage2
  26.9GB: boot/initrd.img-2.6.27-7-generic
  26.9GB: boot/vmlinuz-2.6.27-7-generic
  26.9GB: initrd.img
  26.9GB: vmlinuz
```

Thanks again...you know looking at this something that strikes me as wrong is that windows is not on sdc...or at least it shouldn't be from what I understand...it's on sdb along with linux (only in 1 not 4 like linux)...

---

### Post by Pumalite on 2009-02-15
meierfra gives you several options. Use the one that works for you.

---

### Post by caljohnsmith on 2009-02-15
OK, how about first doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
That will restore a Windows MBR to your sda drive, because that drive does not have Ubuntu on it. Next make sure to use the previous entry I gave for Windows:
```
title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
```
In other words, **do not include the mapping lines**. Next reboot, make sure your BIOS is set to boot the sdb Ubuntu drive, and let me know exactly what happens when you try to boot Windows from Grub. We can work from there.

---

### Post by peteyoferic on 2009-02-15
> **caljohnsmith said:**
> OK, how about first doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
That will restore a Windows MBR to your sda drive, because that drive does not have Ubuntu on it. Next make sure to use the previous entry I gave for Windows:
```
title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
```
In other words, **do not include the mapping lines**. Next reboot, make sure your BIOS is set to boot the sdb Ubuntu drive, and let me know exactly what happens when you try to boot Windows from Grub. We can work from there.

OK that all makes sense to me as far as the procedure, the only thing I wanted to point out is that sda doesn't have windows installed on it, it's a 160GB drive with nothing but media and stuff on it...do you still want me to run the install of lilo onto sda and switch the first boot to that drive?...there are no OS's 
on it.  If so I'll try that right away and let you know the result.

---

### Post by peteyoferic on 2009-02-15
> **Pumalite said:**
> meierfra gives you several options. Use the one that works for you.

OK thanks, I'll give the testdisk thing a go if this other line of attempted fixes doesn't work.

---

### Post by caljohnsmith on 2009-02-15
> **peteyoferic said:**
> OK that all makes sense to me as far as the procedure, the only thing I wanted to point out is that sda doesn't have windows installed on it, it's a 160GB drive with nothing but media and stuff on it...do you still want me to run the install of lilo onto sda and switch the first boot to that drive?...there are no OS's 
on it.  If so I'll try that right away and let you know the result.
Yes, please go ahead and run the lilo commands; even though your sda drive doesn't have any OSes, it currently has Grub installed to its MBR. Thus it will make troubleshooting a lot simpler if Grub is not also installed to that drive; that way if you get the Grub menu on start up, we will know for sure you are booting from your Ubuntu/Windows drive.

---

### Post by peteyoferic on 2009-02-15
> **caljohnsmith said:**
> Yes, please go ahead and run the lilo commands; even though your sda drive doesn't have any OSes, it currently has Grub installed to its MBR. Thus it will make troubleshooting a lot simpler if Grub is not also installed to that drive; that way if you get the Grub menu on start up, we will know for sure you are booting from your Ubuntu/Windows drive.

Success!  Thanks, I did the lilo install, and the mbr restore...and altered the menu.lst to remove the mapping (and a couple of other lines which were not in your suggested version...they were regarding making active etc)  Anyway...the boot order was already correct...so it was one of the other things that did it...all good, thanks so much for your help...great forum, great OS :)

---

### Post by caljohnsmith on 2009-02-15
I'm really glad to hear that worked OK; cheers and enjoy Ubuntu and Windows. :)

---

