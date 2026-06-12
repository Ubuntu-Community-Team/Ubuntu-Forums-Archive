---
title: "GRUB dual-booting woes with multiple hard drives"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Beez0 on 2009-04-15
I'm converting an old box with 5 hard drives in to a home server using xubuntu. All the storage drives (4) are NTFS. My first problem is after every restart I cannot mount the NTFS drives. Ntfsmount says they are scheduled for check and I need to boot in to windows twice. So I reformatted the main drive, cut it in to two partitions and installed windows 7, then Xubuntu. Now it cannot boot in to windows 7. I know this is a common topic but I have been through a dozen threads and none of them seem to work.

What's weird is when I run:

```
grub> find /boot/grub/stage1
```

I get (hd3,0). But this is a storage drive. When Xubuntu boots it says booting from (hd0,0). setup(hd0) in grub gives me Error 12: invalid device requested. So in menu.lst I have tried (hd0,0), (hd0,1), (hd0,2),(hd0,3) and (hd3, 1) and I always get an error. It should be on (hd0,1) but I get Error 12: Invalid device requested, or BOOTMGR is missing. Thanks in advance for your help.

Here is fdisk for good measure:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81cdc001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x366e9c1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19449   156222464    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
116 heads, 51 sectors/track, 52836 cylinders
Units = cylinders of 5916 * 512 = 3028992 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       52814   156222464    7  HPFS/NTFS
/dev/sdc4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdd: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef17ef17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3709    29792511   83  Linux
/dev/sdd2   *        3710        8666    39816192    7  HPFS/NTFS
/dev/sdd3            8667        9039     2996122+   5  Extended
/dev/sdd5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sde: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9f2f9f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       14588   117178078+   7  HPFS/NTFS

menu.lst entry:

title		Windows 7 (maybe)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader        +1

---

### Post by meierfra. on 2009-04-15
Since it's not clear,  which partition holds the Window7 boot files, and which drive you are booting from, I suggest to boot into Xubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Beez0 on 2009-04-15
This is odd too. Before reformatting and installing Xubuntu and Windows 7 I had Vista. Now it seems Vista is showing up and Windows 7 isn't. Vista is listed in the GRUB options but obviously doesn't work. Before installing Xubuntu I could boot into Windows 7 just fine. Thanks for the help!

EDIT: The windows 7 partition is definitely somewhere. I can mount it with ntfsmount /dev/sdd2

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81cdc001

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x366e9c1b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   312,446,975   312,444,928   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
116 heads, 51 sectors/track, 52836 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   312,446,975   312,444,928   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef17ef17

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    59,585,084    59,585,022  83 Linux
/dev/sdd2    *     59,586,560   139,218,943    79,632,384   7 HPFS/NTFS
/dev/sdd3         139,219,290   145,211,534     5,992,245   5 Extended
/dev/sdd5         139,219,353   145,211,534     5,992,182  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf9f2f9f2

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   234,356,219   234,356,157   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C684194084193501" LABEL="MOVIES" TYPE="ntfs" 
/dev/sdb1: UUID="2264AB7C64AB50F9" LABEL="PROGRAMS" TYPE="ntfs" 
/dev/sdc1: UUID="80A4462AA4462350" LABEL="GAMES" TYPE="ntfs" 
/dev/sdd1: UUID="e0e5ef1a-297b-4e6a-9dde-1e004de5e677" TYPE="ext3" 
/dev/sdd2: UUID="E84C21DA4C21A472" TYPE="ntfs" 
/dev/sdd5: UUID="4c434af5-26d0-42c0-8419-629db1cb37ca" TYPE="swap" 
/dev/sde1: UUID="6CF20C3AF20C0B52" LABEL="MUSIC" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sdd2 on /media/WINDOWS type fuseblk (rw,nosuid,nodev,default_permissions,allow_other,blksize=4096,user=root)


