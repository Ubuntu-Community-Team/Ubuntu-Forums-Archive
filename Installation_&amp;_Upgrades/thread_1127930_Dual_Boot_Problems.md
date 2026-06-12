---
title: "Dual Boot Problems"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by tarun.winlin on 2009-04-17
Hi Guys,

I had Ubuntu Hardy running on one partition & WinXP on the other & it was working just fine.

Today, I installed Ubuntu Intrepid on the same partition on which I had Ubuntu Hardy, but now for some reason when I try to boot into Windows, it says HAL.DLL not found or corrupted. It looks somehow I have messed up with the MBR.

Can one of you experts tell me how to get it working back without doing a reinstall of windows.

Thanks.

---

### Post by meierfra. on 2009-04-17
The "hal.dll" error usually  means that "boot.ini" needs to be edited.

But to get clearer picture of your setup, I suggest to boot into  Ubuntu and   download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by Tim Sharitt on 2009-04-17
If you have your Windows XP CD handy, boot it and run the recovery console (unless you can get to a recovery console without it) and Enter 
```
fixboot
```

or possibly
```
fixboot C:
```

Next, you'll need to restore grub with your Ubuntu live CD. Once you have booted the live CD, open a terminal and do the following

Start grub
```
sudo grub
```

Find grub
```
find /boot/grub/stage1
```

With this information, set the root device by filling in X,Y with whatever was returned
```
root (hdX,Y)
```

Install grub
```
setup (hd0)
```

Then quit grub
```
quit
```

Then reboot and try it out. This second installation of grub should not affect Windows again as the partition information has not changed.

---

### Post by zeex on 2009-04-17
Hi tarun, 

HAL.DLL is corrupt/not found could be due to many reasons but i'm assumoing here that your MBR is messed up so here is what you can do.

1) Boot from XP CD and go to recovery console.
2) At the command prompt type **fixmbr**

This action will modify the MBR so that you could use windows again but you can't use ubuntu anymore. so now you need to install grub.

1) boot from ubuntu live CD (installed version and live CD version should be same (not necessary though))
2) Open the terminal and type these commands

$* sudo grub   * ( it'll open grub prompt)
**grub >** *find /boot/grub/stage1*
 [t ‘ll give you something like …. (hdX,Y) example (hd0,6)]
**grub >** *root (hd0,6)*
**grub >** *setup (hd0)*

now exit grub and reboot . It should again give you the dual boot in working condition.
Check this out for more help. [FIXMBR]("http://stringofthoughts.wordpress.com/2009/03/29/removing-linux/") and [GRUB]("http://stringofthoughts.wordpress.com/2009/03/29/re-installing-grub/")

There are a lot of other reason you might get HAL.DLL not found or corrupted msg. like [check this out]("http://www.downloadatoz.com/windows-registry/faq,windows-could-not-start-because-system32-hal-dll-is-missing-or-corrupt.html"), it might help]

Good luck :)

---

### Post by tarun.winlin on 2009-04-17
> **Tim Sharitt said:**
> If you have your Windows XP CD handy, boot it and run the recovery console (unless you can get to a recovery console without it) and Enter 
```
fixboot
```

or possibly
```
fixboot C:
```

Next, you'll need to restore grub with your Ubuntu live CD. Once you have booted the live CD, open a terminal and do the following

Start grub
```
sudo grub
```

Find grub
```
find /boot/grub/stage1
```

With this information, set the root device by filling in X,Y with whatever was returned
```
root (hdX,Y)
```

Install grub
```
setup (hd0)
```

Then quit grub
```
quit
```

Then reboot and try it out. This second installation of grub should not affect Windows again as the partition information has not changed.

[B]Tried this, but, got the following error when tried to boot into windows again. I am able to boot into ubuntu though

```
Error 13: Invalid or unsupported executable format
Press any key to continue...
```[/B]

> **meierfra. said:**
> The "hal.dll" error usually  means that "boot.ini" needs to be edited.

But to get clearer picture of your setup, I suggest to boot into  Ubuntu and   download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

