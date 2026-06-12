---
title: "grub-windows 7 reboot loop"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by kristersaurus on 2009-08-06
hey guys,

im having a problem after installing ubuntu on a machine already running windows 7. 

I can boot into ubuntu from grub just fine, but when i select "windows vista/longhorn (loader)" my machine just reboots. no error message, just a reboot. never really ran into this before. does anyone have any ideas?

this is the menu.lst entry for the windows partition:

```

title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

```

Windows appears in fstab as /dev/sda2, with my root ubuntu part. at /dev/sda3, and swap at /dev/sda4

---

### Post by merlinus on 2009-08-06
Change this:

title Windows Vista/Longhorn (loader)
[COLOR=Red]root (hd0,0)[/COLOR]
savedefault
makeactive
chainloader +1

to this:

title Windows Vista/Longhorn (loader)
[COLOR=Red]rootnoverify (hd0,1)[/COLOR]
savedefault
makeactive
chainloader +1

if windows is on sda2.

---

### Post by kristersaurus on 2009-08-06
thanks for the response.

still no joy, however. i tried both hd(1,0) and hd(0,1)

whats the difference between root and rootnoverify?

---

### Post by merlinus on 2009-08-06
> 
 i tried both hd(1,0) and hd(0,1)
Did you write (hd0,1) and  not hd(0,1)?

Also, post results of

```
sudo fdisk -l
```

---

### Post by kristersaurus on 2009-08-06
yeah, i did write (hd0,1) not hd(0,1). sorry. im working on an app whilst troubleshooting this and crossing some wires.

```

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6789b42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          26       42578   341796875    7  HPFS/NTFS
/dev/sda3           42579       48519    47721082+  83  Linux
/dev/sda4           48520       48641      979965   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6a313ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9730    78149688+  42  SFS

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c911c90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9726    78123944+  42  SFS

```

thanks again for the help.

If it helps any, it appears that the 200MB partition is something windows created..it contains bootmgr among other things.

---

### Post by merlinus on 2009-08-07
If bootmgr is on sda1 -- (hd0,0) in grub terms -- then that may be why it will not start, since the windows files are on sda2.  Another problem may be that sda1 does not end on a cylinder boundary, and so there is some overlap with sda2.

BTW, what is the boot order of your hdds in bios?

---

### Post by kristersaurus on 2009-08-07
400gb first, followed by the two 80 gb drives.

ive seen a lot of missing bootmgr problems with grub and windows 7...no flat reboots with no error message, however. so i would agree that it seems to be a problem...im just surprised there is no error message.

---

### Post by merlinus on 2009-08-07
Is there a boot.ini file in windows that might contain useful info, especially in terms of paths?

---

### Post by kristersaurus on 2009-08-07
this is the current state of my windows entry, btw:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
rootnoverify		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by merlinus on 2009-08-07
If you are wanting the loader, then (hd0,0) is correct.  Try that, but keep rootnoverify.

And you might need to change the boot flag to sda1 as well.

---

### Post by kristersaurus on 2009-08-07
what bootflag are you referring to?

---

### Post by merlinus on 2009-08-07
The boot flag shows as an asterisk next to sda2 in the sudo fdisk -l results.  You can change it to sda1 using gparted.

Windows needs it, although linux does not.

Also, delete makeactive from the menu.lst windows stanzas.

---

### Post by kristersaurus on 2009-08-07
crap. still a no-go.  tried with and without the bootflag set on sda1. rootnoverify (hd0,0) and (hd0,1).

thanks for your persistence.

---

### Post by merlinus on 2009-08-07
Just to be sure, do not have more than one boot flag at a time set on sda, and did you try deleting makeactive from the window entry?

Another idea is to use supergrub to try to boot windows to ensure it is still working:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by oldfred on 2009-08-07
Vista and Win 7 should use rootnoverify and no makeactive lines. like:

title        Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify    (hd0,0)
savedefault
chainloader +1

If you installed Win7 to an empty drive it creates a separate 100mb boot partition. If the drive is not empty it includes the boot in its partition.

On Windows XP either rootnoverify without the makeactive or root (hd0,0) with the makeactive is correct.