=========================== sdd1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e0e5ef1a-297b-4e6a-9dde-1e004de5e677

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
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows 7 (maybe)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader        +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Windows Vista/Longhorn (loader)
root		(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4c434af5-26d0-42c0-8419-629db1cb37ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/menu.lst
  13.0GB: boot/grub/stage2
  13.0GB: boot/initrd.img-2.6.27-11-generic
  13.1GB: boot/initrd.img-2.6.27-7-generic
  13.0GB: boot/vmlinuz-2.6.27-11-generic
  13.1GB: boot/vmlinuz-2.6.27-7-generic
  13.0GB: initrd.img
  13.1GB: initrd.img.old
  13.0GB: vmlinuz
  13.1GB: vmlinuz.old

```

---

### Post by meierfra. on 2009-04-15
> title Windows 7 (maybe)
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1 

That is the correct  entry.


> Now it seems Vista is showing up and Windows 7 isn't. 

Thats's the fault of the script. It always identifies  Win7 has Vista.


It seems the Win7 boot files are missing. Did you delete or format any partitions when you installed Xubuntu?


Anyway, to fix your  problem, set your bios  so that the 74GB Xubuntu/Win 7 is first  among the hard drives in the  bios' boot priority order (although it looks like they are already set that way)

Then boot from your Win7 DVD.  Select "repair computer".  If the  DVD offers you to fix a "start up problems", say "Yes".  If not, choose "Startup Repair" at the next screen.  You might have  run "StartUp Repair" a few times (it tends to fix one problem at the time).


If this does not fix your problem, come back here and report all error messages you got.

---

### Post by Beez0 on 2009-04-16
Ok that makes sense but I've run the startup repair option several times and I still get an Error 22: no such partition when I try to start windows. Are you sure (hd0,1) is the correct entry?

Now when it boots Xubuntu it says it's booting from (hd3,0). So I tried changing menu.lst to boot windows from (hd3,1). Then it says BOOTMGR is missing.

Any suggestions?

---

### Post by meierfra. on 2009-04-16
Sounds like you are now booting from the  /dev/sda, (one of your 160 GB drives). 
Add  

title Windows 7 
rootnoverify (hd3,1)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1 

to you menu.lst
Reboot and try the new entry.

If this did not work,  set your  bios to boot from the 76GB drive /dev/sdd and try the "rootnoverify (hd0,1)" entry.

If none of this works, run the boot info script  and post "RESULTS.txt" again. (Make sure to post the new "RESULTS.txt", it might be called "RESULTS1.txt)

---

### Post by Beez0 on 2009-04-16
Nope tried (hd3,1) where it should be but I still get BOOTMGR is missing. When I try to run startup repair it says something like a system partition could not be found. I tried chkdsk /r C: and it found and fixed some errors but did not help the problem. Here is the recent RESULTS.txt:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81cdc001

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   312,578,047   312,576,000   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x366e9c1b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   312,446,975   312,444,928   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
116 heads, 51 sectors/track, 52836 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   312,446,975   312,444,928   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef17ef17

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63    59,585,084    59,585,022  83 Linux
/dev/sdd2    *     59,586,560   139,218,943    79,632,384   7 HPFS/NTFS
/dev/sdd3         139,219,290   145,211,534     5,992,245   5 Extended
/dev/sdd5         139,219,353   145,211,534     5,992,182  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf9f2f9f2

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63   234,356,219   234,356,157   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C684194084193501" LABEL="MOVIES" TYPE="ntfs" 
/dev/sdb1: UUID="2264AB7C64AB50F9" LABEL="PROGRAMS" TYPE="ntfs" 
/dev/sdc1: UUID="80A4462AA4462350" LABEL="GAMES" TYPE="ntfs" 
/dev/sdd1: UUID="e0e5ef1a-297b-4e6a-9dde-1e004de5e677" TYPE="ext3" 
/dev/sdd2: UUID="E84C21DA4C21A472" TYPE="ntfs" 
/dev/sdd5: UUID="4c434af5-26d0-42c0-8419-629db1cb37ca" TYPE="swap" 
/dev/sde1: UUID="6CF20C3AF20C0B52" LABEL="MUSIC" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
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


=========================== sdd1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e0e5ef1a-297b-4e6a-9dde-1e004de5e677

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
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		e0e5ef1a-297b-4e6a-9dde-1e004de5e677
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
title Windows 7
rootnoverify (hd3,1)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1 


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Windows Vista/Longhorn (loader)
root		(hd4,0)
savedefault
makeactive
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e0e5ef1a-297b-4e6a-9dde-1e004de5e677 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4c434af5-26d0-42c0-8419-629db1cb37ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


  13.1GB: boot/grub/menu.lst
  13.0GB: boot/grub/stage2
  13.0GB: boot/initrd.img-2.6.27-11-generic
  13.1GB: boot/initrd.img-2.6.27-7-generic
  13.0GB: boot/vmlinuz-2.6.27-11-generic
  13.1GB: boot/vmlinuz-2.6.27-7-generic
  13.0GB: initrd.img
  13.1GB: initrd.img.old
  13.0GB: vmlinuz
  13.1GB: vmlinuz.old

```

---

### Post by meierfra. on 2009-04-16
You are still missing the boot files. So I suggest to follow this tutorial to restore your boot files:

[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)

Step1 you already have done. You don't have to do Step3.

So just do Step2.  You also don't have to do the last command in Step 2 (E:\boot\bootsect.exe /nt60  C: )

---

### Post by Beez0 on 2009-04-16
Alright did all that...at least I got a different error this time.

It says "Windows failed to start"

Status: 0xc000000f
Info: the boot selection failed because a required device is inaccessible.

So I ran chkdsk /r G: (which is the drive diskpart told me it should be on). Same error. Ran startup repair a few times for good measure. Still nothing.

I don't even think I would need windows if the NTFS drives would stop getting flagged as dirty. I can't mount them in Xubuntu without booting in to windows. The one time I could (right after installing it) they worked great. I can't convert them to ext3 because they're all filled with data. Maybe if that problem were fixed I could forget about windows entirely? But if Windows is on the verge of working that would be nice too.

Oh and the 74gb is definitely set first priority in the BIOS, which makes me wonder why the partition on it got assigned to G:

---

### Post by meierfra. on 2009-04-16
> 74gb is definitely set first priority in the BIOS, wh
I'm confused. If you are booting from the 74gb drive, then the correct entry for Win 7 in menu.lst should be "(hd0,1)".  Are you using "(hd0,1)" or "(hd3,1)"?

> It says "Windows failed to start"

Status: 0xc000000f
Info: the boot selection failed because a required device is inaccessible.


> G: (which is the drive diskpart told me it should be on).


Both of these make me think that your problems is caused by the Win 7 registry.  The easiest what the fix that problem is to delete the "mounted devices" part of the Win 7 registry. This will force Win 7 to reassign all the drive letters during boot up.

But before I show you how to do that, could your run the boot info script one more time? I just want to see whether the boot files are now in the correct place.

Also to avoid confusing Win 7, you should rename the /Boot/ folder on /dev/sda1:

```
sudo mount /dev/sda1 /mnt
sudo mv /mnt/Boot /mnt/BootRenamed
```

---