[B]Below is the output from the 'RESULTS.txt' formed by the script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf71bf71

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   102,414,374   102,398,310   f W95 Ext d (LBA)
/dev/sda5              16,128   102,414,374   102,398,247   7 HPFS/NTFS
/dev/sda2    *    102,414,375   204,812,684   102,398,310  83 Linux
/dev/sda3         204,812,685   208,893,194     4,080,510  82 Linux swap / Solaris
/dev/sda4         208,893,195   976,751,999   767,858,805   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="59780113-d1a0-4c3c-8fd7-f6d74396b827" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="071fd288-8959-42d6-a065-f66e0c56a0bb" 
/dev/sda4: UUID="F0542B64542B2D32" LABEL="data1" TYPE="ntfs" 
/dev/sda5: UUID="0E081ACB081AB1A7" LABEL="Local_HDD_50GB" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tarun/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tarun)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=59780113-d1a0-4c3c-8fd7-f6d74396b827 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=59780113-d1a0-4c3c-8fd7-f6d74396b827

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
uuid		59780113-d1a0-4c3c-8fd7-f6d74396b827
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=59780113-d1a0-4c3c-8fd7-f6d74396b827 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		59780113-d1a0-4c3c-8fd7-f6d74396b827
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=59780113-d1a0-4c3c-8fd7-f6d74396b827 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		59780113-d1a0-4c3c-8fd7-f6d74396b827
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=59780113-d1a0-4c3c-8fd7-f6d74396b827 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		59780113-d1a0-4c3c-8fd7-f6d74396b827
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=59780113-d1a0-4c3c-8fd7-f6d74396b827 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		59780113-d1a0-4c3c-8fd7-f6d74396b827
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=59780113-d1a0-4c3c-8fd7-f6d74396b827 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=071fd288-8959-42d6-a065-f66e0c56a0bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  63.9GB: boot/grub/menu.lst
  63.9GB: boot/grub/stage2
  63.9GB: boot/initrd.img-2.6.27-11-generic
  63.9GB: boot/initrd.img-2.6.27-7-generic
  63.9GB: boot/vmlinuz-2.6.27-11-generic
  63.9GB: boot/vmlinuz-2.6.27-7-generic
  63.9GB: initrd.img
  63.9GB: initrd.img.old
  63.9GB: vmlinuz
  63.9GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```[/B]

Please let me know how should I proceed from here.

---

### Post by meierfra. on 2009-04-17
Open a terminal in Ubuntu and open boot.ini via

```
sudo mount /dev/sda4 /mnt
sudo nano /mnt/boot.ini
```

Change both 

partition(2)

to

partition(4)

Save the file (by following the instructions on the bottom of the screen)

You also need to edit "menu.lst"

```
gksudo gedit /boot/grub/menu.lst
```

Change your windows item to

title		Microsoft Windows XP Professional
rootnoverify		(hd0,3)
chainloader	+1


Save the file, reboot and see whether you can boot into XP.

---

### Post by tarun.winlin on 2009-04-17
> **meierfra. said:**
> Open a terminal in Ubuntu and open boot.ini via

```
sudo mount /dev/sda4 /mnt
sudo nano /mnt/boot.ini
```

Change both 

partition(2)

to

partition(4)

Save the file (by following the instructions on the bottom of the screen)

You also need to edit "menu.lst"

```
gksudo gedit /boot/grub/menu.lst
```

Change your windows item to

title		Microsoft Windows XP Professional
rootnoverify		(hd0,3)
chainloader	+1


Save the file, reboot and see whether you can boot into XP.

:guitar:

You are the champ!!!!

Can you please point me towards a link or document that explains the 'RESULTS.TXT' or the 'Boot.ini' files?

Thanks a ton!!!

---

### Post by meierfra. on 2009-04-17
Glad it worked out. I think your partition table got shuffled somehow, so I was a little worried that you run into more problems.


> Can you please point me towards a link or document that explains the 'RESULTS.TXT' or the 'Boot.ini' files?

Here is an article on boot.ini

[http://msdn.microsoft.com/en-us/library/ms791541.aspx](http://msdn.microsoft.com/en-us/library/ms791541.aspx)

Unfortunately there isn't  any real documentation on the boot_info_script and RESULTS.txt. But I can tell you what I looked for:

> sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

This told me that the  boot files  for XP are on   sda4.   So this is the parition grub has to chain load.  Grub start counting at zero, so sda4 is (hd0,3) in  grub speak.  (The "0" stands for the first hard drive)

> sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

This told me that the XP operating system is on /dev/sda5. So this is the partition boot.ini has to point to,
Windows counts partitions almost the same way as Linux. It starts counting at 1 and it counts in the same order as Linux. But Windows does not   count extended partitions. So windows list the partitions as

sda2 sda3 sda4 sda5

This makes sda5 the fourth partition, and one needs to use partition(4) in boot.ini.

---

### Post by king2007 on 2009-04-17
interesting tips guys must say i am getting very very pissed at microsoft regarding booting-options.
upgrading did not succeed from intrepid ibex to jaunty jackalope, but having downloaded free .iso- image ; was able to burn it and able to boot into a beautiful jaunty - it works ! 
cannot say that from re-installation of windows xp - had some space left on my first disc. it boots into this re-install, but still does not recognize my ubuntu-disc. i now plan to remove this re-install together with windows 7 and try to fix the all-mixed up booting-process.

---

### Post by tarun.winlin on 2009-04-17
> **meierfra. said:**
> Glad it worked out. I think your partition table got shuffled somehow, so I was a little worried that you run into more problems.




Here is an article on boot.ini

[http://msdn.microsoft.com/en-us/library/ms791541.aspx](http://msdn.microsoft.com/en-us/library/ms791541.aspx)

Unfortunately there isn't  any real documentation on the boot_info_script and RESULTS.txt. But I can tell you what I looked for:



This told me that the  boot files  for XP are on   sda4.   So this is the parition grub has to chain load.  Grub start counting at zero, so sda4 is (hd0,3) in  grub speak.  (The "0" stands for the first hard drive)



This told me that the XP operating system is on /dev/sda5. So this is the partition boot.ini has to point to,
Windows counts partitions almost the same way as Linux. It starts counting at 1 and it counts in the same order as Linux. But Windows does not   count extended partitions. So windows list the partitions as

sda2 sda3 sda4 sda5

This makes sda5 the fourth partition, and one needs to use partition(4) in boot.ini.

Thanks a lot for the explanation, I have a few more questions though.

I have just one SATA hard disk on my computer. I have 5 partitions in all on my HDD. 
1) A 8 GB partition which is not being used.
2) 50GB partition for Windows XP OS.
3) 50GB partition for Ubuntu OS.
4) 2GB SWAP partition for Ubuntu
5) Remaining portion is an NTFS extended partition for Data storage only.

Here is the excerpt from the RESULTS file:

```
/dev/sda1              16,065   102,414,374   102,398,310   f W95 Ext d (LBA)
/dev/sda5              16,128   102,414,374   102,398,247   7 HPFS/NTFS
/dev/sda2    *    102,414,375   204,812,684   102,398,310  83 Linux
/dev/sda3         204,812,685   208,893,194     4,080,510  82 Linux swap / Solaris
/dev/sda4         208,893,195   976,751,999   767,858,805   7 HPFS/NTFS