---

### Post by presence1960 on 2009-08-07
Boot into ubuntu and download the [Boot Info Script 0.32]("http://sourceforge.net/projects/bootinfoscript/") to your desktop. Then open a terminal and run this command: ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on your desktop which contains plenty of info on your setup & boot process. paste the entire contents of that file back here. When pasted here highlight all text and click the # sign on the toolbar to place code tags around the text. This will give us way more info than running a few commands from terminal.

---

### Post by kristersaurus on 2009-08-07
Here she be. Still no luck with grub, but bootrec.exe /fixmbr from the windows install disk fixes it right up.

Thanks again for all the input.


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sdb1 starts at sector 63. According to the info in the 
                       boot sector, sdb1 has 156243967 sectors, but according 
                       to the info from fdisk, it has 156299377 sectors.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sdc1 starts at sector 63. According to the info in the 
                       boot sector, sdc1 has 156243967 sectors, but according 
                       to the info from fdisk, it has 156247889 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf6789b42

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2    *        411,648   684,005,397   683,593,750   7 HPFS/NTFS
/dev/sda3         684,015,570   779,457,734    95,442,165  83 Linux
/dev/sda4         779,457,735   781,417,664     1,959,930  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd6a313ab

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,299,439   156,299,377  42 SFS


GUID Partition Table detected,but does not seem to be used.

Partition           Start           End          Size System
/dev/sdb1              34       262,177       262,144 Microsoft Windows
/dev/sdb17 4,594,164,201,127,149,5681,153,414,085,816,090,624-3,440,750,115,311,058,943 -
/dev/sdb18              0             0             1 -
/dev/sdb19 162,129,586,589,466,624162,129,586,592,804,944     3,338,321 -

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c911c90

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   156,247,951   156,247,889  42 SFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9C9C709E9C70751C" TYPE="ntfs" 
/dev/sda2: UUID="3AD86F81D86F3A71" TYPE="ntfs" 
/dev/sda3: UUID="0ee7de11-feb3-4dac-9ada-b09ed3afab67" TYPE="ext3" 
/dev/sda4: UUID="11a05876-1ec0-468f-ab15-bb8d4777483e" TYPE="swap" 
/dev/sdb1: UUID="5A9A1BB49A1B8B9F" LABEL="Mirrored" TYPE="ntfs" 
/dev/sdc1: UUID="5A9A1BB49A1B8B9F" LABEL="Mirrored" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/krister/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=krister)


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=0ee7de11-feb3-4dac-9ada-b09ed3afab67 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 9.04, kernel 2.6.28-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0ee7de11-feb3-4dac-9ada-b09ed3afab67 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0ee7de11-feb3-4dac-9ada-b09ed3afab67 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=0ee7de11-feb3-4dac-9ada-b09ed3afab67 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=0ee7de11-feb3-4dac-9ada-b09ed3afab67 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ee7de11-feb3-4dac-9ada-b09ed3afab67 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0ee7de11-feb3-4dac-9ada-b09ed3afab67 ro  single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,2)
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0ee7de11-feb3-4dac-9ada-b09ed3afab67 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=3AD86F81D86F3A71 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=11a05876-1ec0-468f-ab15-bb8d4777483e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 373.9GB: boot/grub/menu.lst
 373.8GB: boot/grub/stage2
 373.8GB: boot/initrd.img-2.6.24-16-generic
 373.8GB: boot/initrd.img-2.6.24-16-generic.bak
 373.8GB: boot/initrd.img-2.6.27-14-generic
 373.8GB: boot/initrd.img-2.6.28-14-generic
 373.8GB: boot/vmlinuz-2.6.24-16-generic
 373.9GB: boot/vmlinuz-2.6.27-14-generic
 373.9GB: boot/vmlinuz-2.6.28-14-generic
 373.8GB: initrd.img
 373.8GB: initrd.img.old
 373.9GB: vmlinuz
 373.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown GPT Partiton Type
5052495648454144000030630002000c
Unknown GPT Partiton Type
64302d613562652d3030613063393164
Unknown GPT Partiton Type
30000000000000000000000000000000

