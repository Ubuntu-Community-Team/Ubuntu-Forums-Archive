---
title: "Problem booting in Windows after installing Ubuntu"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by drunkenbrawler on 2009-09-03
I am a regular Windows user and have decided to use Ubuntu as i have heard it is good.

I have two hard-discs. 1 is 80Gb PATA disc and other 1 is 160Gb SATA disc. I have Windows XP- service pack 2 installed on SATA disc which is my secondary boot device (first being my CD-ROM).

I installed Ubuntu 8.10 on my 2nd hard-disc (PATA) and then restarted the computer. At that moment i got an error message saying
"DISC BOOT FAILURE. PLEASE INSERT THE SYSTEM DISC IN TRAY AND TRY AGAIN"
:confused:

After this, i went in the boot menu and tried to boot in Windows but the same error kept on repeating.
I can select to boot in my secondary hard-disc and boot in Ubuntu without (till this moment) any problem.

I am happy with Ubuntu but i need to boot in Windows for using softwares for my academics. 

I have used Windows for long time but i am completely new in Linux world.:(
my system configuration is

Pentium 4 processor, 2.6 GHz,
1.2 Gb RAM, 64 Mb on-board graphics card,
160 Gb SATA hard disc (secondary boot device)
80 Gb PATA hard disc (tertiary boot device)

Any help will be greatly appreciated.

---

### Post by presence1960 on 2009-09-03
Let's get a better look at your setup. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

P.S let me the boot order of your hard disks in BIOS also please!

---

### Post by drunkenbrawler on 2009-09-03
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb067f032

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   312,576,704   271,610,955   5 Extended
/dev/sda5          40,965,813    81,915,434    40,949,622   7 HPFS/NTFS
/dev/sda6          81,915,498   143,347,994    61,432,497   7 HPFS/NTFS
/dev/sda7         143,348,058   204,780,554    61,432,497   7 HPFS/NTFS
/dev/sda8         204,780,618   312,576,704   107,796,087   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe99ee99e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    40,965,749    40,965,687  83 Linux
/dev/sdb2          40,965,750    43,006,004     2,040,255  82 Linux swap / Solaris
/dev/sdb3          43,006,005   156,360,644   113,354,640   5 Extended
/dev/sdb5          43,006,068   156,360,644   113,354,577   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DEC8FE5FC8FE34FD" TYPE="ntfs" 
/dev/sda5: UUID="73632DDA28878AF0" LABEL="Aniket" TYPE="ntfs" 
/dev/sda6: UUID="0F68A3ED1258C95C" LABEL="Miscellaneous" TYPE="ntfs" 
/dev/sda7: UUID="5912239A7117E226" LABEL="Games" TYPE="ntfs" 
/dev/sda8: UUID="623E364F0F7F3902" LABEL="Movies" TYPE="ntfs" 
/dev/sdb1: UUID="313d3f5d-a0e7-4bd0-a389-aca7cdb261dd" TYPE="ext3" 
/dev/sdb2: UUID="26bad766-85ae-4f8a-bc58-145cd7504213" TYPE="swap" 
/dev/sdb5: UUID="63D9E6121E7F91C1" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda6 on /media/Miscellaneous type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/Aniket type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
tmpfs on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=0755)
gvfs-fuse-daemon on /home/aniket/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aniket)


=========================== sdb1/boot/grub/menu.lst: ===========================

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

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=313d3f5d-a0e7-4bd0-a389-aca7cdb261dd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=313d3f5d-a0e7-4bd0-a389-aca7cdb261dd

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

title        Ubuntu 8.10, kernel 2.6.27-14-generic
uuid        313d3f5d-a0e7-4bd0-a389-aca7cdb261dd
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=313d3f5d-a0e7-4bd0-a389-aca7cdb261dd ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid        313d3f5d-a0e7-4bd0-a389-aca7cdb261dd
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=313d3f5d-a0e7-4bd0-a389-aca7cdb261dd ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        313d3f5d-a0e7-4bd0-a389-aca7cdb261dd
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=313d3f5d-a0e7-4bd0-a389-aca7cdb261dd ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        313d3f5d-a0e7-4bd0-a389-aca7cdb261dd
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=313d3f5d-a0e7-4bd0-a389-aca7cdb261dd ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        313d3f5d-a0e7-4bd0-a389-aca7cdb261dd
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=313d3f5d-a0e7-4bd0-a389-aca7cdb261dd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb2
UUID=26bad766-85ae-4f8a-bc58-145cd7504213 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/menu.lst
  17.5GB: boot/grub/stage2
  17.4GB: boot/initrd.img-2.6.27-14-generic
  17.5GB: boot/initrd.img-2.6.27-7-generic
  17.4GB: boot/vmlinuz-2.6.27-14-generic
  17.4GB: boot/vmlinuz-2.6.27-7-generic
  17.4GB: initrd.img
  17.5GB: initrd.img.old
  17.4GB: vmlinuz
  17.4GB: vmlinuz.old