```

According to this here is the mapping:

1) A 8 GB partition which is not being used = sda1
2) 50GB partition for Windows XP OS = sda5
3) 50GB partition for Ubuntu OS = sda2
4) 2GB SWAP partition for Ubuntu = sda3
5) Remaining portion is an NTFS extended partition for Data storage only = sda4

In your post you say that the boot files for XP are on Sda4 (how come, this is my D: drive in windows used only for data storage) & then you say that the operating system itself is on Sda5 (this is matching)???
Are the boot files for an operating in a different partition & the OS in a different partition? :confused:

---

### Post by meierfra. on 2009-04-17
> 1) A 8 GB partition which is not being used = sda1
Not quite.
You do have 8GB of unallocated space at the beginning of the hard drive. But that unallocated space does not have any  associated device.
sda1 is an extended partition of size 51GB.  An extended partition is a container for other partitions. In  your case sda1 just  contains one logical partition, namely sda5.
 The partition table  in the  MBR only has space  four 4 partitions. These four partitions are called primary partitions and are numbered sda1,sda2, sda3,sda4.   If you want to have more than four partitions, one  of your four primary partitions has to be an extended partition. The extended partition can hold many logical partitions, numbered sda5 and higher.

> Are the boot files for an operating in a different partition & the OS in a different partition?
Often, but not always. Since the regular Windows MBR can only boot primary partitions, Windows puts the boot files always on a primary partition.  Since your Windows OS is on a logical partition, the boot files ended up on a different partition than the OS.
But Grub is able to boot logical partitions. So if you want, I can show you how to boot XP directly from sda5.

---

### Post by tarun.winlin on 2009-04-18
> **meierfra. said:**
> Not quite.
You do have 8GB of unallocated space at the beginning of the hard drive. But that unallocated space does not have any  associated device.
sda1 is an extended partition of size 51GB.  An extended partition is a container for other partitions. In  your case sda1 just  contains one logical partition, namely sda5.
 The partition table  in the  MBR only has space  four 4 partitions. These four partitions are called primary partitions and are numbered sda1,sda2, sda3,sda4.   If you want to have more than four partitions, one  of your four primary partitions has to be an extended partition. The extended partition can hold many logical partitions, numbered sda5 and higher.


Often, but not always. Since the regular Windows MBR can only boot primary partitions, Windows puts the boot files always on a primary partition.  Since your Windows OS is on a logical partition, the boot files ended up on a different partition than the OS.
But Grub is able to boot logical partitions. So if you want, I can show you how to boot XP directly from sda5.

Ok so what I understand now is as follows.

Primary partitions would always be sda1, sda2, sda3, or sda4. After that any partition that you see would be a logical partition created on one of the extended partitions.
If the above statement is correct, my next logical questions are:
1) Can we have more than 1 extended partitions on one physical disc?
2) Can we have all 4 as primary partitions & no extended partition on a physical disk?

In my case then sda1 is an extended partition. sda2, sda3, & sda4 are all primary partition while sda2 is the primary boot partition. Windows OS is installed in sda5 which is an extended partition & hence since windows can't boot from an extended partition, it boots from sda4 which is formatted as NTFS.

This raises another question in my mind.

What if I did not have that sda4 partition formatted under NTFS. Where would have windows kept it's boot files then?

What I mean is let's say the Windows OS is installed on a extended partition & all the primary partitions on the system are installed with ext3 filesystem which Windows cannot read. How would Windows boot then?

Thanks a lot for taking the time in explaining me all this.

---

### Post by meierfra. on 2009-04-18
> Primary partitions would always be sda1, sda2, sda3, or sda4. After that any partition that you see would be a logical partition created on one of the extended partitions.
Correct.

> 1) Can we have more than 1 extended partitions on one physical disc?
No.

> 2) Can we have all 4 as primary partitions & no extended partition on a physical disk?
Yes.

> In my case then sda1 is an extended partition. sda2, sda3, & sda4 are all primary partition while sda2 is the primary boot partition. Windows OS is installed in sda5 which is an extended partition & hence since windows can't boot from an extended partition, it boots from sda4 which is formatted as NTFS.

Small correction.  It should say:

In my case then sda1 is an extended partition. sda2, sda3, & sda4 are all primary partition while sda2 is the primary boot partition. Windows OS is installed in sda5 which is an [COLOR="Red"]logical[/COLOR] partition & hence since windows can't boot from an [COLOR="Red"]logical[/COLOR] partition, it boots from sda4 which is formatted as NTFS.

Also since you are using grub as the  main boot loader, the boot partition does not have to be primary and the boot flags are irrelevant.

> What if I did not have that sda4 partition formatted under NTFS. Where would have windows kept it's boot files then?

What I mean is let's say the Windows OS is installed on a extended partition & all the primary partitions on the system are installed with ext3 filesystem which Windows cannot read. How would Windows boot then?

Windows will plainly refuse to install if there is no primary fat or ntfs partition on the boot drive. Often the Windows CD won't even boot under those circumstances.

But if you really would like to  have Windows on a logical partition with all primary partition ext3, it be done in one of the following ways:

1) Create a primary ntfs  partition. Install Windows on logical partition with the boot files on the primary ntfs partition. Move the boot files to the Windows partition and reformat the primary ntfs partition  to ext3.

2)  Install Windows on a primary ntfs partition  and convert the primary partition to  logical partition.

3)  Install  Windows on a primary ntfs partition, clone it to  a logical partition and  then reformat  the original  to ext3.

In either case, you won't be able to boot Windows with a Windows MBR. You will have to use grub or lilo or some other boot loader to chainload the Windows boot loader.

---

### Post by tarun.winlin on 2009-04-18
> 
Quote:
In my case then sda1 is an extended partition. sda2, sda3, & sda4 are all primary partition while sda2 is the primary boot partition. Windows OS is installed in sda5 which is an extended partition & hence since windows can't boot from an extended partition, it boots from sda4 which is formatted as NTFS.
Small correction. It should say:

In my case then sda1 is an extended partition. sda2, sda3, & sda4 are all primary partition while sda2 is the primary boot partition. Windows OS is installed in sda5 which is an logical partition & hence since windows can't boot from an logical partition, it boots from sda4 which is formatted as NTFS.

Also since you are using grub as the main boot loader, the boot partition does not have to be primary and the boot flags are irrelevant.

Now, I was assuming that an extended partition can have only a logical partition. Hence I was using the name interchangeably. From your post it looks that is in correct. If incorrect, then what are the other types of partitions than one can create in a extended partition?

> In either case, you won't be able to boot Windows with a Windows MBR. You will have to use grub or lilo or some other boot loader to chainload the Windows boot loader.

So, where does the MBR exists? Does it exists on one of the primary paritions? 

Is it correct to say a MBR is one which is used to give the PC information to provide us with the boot menu & then chainload the bootloader of a particular OS as per the choice?

What is a primary boot partition then?

Sorry to bug you with so many questions but I feel if I do not understand it right now, I will never understand it.
And you look like someone who knows this in & out.

When I do a Start-->Run-->notepad C:/boot.ini

The file that opens up still has the below code:
> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


I remember we changed partition(2) to partition(4) in some boot.ini file. Which file was that?

If at some later time I completely remove linux, would my windows installation still work?

---

### Post by tarun.winlin on 2009-04-18
Bump!!

---

### Post by meierfra. on 2009-04-18
You should wait 24 hours before bumping a thread.

> I was assuming that an extended partition can have only a logical partition. 
It can have many partitions (I think, 11 for a sata drive and 59 for an ide drive)

> what are the other types of partitions than one can create in a extended partition?
Any type  of partition. (but not another extended partition)


> So, where does the MBR exists? 


The MBR is the very first sector of the hard drive. It comes before any partition. 


> Is it correct to say a MBR is one which is used to give the PC information to provide us with the boot menu & then chainload the bootloader of a particular OS as per the choice?
Almost. Booting with grub works like this:

stage 1 (located in the MBR) -> stage1.5 (located in sector 2-63)->stage 2(located on the Ubuntu boot partition)

stage 2 reads the file /boot/grub/menu.lst and displays the  Boot menu. stage 2 then also will load the kernel (of a linux OS) or chainload another boot loader.


> default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW S

boot.ini is a hidden system file. Maybe notepad opened a backup of boot.ini. To access boot.ini from XP see

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by tarun.winlin on 2009-04-18
> You should wait 24 hours before bumping a thread.

I am very sorry. I will keep that in mind from next time on. Thanks for pointing that out.

> boot.ini is a hidden system file. Maybe notepad opened a backup of boot.ini. To access boot.ini from XP see

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

I used this method to check the contents of the 'boot.ini' file, but, it still shows the same thing:

> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Any Idea why?? Because I think we changed it when we mounted it from ubuntu & change the contents.

So the boot procedure when dual booting Windows & Linux & using GRUB as the boot loader would be roughly as follows:
1) Switch on the PC.
2) Control goes to the BIOS.
3) End of the BIOS points to the MBR
4) MBR has the boot program in the first sector & the partition table in the last sector.
5) MBR displays the 'boot menu' giving an option to boot either in windows or linux.
6) We select an option from the interface.
7) Control goes to that partition & the OS takes over from there.

If the above is correct where is the 'boot.ini' needed in this entire procedure?

Thanks again for all the help. This forum is a blessing for Linux newbies :-)

---

### Post by meierfra. on 2009-04-18
> ny Idea why?? Because I think we changed it when we mounted it from ubuntu & change the contents.
Very strange.

Maybe, you have a second boot.ini. What is the output of

```
sudo mount /dev/sda4 /mnt
cat /mnt/boot.ini
sudo umount /mnt
sudo mount /dev/sda5 /mnt
cat /mnt/boot.ini