=============================== StdErr Messages: ===============================

mkdir: cannot create directory `sda4': File exists

```

---

### Post by presence1960 on 2009-08-07
you still have the bootflag on sda2. it needs to be on sda1. You can change it in ubuntu with partition editor (System > Administration > Partition Editor. make sure you turn it off for sda2 as well.

I see you have SFS- that is an encrypted file system correct? I know zippo about it. But your partition tables are messed up for sdb , but that should have no effect on your booting from sda.

your menu.lst is all messed up. Your newer kernels are down the bottom of the list instead of at the top. Take the boot flag off sda2 and set it to sda1. Then edit your menu.lst windows entry like this:

```
# This entry automatically added by the Debian installer for a non-linux OS # on /dev/sda1
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,0)
chainloader	+1
```

Windows does not "need" a boot flag, but since you have one you have it set to the wrong partition. Windows 7 with a System Reserved partition (sda1) must boot from that partition. remove the boot flag from sda2 and set it to sda1. Then see what you have. Edit menu.lst also then try to boot windows. here is my fdisk output:
```
raz@raz-desktop:~$ sudo sfisk -l
[sudo] password for raz: 
sudo: sfisk: command not found
raz@raz-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   5  Extended
/dev/sda2            5223       19843   117443182+  83  Linux
/dev/sda3           19844       25064    41937682+   7  HPFS/NTFS
/dev/sda4           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16193   130070241   83  Linux
/dev/sdb2           16194       19457    26218080   83  Linux

Disk /dev/sdg: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079662

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         115      923706    b  W95 FAT32
/dev/sdg2             116        9964    79112092+  83  Linux
raz@raz-desktop:~$ 
```
sda5 is Ubuntu Jaunty, sda7 is Mint 5, sdb 2 is Sabayon 4.1 sda4 is Win 7(notice no boot flag) sda2 and sdb1 are linux data partitions, sda3 is windows data partition

P.S.  I meant windows 7 does not need a boot flag. Win 7 is the first windows version I have seen installed without a boot flag. Also I am glad you started this thread because I just noticed my sda1 (extended) had a boot flag on it which I promptly booted the Live CD and removed that.

---

### Post by kristersaurus on 2009-08-08
hey, thanks for the info.

just fyi, sda2 is where windows install opted to put the boot flag.

i did try booting after removing the boot flag from sda2 and putting it on sda1. i also removed the makeactive and savedefault and tried booting with rootnoverify (hd0,0), with no luck. it still blanks for a second and reboots. so weird. i wish it at least gave me some error indication.

i'm always open to more options, but i think i might be stuck using the windows install dvd to do a bootrec /fixmbr and running ubuntu from within windows using virtualbox or something...yuck.

---

### Post by presence1960 on 2009-08-08
> **kristersaurus said:**
> hey, thanks for the info.

just fyi, sda2 is where windows install opted to put the boot flag.

i did try booting after removing the boot flag from sda2 and putting it on sda1. i also removed the makeactive and savedefault and tried booting with rootnoverify (hd0,0), with no luck. it still blanks for a second and reboots. so weird. i wish it at least gave me some error indication.

i'm always open to more options, but i think i might be stuck using the windows install dvd to do a bootrec /fixmbr and running ubuntu from within windows using virtualbox or something...yuck.

before you run ubuntu from windows. Why don't you try what you said withe disk. if that doesn't work try reinstalling windows. I would delete sda1 & sda2 and create 1 NTFS  primary partition with gparted. Then I would install windows to that newly created NTFS primary partition.

---

### Post by cionci on 2009-10-10
I've the same issue.

sdc and sdd are on a 19160 SCSI adapter.

Windows 7 is installed on sdc2, Interpid on sdd1.
Actually if I change the boot order from BIOS I can boot into each OS.
From Grub I cannot start Windows 7, if I try the system reboots.
Inside grub shell Intrepid partition as been identified by (hd0,0) (using command find), so Windows 7 partition is (hd1,1).

I've tried:

rootnoverify	(hd0,0)
chainloader	+1

rootnoverify	(hd1,0)
chainloader	+1

rootnoverify	(hd1,1)
chainloader	+1

rootnoverify	(hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader	+1

rootnoverify	(hd1,1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader	+1

I'v tried makeactive too.

```

Disco /dev/sda: 82.3 GB, 82348277760 byte
255 testine, 63 settori/tracce, 10011 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0xb4419b89

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10011    80413326    7  HPFS/NTFS

Disco /dev/sdb: 640.1 GB, 640135028736 byte
255 testine, 63 settori/tracce, 77825 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0xd83ec100

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77825   625129281   83  Linux

Disco /dev/sdc: 73.5 GB, 73543163904 byte
255 testine, 63 settori/tracce, 8941 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0xb814b814

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2550    20482843+  83  Linux
/dev/sdc2   *        2551        8941    51335707+   7  HPFS/NTFS

Disco /dev/sdd: 73.5 GB, 73543163904 byte
255 testine, 63 settori/tracce, 8941 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x5ced3687

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2611    20972826   83  Linux
/dev/sdd2            2612        8941    50845725    5  Esteso
/dev/sdd5            2612        3916    10482381   83  Linux
/dev/sdd6            3917        4328     3309358+  82  Linux swap / Solaris
/dev/sdd7   *        4329        8941    37053891   83  Linux

```
Any idea ?

---

### Post by presence1960 on 2009-10-10
> **cionci said:**
> I've the same issue.

sdc and sdd are on a 19160 SCSI adapter.

Windows 7 is installed on sdc2, Interpid on sdd1.
Actually if I change the boot order from BIOS I can boot into each OS.
From Grub I cannot start Windows 7, if I try the system reboots.
Inside grub shell Intrepid partition as been identified by (hd0,0) (using command find), so Windows 7 partition is (hd1,1).

I've tried:

rootnoverify	(hd0,0)
chainloader	+1

rootnoverify	(hd1,0)
chainloader	+1

rootnoverify	(hd1,1)
chainloader	+1

rootnoverify	(hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader	+1

rootnoverify	(hd1,1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader	+1

I'v tried makeactive too.

```

Disco /dev/sda: 82.3 GB, 82348277760 byte
255 testine, 63 settori/tracce, 10011 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0xb4419b89

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10011    80413326    7  HPFS/NTFS

Disco /dev/sdb: 640.1 GB, 640135028736 byte
255 testine, 63 settori/tracce, 77825 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0xd83ec100

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       77825   625129281   83  Linux

Disco /dev/sdc: 73.5 GB, 73543163904 byte
255 testine, 63 settori/tracce, 8941 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0xb814b814

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2550    20482843+  83  Linux
/dev/sdc2   *        2551        8941    51335707+   7  HPFS/NTFS

Disco /dev/sdd: 73.5 GB, 73543163904 byte
255 testine, 63 settori/tracce, 8941 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x5ced3687

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2611    20972826   83  Linux
/dev/sdd2            2612        8941    50845725    5  Esteso
/dev/sdd5            2612        3916    10482381   83  Linux
/dev/sdd6            3917        4328     3309358+  82  Linux swap / Solaris
/dev/sdd7   *        4329        8941    37053891   83  Linux

```
Any idea ?

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Also give me the order of your hard disk booting in BIOS please.

---

### Post by cionci on 2009-10-10
I think there's a problem in the script because Windows is only on the MBR of sda and sdc.

sda and sdb are Sata hdd. sdc and sdb are SCSI hdd.

Boot order is:
sdd
sdc
sda
sdb

From the grub console find /boot/grub/stage1 returns (hd0,0).
I would like to boot at least one of the Win 7 installations.

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdd1 and 
                       looks at sector 29897279 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdd. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: tipo di filesystem 'ext4' sconosciuto

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 82.3 GB, 82348277760 byte
255 testine, 63 settori/tracce, 10011 cilindri, totale 160836480 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0xb4419b89

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   160,826,714   160,826,652   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 640.1 GB, 640135028736 byte
255 testine, 63 settori/tracce, 77825 cilindri, totale 1250263728 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0xd83ec100

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,250,258,624 1,250,258,562  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 73.5 GB, 73543163904 byte
255 testine, 63 settori/tracce, 8941 cilindri, totale 143638992 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0xb814b814

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687  83 Linux
/dev/sdc2    *     40,965,750   143,637,164   102,671,415   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disco /dev/sdd: 73.5 GB, 73543163904 byte
255 testine, 63 settori/tracce, 8941 cilindri, totale 143638992 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x5ced3687

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    41,945,714    41,945,652  83 Linux
/dev/sdd2          41,945,715   143,637,164   101,691,450   5 Extended
/dev/sdd5          41,945,778    62,910,539    20,964,762  83 Linux
/dev/sdd6          62,910,603    69,529,319     6,618,717  82 Linux swap / Solaris
/dev/sdd7    *     69,529,383   143,637,164    74,107,782  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C49CD2749CD2608A" TYPE="ntfs" 
/dev/sdb1: LABEL="deposito" UUID="2e04034d-751f-41c2-a698-45ffeb2dedd8" TYPE="ext3" 
/dev/sdc1: UUID="858ce3a6-ff1a-4f98-b94e-310ad300e11f" TYPE="ext3" 
/dev/sdc2: UUID="065C96995C96835B" TYPE="ntfs" 
/dev/sdd1: UUID="c4993668-4f45-416f-899e-98e6a3931af5" TYPE="ext3" 
/dev/sdd5: LABEL="mail" UUID="f555eb93-0d60-4dcb-839c-1043f16af622" TYPE="ext3" 
/dev/sdd6: UUID="f47f4810-beb0-4a42-b23b-3e085871c255" TYPE="swap" 
/dev/sdd7: UUID="23ff03c8-0202-4af1-99ae-ac1c066d436e" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
usbfs on /dev/bus/usb/.usbfs type usbfs (rw,devmode=600,busmode=700,listmode=644)
usbfs on /proc/bus/usb/.usbfs type usbfs (rw,devmode=600,busmode=700,listmode=644)
/dev/sdc1 on /home type ext3 (rw,relatime)
/dev/sdb1 on /media/deposito type ext3 (rw,relatime)
/dev/sdd5 on /media/sdc5 type ext3 (rw,relatime)
none on /proc/bus/usb type usbfs (rw,devgid=125,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cionci/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cionci)


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
# kopt=root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c4993668-4f45-416f-899e-98e6a3931af5

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Windows 7 (hd1,0)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

title Windows 7 (hd1,1)
rootmoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 




=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c4993668-4f45-416f-899e-98e6a3931af5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=858ce3a6-ff1a-4f98-b94e-310ad300e11f /home           ext3    relatime        0       2
# /dev/sdb6
UUID=f47f4810-beb0-4a42-b23b-3e085871c255 none            swap    sw              0       0
UUID=2e04034d-751f-41c2-a698-45ffeb2dedd8 /media/deposito	ext3	relatime	0	2
UUID=f555eb93-0d60-4dcb-839c-1043f16af622 /media/sdc5		ext3	relatime	0	2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0


=================== sdd1: Location of files loaded by Grub: ===================


  15.3GB: boot/grub/menu.lst
  15.3GB: boot/grub/stage2
  15.3GB: boot/initrd.img-2.6.27-11-generic
  15.3GB: boot/initrd.img-2.6.27-14-generic
  15.3GB: boot/vmlinuz-2.6.27-11-generic
  15.3GB: boot/vmlinuz-2.6.27-14-generic
  15.3GB: initrd.img
  15.3GB: initrd.img.old
  15.3GB: vmlinuz
  15.3GB: vmlinuz.old

```

---

### Post by presence1960 on 2009-10-10
> **cionci said:**
> I think there's a problem in the script because Windows is only on the MBR of sda and sdc.

sda and sdb are Sata hdd. sdc and sdb are SCSI hdd.

Boot order is:
sdd
sdc
sda
sdb

From the grub console find /boot/grub/stage1 returns (hd0,0).
I would like to boot at least one of the Win 7 installations.

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdd1 and 
                       looks at sector 29897279 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdd. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: tipo di filesystem 'ext4' sconosciuto

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 82.3 GB, 82348277760 byte
255 testine, 63 settori/tracce, 10011 cilindri, totale 160836480 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0xb4419b89

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   160,826,714   160,826,652   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 640.1 GB, 640135028736 byte
255 testine, 63 settori/tracce, 77825 cilindri, totale 1250263728 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0xd83ec100

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,250,258,624 1,250,258,562  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 73.5 GB, 73543163904 byte
255 testine, 63 settori/tracce, 8941 cilindri, totale 143638992 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0xb814b814

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687  83 Linux
/dev/sdc2    *     40,965,750   143,637,164   102,671,415   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disco /dev/sdd: 73.5 GB, 73543163904 byte
255 testine, 63 settori/tracce, 8941 cilindri, totale 143638992 settori
Unità = settori di 1 * 512 = 512 byte
Identificativo disco: 0x5ced3687

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    41,945,714    41,945,652  83 Linux
/dev/sdd2          41,945,715   143,637,164   101,691,450   5 Extended
/dev/sdd5          41,945,778    62,910,539    20,964,762  83 Linux
/dev/sdd6          62,910,603    69,529,319     6,618,717  82 Linux swap / Solaris
/dev/sdd7    *     69,529,383   143,637,164    74,107,782  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C49CD2749CD2608A" TYPE="ntfs" 
/dev/sdb1: LABEL="deposito" UUID="2e04034d-751f-41c2-a698-45ffeb2dedd8" TYPE="ext3" 
/dev/sdc1: UUID="858ce3a6-ff1a-4f98-b94e-310ad300e11f" TYPE="ext3" 
/dev/sdc2: UUID="065C96995C96835B" TYPE="ntfs" 
/dev/sdd1: UUID="c4993668-4f45-416f-899e-98e6a3931af5" TYPE="ext3" 
/dev/sdd5: LABEL="mail" UUID="f555eb93-0d60-4dcb-839c-1043f16af622" TYPE="ext3" 
/dev/sdd6: UUID="f47f4810-beb0-4a42-b23b-3e085871c255" TYPE="swap" 
/dev/sdd7: UUID="23ff03c8-0202-4af1-99ae-ac1c066d436e" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
usbfs on /dev/bus/usb/.usbfs type usbfs (rw,devmode=600,busmode=700,listmode=644)
usbfs on /proc/bus/usb/.usbfs type usbfs (rw,devmode=600,busmode=700,listmode=644)
/dev/sdc1 on /home type ext3 (rw,relatime)
/dev/sdb1 on /media/deposito type ext3 (rw,relatime)
/dev/sdd5 on /media/sdc5 type ext3 (rw,relatime)
none on /proc/bus/usb type usbfs (rw,devgid=125,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cionci/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cionci)


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
# kopt=root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c4993668-4f45-416f-899e-98e6a3931af5

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c4993668-4f45-416f-899e-98e6a3931af5 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		c4993668-4f45-416f-899e-98e6a3931af5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Windows 7 (hd1,0)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

title Windows 7 (hd1,1)
rootmoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 




=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c4993668-4f45-416f-899e-98e6a3931af5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=858ce3a6-ff1a-4f98-b94e-310ad300e11f /home           ext3    relatime        0       2
# /dev/sdb6
UUID=f47f4810-beb0-4a42-b23b-3e085871c255 none            swap    sw              0       0
UUID=2e04034d-751f-41c2-a698-45ffeb2dedd8 /media/deposito	ext3	relatime	0	2
UUID=f555eb93-0d60-4dcb-839c-1043f16af622 /media/sdc5		ext3	relatime	0	2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0


=================== sdd1: Location of files loaded by Grub: ===================


  15.3GB: boot/grub/menu.lst
  15.3GB: boot/grub/stage2
  15.3GB: boot/initrd.img-2.6.27-11-generic
  15.3GB: boot/initrd.img-2.6.27-14-generic
  15.3GB: boot/vmlinuz-2.6.27-11-generic
  15.3GB: boot/vmlinuz-2.6.27-14-generic
  15.3GB: initrd.img
  15.3GB: initrd.img.old
  15.3GB: vmlinuz
  15.3GB: vmlinuz.old

```

If you look at the first section Windows is installed on MBR of all 4 disks!

here is what you need to do:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd3,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd3,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd3)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

You seem to have 2 Vista installs on sda1 and sdc2. I don't know if one is Vista or windows 7, at any rate when we get to the step of editing your windows entries in menu.lst you can edit the titles of the OS accordingly.

When rebooting enter BIOS and set the hard disk boot order to sdd, sda, sdc & sdb - exactly in that order! Save changes to CMOS and exit BIOS. Continue booting and when GRUB comes up choose Ubuntu. Open a terminal and run this command ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to this:

title Windows 7 (hd1,0)
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

title Windows 7 (hd1,1)
root[COLOR="Red"]m[/COLOR]overify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

and change it to:

```
title          Windows 7 (sda1)
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1 

title          Windows 7 (sdc2)
rootnoverify   (hd2,1)
map            (hd0) (hd2)
map            (hd2) (hd0)
chainloader    +1 
```

note the red "m" in your existing entry, be sure to change that to an "n".
Click Save on toolbar, close file and reboot. You should now be able to boot windows also.

---

### Post by cionci on 2009-10-10
I think there's a problem in the script, because Windows is not on the MBR of sdb and sdd.
grub starts normally booting from sdd, so I don't have to install it on the MBR of that disk.
I had already tested every menu.lst entry you have proposed directly using grub editing features at boot time, but system reboots everytime I point at a Windows 7 partition and I try to boot.

---

### Post by presence1960 on 2009-10-10
> **cionci said:**
> I think there's a problem in the script, because Windows is not on the MBR of sdb and sdd.
grub starts normally booting from sdd, so I don't have to install it on the MBR of that disk.
I had already tested every menu.lst entry you have proposed directly using grub editing features at boot time, but system reboots everytime I point at a Windows 7 partition and I try to boot.

well that is not a problem with the script, it is a problem with windows. That script only reports what you have installed & set up on your machine. It works just fine for everyone else.

If GRUB was pointing to the wrong place for windows when you choose windows you would get a GRUB error.  So the problem is with windows. Try using the recovery console of your windows disk to fix windows. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and use instructions for vista.

---

### Post by cionci on 2009-10-10
I was speaking about this part of RESULTS.txt where script states I have Windows on MBRs of all disks, but it's not true.
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd


```
I've grub in /dev/sdd MBR. /dev/sdb MBR is empty.
> **presence1960 said:**
> If GRUB was pointing to the wrong place for windows when you choose windows you would get a GRUB error.  
Exactly...but when I have no error system reboots ;)
> **presence1960 said:**
> So the problem is with windows. Try using the recovery console of your windows disk to fix windows. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and use instructions for vista.
But if I change boot order and I set a disk where Windows is on MBR as first disk, Windows starts fine. Both are fresh installs of Windows 7.

---

### Post by cionci on 2009-10-10
Yesterday I've tried to install Karmik to see if grub 2 was able to boot Windows.
I've installed Karmik on a partition of sdd and grub on sda MBR, but the result was the same: if I select the automatic generated Windows entry system reboots.

I don't think it's a generic grub issue, but maybe an issue related to my motherboard, an Abit AB9 Pro.

---

### Post by Mark Phelps on 2009-10-10
Just so you know, this is NOT an issue where GRUB just can't boot to Windows 7.  I have Windows 7 installed (along with other OSs) and GRUB boots to it just fine.

What is different, is that my Windows 7 install uses one partition not two. so, I suspect that the REAL problem is that GRUB simply can't handle the two-partition installed version of Windows 7.

---

### Post by presence1960 on 2009-10-10
it is not the boot info script. I have suggested using it on here literally close to a thousand times and have used it myself on my machine. It has never been wrong. 

In my experience helping others on here I have found that what people say they have on their machine and what is actually on there are many times far apart. I am not saying that is or is not the case with you, but the law of averages on the script's side.

That is why I insist on using the boot info script. It reports back what you have. To my knowledge you are the only one who has ever disputed it's results.

---

### Post by presence1960 on 2009-10-10
> **Mark Phelps said:**
> Just so you know, this is NOT an issue where GRUB just can't boot to Windows 7.  I have Windows 7 installed (along with other OSs) and GRUB boots to it just fine.

What is different, is that my Windows 7 install uses one partition not two. so, I suspect that the REAL problem is that GRUB simply can't handle the two-partition installed version of Windows 7.

+1 

It definitely is not GRUB! It is a Windows issue because if it were GRUB there would be a GRUB error reported. OP says it just reboots in a loop which is definitely a Windows issue. I would remove 1 Windows 7. I am curious why do you have 2 versions of the same OS anyhow?

At one point I had Windows 7, Ubuntu 9.04, Sabayon 4.1 & Mint all booting from Jaunty's GRUB on MBR.

Currently I only have Ubuntu 9.04 and XP Professional.

---

### Post by oldfred on 2009-10-10
I noticed this on a different thread and I think this is why many are having issues with grub booting win7 directly.

louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words

---

### Post by cionci on 2009-10-11
> **Mark Phelps said:**
> Just so you know, this is NOT an issue where GRUB just can't boot to Windows 7.  I have Windows 7 installed (along with other OSs) and GRUB boots to it just fine.

What is different, is that my Windows 7 install uses one partition not two. so, I suspect that the REAL problem is that GRUB simply can't handle the two-partition installed version of Windows 7.
No, the two partition are two different installations of Windows 7. The second Windows 7 installation on SCSI is the result of my tests: I was hoping that booting from SCSI to SCSI Windwos 7 could resolve the reboot issue I had with Windows 7 on SATA, but I was wrong.
I've tried with sda disconnected also, but I have a reboot anyway.

---

### Post by cionci on 2009-10-11
> **presence1960 said:**
> +1 

It definitely is not GRUB! It is a Windows issue because if it were GRUB there would be a GRUB error reported. OP says it just reboots in a loop which is definitely a Windows issue. 
Maybe I wasn't clear enough: system reboots if I choose a Windows entry, but grub starts again after reboot. The reboot is similar to that I obtain using reset button.
> **presence1960 said:**
> I would remove 1 Windows 7. I am curious why do you have 2 versions of the same OS anyhow?
I don't need two Windows 7, they are tests to see if I could get around the issue I was having with SATA installation by installing another Windows 7 on a SCSI partition. Disabling SATA controller lead to a reboot anyway if I try to boot from SCSI installation.
It's difficult to me to consider it a Windows only issue, because Windows starts without problem selecting its hard disk as first in the boot sequence.

To be clear: I was installing Windows 7 only for testing purpose. I'm an Ubuntu only user from 6.04 ;)
> **presence1960 said:**
> it is not the boot info script. I have suggested using it on here literally close to a thousand times and have used it myself on my machine. It has never been wrong. 
But if it states that I have Windows on MBR of /dev/sdd it's definitely wrong, because facts negate that: grub boot from that hard disk and did that for about two years ;)
> **presence1960 said:**
> In my experience helping others on here I have found that what people say they have on their machine and what is actually on there are many times far apart. I am not saying that is or is not the case with you, but the law of averages on the script's side.

That is why I insist on using the boot info script. It reports back what you have. To my knowledge you are the only one who has ever disputed it's results.
I helped a thousand of Ubuntu users in an italian forum and your it's surely the right way to help other people ;)
The funny implication of the incident is that many users I helped was having problems right with grub :D

---

### Post by cionci on 2009-10-11
> **oldfred said:**
> I noticed this on a different thread and I think this is why many are having issues with grub booting win7 directly.
Could you point me at that thread ? In the meanwhile I'll try to use search ;)

---

### Post by oldfred on 2009-10-11
this was the thread where louieb make the comment , with links to more info & picture:

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Somewhere else I saw someone with three windows partitions and only the window XP was primary. He had Vista and 7 in logical partitions but was able to boot all three from the XP partition. I think he was having the same issue of not able to get grub to boot vista & 7 because the boot loaders were moved to the XP partition.

---