```

---

### Post by presence1960 on 2009-09-03
Boot into Ubuntu, when the desktop loads open a terminal and run this command: ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to this line 
### END DEBIAN AUTOMAGIC KERNELS LIST


and add this under it skipping a line

```
title          Windows XP
rootnoverify   (hd0,0)
chainloader    +1
```

click Save on the toolbar and close the file.
Reboot. Keep your 160 GB disk (sda) first in hard disk boot order in BIOS. This will bring up GRUB when you boot. Select the windows entry and boot into windows

---

### Post by drunkenbrawler on 2009-09-03
I was told to post part of this menu.lst file... it looked like

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
I think there is entry of title Windows. Do i replace it with one you are telling?

---

### Post by drunkenbrawler on 2009-09-03
I'm sorry, but the emoticons appearing at the top are actually ( 8 )
thanks :)

---

### Post by drunkenbrawler on 2009-09-03
I typed the command given in your post and added

title          Windows XP
rootnoverify   (hd0,0)
chainloader    +1
after skipping a line.

After that i restarted and increased the priority of my SATA drive in boot configuration to make it first boot device in hard-discs.

After that i saw message "Grub loading. press ESC to enter boot menu."

As i pressed ESC, i saw familiar boot menu that allowed to select OS to boot in...

I selected Windows XP and i got following message.

> NTLDR missing
Press CTRL+ALT+DELETE to restart
:confused:

there was nothing there except this message on black screen :(

What do i do now?

---

### Post by presence1960 on 2009-09-04
> **drunkenbrawler said:**
> I typed the command given in your post and added

title          Windows XP
rootnoverify   (hd0,0)
chainloader    +1
after skipping a line.

After that i restarted and increased the priority of my SATA drive in boot configuration to make it first boot device in hard-discs.

After that i saw message "Grub loading. press ESC to enter boot menu."

As i pressed ESC, i saw familiar boot menu that allowed to select OS to boot in...

I selected Windows XP and i got following message.


:confused:

there was nothing there except this message on black screen :(

What do i do now?

change the rootnoverify (hd0,0) line to rootnoverify (hd1,0)

It may be because you didn't give me the order of your hard disk booting until after i posted. try this and see what happens. Don't change the order in BIOS because GRUB is coming up at boot!

---

### Post by drunkenbrawler on 2009-09-04
I tried all the variations from hd0,0 to hd0,4 and then i tried hd1,0

for hd0,1 to hd0,4, The message appeared saying 
> Starting up...

but that was all. It hung up there.

For hd1,0, message was

> 
Error 13: Invalid or unsupported execution
Press any key to continue...

after i pressed key, i was redirected to Grub boot menu again

and 1 more thing that might be of importance:
when i boot in Ubuntu it says:

> Booting from hd1,0 ext3 <long string of alphabets and no.s with some "-" icons

---

### Post by presence1960 on 2009-09-04
> **drunkenbrawler said:**
> I tried all the variations from hd0,0 to hd0,4 and then i tried hd1,0

for hd0,1 to hd0,4, The message appeared saying 


but that was all. It hung up there.

For hd1,0, message was



after i pressed key, i was redirected to Grub boot menu again

and 1 more thing that might be of importance:
when i boot in Ubuntu it says:

Ok then (hd1,0) is Ubuntu that means (hd0,0) is XP. You are going to have to put windows bootloader back on the windows disk.

You will need you XP install CD. You will have to change the order of your hard disk booting in BIOS so the windows disk boots first. Then boot the windows install CD and follow [this]("http://ubuntuforums.org/showthread.php?t=1014708") use the instructions for XP.
Reboot and check that windows boots right up. If so then reboot and go into BIOS and make the other disk boot before windows disk. Then try windows from GRUB. Make sure the windows entry is (hd0,0) in menu.lst before you do all the above.

If you don't have a windows install CD but instead you have a recovery partition/recovery CDs/DVDs you can try Super Grub Disk to restore the MBR. 

The last resort would be to unplug your Ubuntu hard disk and reinstall windows.

P.S. when you boot Ubuntu that is telling you the Ubuntu root partition and those string of characters is the UUID for that partition.

---

### Post by presence1960 on 2009-09-04
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
   [COLOR="Red"] Boot files/dirs:[/COLOR]

I did not notice you had no boot files/dir when you posted the output to your script. see red above. So my last post is correct, you need to restore windows bootloader. Hopefully this will turn the trick. If not you may have to replace boot.ini by doing [this]("http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm") For now just restore the bootloader and we'll go from there.

---

### Post by drunkenbrawler on 2009-09-04
Ok. I'll try it now.

actually i was afraid to use fixmbr cause i thought after i use it, i wont be able to boot in Ubuntu as Grub may be removed

but i'll try it now and report in 15 mins. 
thanx :)

---

### Post by drunkenbrawler on 2009-09-04
After i did

fixboot
fixmbr
exit

i tried to boot but if i keep the first hard disc as u told, it again says

> DISC BOOT FAILURE. PLEASE INSERT THE SYSTEM DISC IN TRAY AND TRY AGAIN

if i change the hard disc boot priority it says
> 
NTLDR missing
Press CTRL+ALT+DELETE to restart 

I'm using live cd now cause i can't boot in either operating systems.
I'm trying the 2nd method you posted

---

### Post by drunkenbrawler on 2009-09-04
I tried the second method just now.

I did everything as per procedure given.
I did the followinf steps
```

Select the windows installation:1
Enter administrator password:  (I dont have any :p)
bootcfg /rebuild
```

It detected an installation on my C: and asked me something like

```
Add installation to boot list? (Yes/No/All). y
Enter Load Identifier:.Windows XP professional
Enter OS Load options: /fastdetect
```[I]

A[/I]fter that i got following message:

> ERROR: Failed to add selected boot entry to boot list

:( what to do now?

---

