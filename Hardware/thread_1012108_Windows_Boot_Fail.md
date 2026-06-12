---
title: "Windows Boot Fail"
date: 2008-12-15
forum: Hardware
---

### Post by vancedus on 2008-12-15
Hi,

I recently attempted to boot my Windows XP partition and found it quickly flashes to a blue screen and then returns to my dual boot screen.  The blue screen flashes too quickly to see what it said.  Any help?  Thank you.

---

### Post by vancedus on 2008-12-17
Update:

I found the error code.

Stop: 0x0000007B.  I read that it could be a number of things.  It is related to GRUB? If anyone can help, please do.. thankyou

---

### Post by cdtech on 2008-12-17
Can you post your "/boot/grub/menu.lst"? That could cause the issue.

Thanks......

---

### Post by vancedus on 2008-12-18
Here is the GRUB list, Thank you.

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
# kopt=root=UUID=d8137222-5a3e-4861-a240-837515b49133 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d8137222-5a3e-4861-a240-837515b49133 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d8137222-5a3e-4861-a240-837515b49133 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-3-rt
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=d8137222-5a3e-4861-a240-837515b49133 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-3-rt
quiet

title		Ubuntu 8.10, kernel 2.6.27-3-rt (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-3-rt root=UUID=d8137222-5a3e-4861-a240-837515b49133 ro  single
initrd		/boot/initrd.img-2.6.27-3-rt

title		Ubuntu 8.10, kernel 2.6.24-22-rt
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d8137222-5a3e-4861-a240-837515b49133 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-22-rt
quiet

title		Ubuntu 8.10, kernel 2.6.24-22-rt (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-rt root=UUID=d8137222-5a3e-4861-a240-837515b49133 ro  single
initrd		/boot/initrd.img-2.6.24-22-rt

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
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

---

### Post by caljohnsmith on 2008-12-18
If your Windows is on the first partition of your HDD, then your current Grub entry for it should be fine. Just to check, how about also posting:
```
sudo fdisk -l
```
Do you have your Windows Install CD? I would recommend booting that, go to the "recovery console" and run:
```
chkdsk /r
```
And run chkdsk as many times as it takes until it reports no errors. Then reboot, and if Windows still crashes, I think your best bet would be to next do a "Windows Repair" from the Install CD. That should be enough to at least get Windows booting again, but you will of course have to download all of Windows updates since the time your Install CD was made. How about giving that a shot and let us know how it goes.

---

### Post by vancedus on 2008-12-18
Thanks for the help.  I won't be able to get to my install CD for about a week but I'll have to give it a shot.  Thanks again.  Here is my fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64166416

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15622   125480469    7  HPFS/NTFS
/dev/sda2           15623       24321    69874717+   5  Extended
/dev/sda5           15623       23961    66982986   83  Linux
/dev/sda6           23962       24321     2891668+  82  Linux swap / Solaris

Thanks

---

### Post by caljohnsmith on 2008-12-18
Since you don't have your Windows Install CD handy, you could download and use a Windows Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). That will at least let you run the chkdsk command, but it won't actually do a "Windows Repair" which requires all the original XP system files from the Install CD. Let me know how that goes. :)

---

### Post by vancedus on 2008-12-18
I ran the recovery CD and it told me that it could not find the hard drive and then rebooted. Any suggestions?  Thanks

---

### Post by caljohnsmith on 2008-12-18
> **vancedus said:**
> I ran the recovery CD and it told me that it could not find the hard drive and then rebooted. Any suggestions?  Thanks
Is your drive IDE (PATA) or SATA? If it is SATA, then when you boot the Windows CD, you have to load your SATA drivers from the Windows CD so the Windows CD can deal with the drive. But if the drive is IDE/PATA, then another option is to download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), and then run the chkdsk command from that CD. Just make sure you don't run any Vista commands on your XP install, but "chkdsk" should be just fine. :)

---

### Post by vancedus on 2008-12-18
I came across a XP PRO recovery CD and when I booted it, and it loaded the drivers for SATA, it still told me that Windows XP is not installed on my computer.  I checked my partition in Gparted and everything appeared to be normal. Any other ideas?  Thanks

---

### Post by caljohnsmith on 2008-12-18
How about checking to see if the partition is mountable and readable:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L, not a one. Please post the output of the above commands.

---

### Post by vancedus on 2008-12-18
This was the response to the command.  I have mounted the volume and pulled files from it so I know it is readable.  Thank you.


[sudo] password for vancedus: 
vancedus@Athena:~$ ls -l /mnt
total 2095537
-rwxrwxrwx 1 root root          0 2007-10-31 16:17 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        211 2008-06-19 20:30 boot.ini
-rwxrwxrwx 1 root root          0 2007-10-31 16:17 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-06-19 20:31 Documents and Settings
drwxrwxrwx 1 root root          0 2008-06-23 16:41 Downloads
drwxrwxrwx 1 root root       4096 2007-10-31 17:43 Drivers
drwxrwxrwx 1 root root          0 2007-10-31 16:27 Intel
-rwxrwxrwx 1 root root          0 2007-10-31 16:17 IO.SYS
-rwxrwxrwx 1 root root          0 2007-10-31 16:17 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-06-22 13:32 MSOCache
drwxrwxrwx 1 root root          0 2007-10-31 16:29 MyWorks
-rwxrwxrwx 1 root root      47564 2007-07-27 08:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-06-02 15:12 ntldr
-rwxrwxrwx 1 root root 2145386496 2008-11-15 13:10 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-10-27 18:40 Program Files
drwxrwxrwx 1 root root       4096 2008-06-21 13:24 RECYCLER
-rwxrwxrwx 1 root root       4645 2008-11-14 11:28 rollback.ini
-rwxrwxrwx 2 root root        512 2008-06-21 21:45 ScanSectorLog.dat
drwxrwxrwx 1 root root       4096 2008-06-19 20:30 System Volume Information
drwxrwxrwx 1 root root     102400 2008-11-15 13:11 WINDOWS

---

### Post by caljohnsmith on 2008-12-18
Did that Windows Install CD you used have SP1 included in it? Because if not, that could be the issue; if I remember correctly, without SP1 the Windows CD can't handle a HDD larger than 137 GB. At least your Windows partition is mountable and readable, so that's a good sign; it also looks like everything is presumably there. Sometimes the Windows CD can have problems if the partition table on the HDD is slightly corrupt, and although your previous fdisk results don't show any problems, it would be good to do one more check:
```
sudo sfdisk -luS
sudo parted /dev/sda print
```
And please post the results.

---

### Post by vancedus on 2008-12-18
Here are he resaults from the commands.  Thanks.

vancedus@Athena:~$ sudo sfdisk -luS

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 250962985  250960938   7  HPFS/NTFS
/dev/sda2     250967430 390716864  139749435   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     250967493 384933464  133965972  83  Linux
/dev/sda6     384933528 390716864    5783337  82  Linux swap / Solaris

vancedus@Athena:~$ sudo parted /dev/sda print
Model: ATA ST9200420ASG (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  128GB  128GB   primary   ntfs         boot 
 2      128GB   200GB  71.6GB  extended                    
 5      128GB   197GB  68.6GB  logical   ext3              
 6      197GB   200GB  2961MB  logical   linux-swap        

vancedus@Athena:~$

---

### Post by caljohnsmith on 2008-12-18
It looks to me like your partition table is fine, so I'm not sure what the problem is with the Windows CD not recognizing your HDD. Maybe the SATA drivers the CD used weren't compatible with your SATA drive or something. At least you can access your data in the meantime, sorry I can't offer any more suggestions at the moment. I'll let you know if I can think of anything else to try.

---