```

> 5) MBR displays the 'boot menu' giving an option to boot either in windows or linux.
Not quite. The "MBR" is to small to hold the code to display the "boot menu". That's why the MBR just calls "stage1.5" and "stage1.5" calls stage2. Stage2 is a file on the Ubuntu partion  (size 120kB, the MBR is only 0.5kB). The code in stage2 then displays the Boot menu.


> If the above is correct where is the 'boot.ini' needed in this entire procedure?

Stage 2 calls the boot sector of /dev/sda4.  The boot sector  calls the file ntldr on /dev/sda4.  ntldr looks at boot.ini for the location  of the Windows 0S.

---

### Post by tarun.winlin on 2009-04-19
> Maybe, you have a second boot.ini. What is the output of
I will post the output when I am back on my linux box.

> Not quite. The "MBR" is to small to hold the code to display the "boot menu". That's why the MBR just calls "stage1.5" and "stage1.5" calls stage2. Stage2 is a file on the Ubuntu partion (size 120kB, the MBR is only 0.5kB). The code in stage2 then displays the Boot menu.
This text is taken from: [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
```
The MBR can simply assume that the one active partition on the current drive is supposed to boot, or alternately, it can be programmed as a Dual boot MBR. A dual boot MBR must interact with the user to determine which partition on which drive should boot, and may transfer control to the MBR of a different drive.
```

I am mixing up things here???

---

### Post by meierfra. on 2009-04-19
> The MBR can simply assume that the one active partition on the current drive is supposed to boot, or alternately, it can be programmed as a Dual boot MBR. A dual boot MBR [COLOR="Red"]must[/COLOR] interact with the user to determine which partition on which drive should boot, and may transfer control to the MBR of a different drive.

The "must" part is wrong.  It does not have to be the MBR which interacts with the users.  There are some MBR's  which interact with the users, but only in a very primitive way. 

The Grub MBR does not interact with the user.  The interaction with user is done by Grub's stage 2.

---

### Post by tarun.winlin on 2009-04-19
> Maybe, you have a second boot.ini. What is the output of

```
tarun@tarun-home:~$ sudo mount /dev/sda4 /mnt
[sudo] password for tarun: 
tarun@tarun-home:~$ cat /mnt/boot.ini
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
tarun@tarun-home:~$ sudo umount /mnt
tarun@tarun-home:~$ sudo mount /dev/sda5 /mnt
tarun@tarun-home:~$ cat /mnt/boot.ini
cat: /mnt/boot.ini: No such file or directory
tarun@tarun-home:~$
```

This is Wierd!!!!:confused:

---

### Post by meierfra. on 2009-04-19
> This is Wierd!!!!

Yes, it is. But as long as your system is working, I wouldn't worry about it. 

What is the output of

```
sudo mount /dev/sda5 /mnt
ls -l  /mount

```

---

### Post by tarun.winlin on 2009-04-22
Here is the output you requested.

```
sudo ls -l /mnt
total 2095206
-rwxrwxrwx 1 root root          0 2008-08-16 08:38 AUTOEXEC.BAT
drwxrwxrwx 1 root root       4096 2009-03-27 20:38 Config.Msi
-rwxrwxrwx 1 root root          0 2008-08-16 08:38 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-08-16 08:42 Documents and Settings
-rwxrwxrwx 1 root root        266 2009-03-24 21:30 hook.log
drwxrwxrwx 1 root root       4096 2008-08-21 15:15 Inetpub
-rwxrwxrwx 1 root root          0 2008-08-16 08:38 IO.SYS
-rwxrwxrwx 1 root root          0 2008-08-16 08:38 MSDOS.SYS
-rwxrwxrwx 1 root root 2145386496 2009-04-22 10:32 pagefile.sys
drwxrwxrwx 1 root root      12288 2009-04-10 13:37 Program Files
drwxrwxrwx 1 root root          0 2008-08-17 05:12 RECYCLER
-rwxrwxrwx 1 root root        114 2009-04-22 10:32 sccfg.sys
-rwxrwxrwx 2 root root        114 2009-02-07 19:32 sccfg.sys.bd.ren
drwxrwxrwx 1 root root       4096 2008-08-16 08:42 System Volume Information
drwxrwxrwx 1 root root          0 2008-11-23 23:37 temp
-rwxrwxrwx 2 root root        594 2009-01-13 14:59 updatedatfix.log
drwxrwxrwx 1 root root          0 2008-08-26 04:07 Virtual Machines
drwxrwxrwx 1 root root      69632 2009-04-17 13:39 WINDOWS
```

---

### Post by meierfra. on 2009-04-22
OK. One last try to solve the mystery:

```
sudo mount /dev/sda4 /mnt
ls -l  /mount

```

---

