---
title: "Getting GRUB to recognize a Windows installation on a RAID0 array..."
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by gogogadgetearl on 2009-03-10
I have 4 SATA hard drives:
[LIST]
[*]2 x 80GB in RAID0 [Windows]
[*]1 x 320GB [media storage]
[*]1 x 160GB [hopefully Kubuntu]
[/LIST]
The RAID controller is an NVIDIA RAID from an ASUS A8N32-SLI motherboard.

I've read up on the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"), but it's geared more for installing Ubuntu *onto* the RAID, whereas I'm installing Kubuntu on a separate HDD and I only need GRUB to recognize the RAID for my Windows installation.  I'm still somewhat of a newbie, so I couldn't exactly figure out how to configure GRUB given the instructions from the FakeRaidHowTo.

I ran the Ubiquity installer from the 8.10 Live CD, installed Kubuntu onto the spare 160GB HDD, but now I get an "Error 21" in GRUB.

Any help would be incredible.  Thanks!

---

### Post by Neo_The_User on 2009-03-10
```

sudo update-grub

```

---

### Post by gogogadgetearl on 2009-03-10
> **Neo_The_User said:**
> ```

sudo update-grub

```

From where?  The Live CD?  Would I need to CHROOT into my Kubuntu installation first?

---

### Post by Neo_The_User on 2009-03-10
> **gogogadgetearl said:**
> From where?  The Live CD?  Would I need to CHROOT into my Kubuntu installation first?

Eh after reading your first post again...

GRUB Error 21 means it can't find the kernel.

Not from the livecd. HDD if you can.

---

### Post by gogogadgetearl on 2009-03-10
> **Neo_The_User said:**
> Eh after reading your first post again...

GRUB Error 21 means it can't find the kernel.

Not from the livecd. HDD if you can.

No go on booting from the HDD.  I can't yet get past the Error 21.

---

### Post by Neo_The_User on 2009-03-10
You try accessing the linux partition in Windows, it asks you if you want to format it. Choose yes, all data on linux partition is erased. Choose no, you can't read or write to the linux partition so you're going to have to use the Ubuntu LiveCD and edit menu.lst by hand located on your hard drive.

---

### Post by gogogadgetearl on 2009-03-10
> **Neo_The_User said:**
> You try accessing the linux partition in Windows, it asks you if you want to format it. Choose yes, all data on linux partition is erased. Choose no, you can't read or write to the linux partition so you're going to have to use the Ubuntu LiveCD and edit menu.lst by hand located on your hard drive.

Can't access any OS installed on the HDD.  Looks like my only option is through the Live CD.

So, when I edit menu.lst, what device do I list as my Windows RAID, and what devices do I list as my Kubuntu HDD?

On that Kubuntu installation, the /boot/grub/device.map reads:
```

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

```

I know I only have 4 HDDs in there, so 2 of those should be recognized as a RAID, and another should be recognized as my Kubuntu installation.

The abridged version of /boot/grub/menu.lst on my HDD Kubuntu installation reads:
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		329bb130-cce6-4ca2-a1c7-0d05a0de6f19
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=329bb130-cce6-4ca2-a1c7-0d05a0de6f19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		329bb130-cce6-4ca2-a1c7-0d05a0de6f19
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=329bb130-cce6-4ca2-a1c7-0d05a0de6f19 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		329bb130-cce6-4ca2-a1c7-0d05a0de6f19
kernel		/boot/memtest86+.bin
quiet

```

Following the FakeRaidHowTo, I intalled dmraid on the Live CD boot (not on the Kubuntu HDD installation) and I was able to see /dev/mapper/nvidia_fcbhfaee -- which seemed to be the Windows RAID.  Unfortunately, when I tried to CHROOT into my Kubuntu HDD intallation ('sudo chroot /media/disk' from the Live CD boot) and install dmraid there, the 'apt-get update' command fails at 96% with "Could not set non-blocking flag Bad file descriptor E: Method http has died unexpectedly!"  Out of hope, I tried 'apt-get install -y dmraid' anyway, but it got all kinds of permission denied errors.

Basically, I just want to fix GRUB so I can boot into Windows or Kubuntu.  Any ideas?

---

### Post by Neo_The_User on 2009-03-10
I'm out of ideas.

---

### Post by meierfra. on 2009-03-10
You need to install grub of the MBR of the ubuntu drive and then set your bios to boot from the Ubuntu drive:

Boot the LiveCD, open a terminal and type:

```
sudo grub
```

and then at the "grub" prompt:


```
 find /boot/grub/menu.lst
```


This will return "(hdX,Y)" where "X" and "Y" are some numbers, for example (hd2,0).

Still at the grub prompt:

```
root (hdX,Y)
setup (hdX)
quit
```
(where "X" and "Y" need to be replaced by the numbers returned by "find /boot/grub/menu.lst")

Reboot (with the bios set to boot from the Ubuntu drive) and hope for the best. 

**If this did not work:**

In order to get a clearer picture of your setup, boot from your LiveCD, download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by Ceza on 2009-03-10
Hello,
   I'm a nub so take what I say with a grain of salt but the first thing I suggest you do is to unplug the media storage drive. I know you shouldn't need to and if you know what you are doing then great but I myself tried this an nuked my storage/backup drive by accident. Fact is you don't need it plugged in while messing with this anyway and it will eliminate confusion to be sure which other drives you are on.

Next I would make sure you have any important data on your Windows install backed up too. 

As I myself failed at this I will tell you that I finally gave up and decided my best option was to use the BIOS to select which drive to boot from. It is sure nice to be able to select it from a prompt and I would commend you if you figure it out (followed by asking you how you did it) but if you can't it is easy to select your boot drive in the BIOS and bypass the problem completely.

It sucked when I lost all my data while playing with this and would hate for you to experience the same. Good luck to you! :D

---

### Post by gogogadgetearl on 2009-03-11
> **meierfra. said:**
> 
...
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.


```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #4 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f6eaf93

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   312,600,575   312,598,528   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b27f806

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   178,289,369   178,287,322   7 HPFS/NTFS
/dev/sdb2         178,289,370   312,592,769   134,303,400  83 Linux

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb2 ends after the last sector of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf2432e2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9af49af4

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    97,659,134    97,659,072  83 Linux
/dev/sdd2          97,659,135   312,576,704   214,917,570   5 Extended
/dev/sdd5          97,659,198   117,258,434    19,599,237  82 Linux swap / Solaris
/dev/sdd6         117,258,498   312,576,704   195,318,207  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sdc1: UUID="DEF45CB8F45C949D" LABEL="Cold Storage" TYPE="ntfs" 
/dev/sdd1: UUID="329bb130-cce6-4ca2-a1c7-0d05a0de6f19" TYPE="ext3" 
/dev/sdd5: UUID="f6c5f34b-5c8d-413d-94bf-792fc2df8acd" TYPE="swap" 
/dev/sdd6: UUID="d0338b8f-9f55-4e25-9804-0def63050401" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/mapper/nvidia_fcbhfaae1: UUID="1C6CF6436CF6176C" TYPE="ntfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdd1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1 on /media/Cold Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev on /media/disk/dev type none (rw,bind)
proc on /media/disk/proc type proc (rw)
sys on /media/disk/sys type sysfs (rw)


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
timeout		30

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
# kopt=root=UUID=329bb130-cce6-4ca2-a1c7-0d05a0de6f19 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=329bb130-cce6-4ca2-a1c7-0d05a0de6f19

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

title		Windows Vista SP1
rootnoverify	(hd0,0)
makeactive
chainloader +1

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		329bb130-cce6-4ca2-a1c7-0d05a0de6f19
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=329bb130-cce6-4ca2-a1c7-0d05a0de6f19 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		329bb130-cce6-4ca2-a1c7-0d05a0de6f19
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=329bb130-cce6-4ca2-a1c7-0d05a0de6f19 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		329bb130-cce6-4ca2-a1c7-0d05a0de6f19
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=329bb130-cce6-4ca2-a1c7-0d05a0de6f19 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd6
UUID=d0338b8f-9f55-4e25-9804-0def63050401 /home           ext3    relatime        0       2
# /dev/sdd5
UUID=f6c5f34b-5c8d-413d-94bf-792fc2df8acd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


  28.4GB: boot/grub/menu.lst
  28.4GB: boot/grub/stage2
  28.5GB: boot/initrd.img-2.6.27-7-generic
  28.5GB: boot/vmlinuz-2.6.27-7-generic
  28.5GB: initrd.img
  28.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  01 00 20 20 20 20 20 20  20 20 3c 53 65 74 4b 65  |..        <SetKe|
00000010  79 56 61 6c 75 65 20 70  61 74 68 3d 22 5c 52 65  |yValue path="\Re|
00000020  67 69 73 74 72 79 5c 4d  61 63 68 69 6e 65 5c 43  |gistry\Machine\C|
00000030  4f 4d 50 4f 4e 45 4e 54  53 5c 57 69 6e 6e 65 72  |OMPONENTS\Winner|
00000040  73 5c 78 38 36 5f 31 31  64 32 37 30 32 36 31 61  |s\x86_11d270261a|
00000050  38 61 37 36 65 63 33 64  65 61 32 62 38 35 65 33  |8a76ec3dea2b85e3|
00000060  33 34 61 30 64 30 5f 33  31 62 66 33 38 35 36 61  |34a0d0_31bf3856a|
00000070  64 33 36 34 65 33 35 5f  6e 6f 6e 65 5f 30 31 33  |d364e35_none_013|
00000080  31 34 36 35 33 39 38 66  31 32 33 62 30 22 20 6e  |1465398f123b0" n|
00000090  61 6d 65 3d 22 22 20 74  79 70 65 3d 22 30 78 30  |ame="" type="0x0|
000000a0  30 30 30 30 30 30 31 22  20 65 6e 63 6f 64 69 6e  |0000001" encodin|
000000b0  67 3d 22 62 61 73 65 36  34 22 20 76 61 6c 75 65  |g="base64" value|
000000c0  3d 22 4e 67 41 75 41 44  41 41 41 41 41 3d 22 2f  |="NgAuADAAAAA="/|
000000d0  3e 0a 20 20 20 20 20 20  20 20 3c 53 65 74 4b 65  |>.        <SetKe|
000000e0  79 56 61 6c 75 65 20 70  61 74 68 3d 22 5c 52 65  |yValue path="\Re|
000000f0  67 69 73 74 72 79 5c 4d  61 63 68 69 6e 65 5c 43  |gistry\Machine\C|
00000100  4f 4d 50 4f 4e 45 4e 54  53 5c 57 69 6e 6e 65 72  |OMPONENTS\Winner|
00000110  73 5c 78 38 36 5f 31 31  64 32 37 30 32 36 31 61  |s\x86_11d270261a|
00000120  38 61 37 36 65 63 33 64  65 61 32 62 38 35 65 33  |8a76ec3dea2b85e3|
00000130  33 34 61 30 64 30 5f 33  31 62 66 33 38 35 36 61  |34a0d0_31bf3856a|
00000140  64 33 36 34 65 33 35 5f  6e 6f 6e 65 5f 30 31 33  |d364e35_none_013|
00000150  31 34 36 35 33 39 38 66  31 32 33 62 30 5c 36 2e  |1465398f123b0\6.|
00000160  30 22 20 6e 61 6d 65 3d  22 22 20 74 79 70 65 3d  |0" name="" type=|
00000170  22 30 78 30 30 30 30 30  30 30 31 22 20 65 6e 63  |"0x00000001" enc|
00000180  6f 64 69 6e 67 3d 22 62  61 73 65 36 34 22 20 76  |oding="base64" v|
00000190  61 6c 75 65 3d 22 4e 67  41 75 41 44 41 41 4c 67  |alue="NgAuADAALg|
000001a0  41 32 41 44 41 41 4d 41  41 77 41 43 34 41 4d 51  |A2ADAAMAAwAC4AMQ|
000001b0  41 32 41 44 63 41 4d 41  41 34 41 41 41 41 22 2f  |A2ADcAMAA4AAAA"/|
000001c0  3e 0a 20 20 20 20 20 20  20 20 3c 53 65 74 4b 65  |>.        <SetKe|
000001d0  79 56 61 6c 75 65 20 70  61 74 68 3d 22 5c 52 65  |yValue path="\Re|
000001e0  67 69 73 74 72 79 5c 4d  61 63 68 69 6e 65 5c 43  |gistry\Machine\C|
000001f0  4f 4d 50 4f 4e 45 4e 54  53 5c 57 69 6e 6e 65 72  |OMPONENTS\Winner|
00000200

Unknown BootLoader  on sdb1

00000000  01 00 33 38 35 36 61 64  33 36 34 65 33 35 7e 78  |..3856ad364e35~x|
00000010  38 36 7e 7e 36 2e 30 2e  36 30 30 31 2e 32 31 32  |86~~6.0.6001.212|
00000020  33 2e 39 5f 65 61 35 39  35 34 35 39 65 66 37 39  |3.9_ea595459ef79|
00000030  32 33 36 66 22 20 74 79  70 65 3d 22 30 78 30 30  |236f" type="0x00|
00000040  30 30 30 30 30 33 22 20  65 6e 63 6f 64 69 6e 67  |000003" encoding|
00000050  3d 22 62 61 73 65 36 34  22 20 76 61 6c 75 65 3d  |="base64" value=|
00000060  22 55 51 41 41 41 41 45  41 41 41 42 51 59 57 4e  |"UQAAAAEAAABQYWN|
00000070  72 59 57 64 6c 58 7a 52  66 5a 6d 39 79 58 30 74  |rYWdlXzRfZm9yX0t|
00000080  43 4f 54 51 34 4e 6a 45  77 66 6a 4d 78 59 6d 59  |COTQ4NjEwfjMxYmY|
00000090  7a 4f 44 55 32 59 57 51  7a 4e 6a 52 6c 4d 7a 56  |zODU2YWQzNjRlMzV|
000000a0  2b 65 44 67 32 66 6e 34  32 4c 6a 41 75 4e 6a 41  |+eDg2fn42LjAuNjA|
000000b0  77 4d 53 34 79 4d 54 49  7a 4c 6a 6b 30 4f 44 59  |wMS4yMTIzLjk0ODY|
000000c0  78 4d 43 30 79 4d 7a 5a  66 62 6d 56 31 64 48 4a  |xMC0yMzZfbmV1dHJ|
000000d0  68 62 46 39 48 52 46 49  79 22 2f 3e 0a 20 20 20  |hbF9HRFIy"/>.   |
000000e0  20 20 20 20 20 3c 53 65  74 4b 65 79 56 61 6c 75  |     <SetKeyValu|
000000f0  65 20 70 61 74 68 3d 22  5c 52 65 67 69 73 74 72  |e path="\Registr|
00000100  79 5c 4d 61 63 68 69 6e  65 5c 43 4f 4d 50 4f 4e  |y\Machine\COMPON|
00000110  45 4e 54 53 5c 43 61 6e  6f 6e 69 63 61 6c 44 61  |ENTS\CanonicalDa|
00000120  74 61 5c 44 65 70 6c 6f  79 6d 65 6e 74 73 5c 61  |ta\Deployments\a|
00000130  38 33 30 63 39 37 38 31  65 37 2e 2e 38 33 63 37  |830c9781e7..83c7|
00000140  61 33 64 32 31 64 61 5f  33 31 62 66 33 38 35 36  |a3d21da_31bf3856|
00000150  61 64 33 36 34 65 33 35  5f 36 2e 30 2e 36 30 30  |ad364e35_6.0.600|
00000160  31 2e 31 38 30 39 36 5f  35 37 33 65 62 33 32 36  |1.18096_573eb326|
00000170  63 34 61 66 33 64 35 34  22 20 6e 61 6d 65 3d 22  |c4af3d54" name="|
00000180  69 21 43 42 53 5f 70 61  63 6b 61 67 65 5f 34 5f  |i!CBS_package_4_|
00000190  66 6f 72 5f 6b 62 39 34  38 36 31 30 7e 33 31 62  |for_kb948610~31b|
000001a0  66 33 38 35 36 61 64 33  36 34 65 33 35 7e 78 38  |f3856ad364e35~x8|
000001b0  36 7e 7e 36 2e 30 2e 36  30 30 31 2e 32 31 32 33  |6~~6.0.6001.2123|
000001c0  2e 39 5f 39 32 33 39 65  62 35 64 66 33 61 38 34  |.9_9239eb5df3a84|
000001d0  33 61 31 22 20 74 79 70  65 3d 22 30 78 30 30 30  |3a1" type="0x000|
000001e0  30 30 30 30 33 22 20 65  6e 63 6f 64 69 6e 67 3d  |00003" encoding=|
000001f0  22 62 61 73 65 36 34 22  20 76 61 6c 75 65 3d 22  |"base64" value="|
00000200

Unknown BootLoader  on sdb2




```

---

### Post by meierfra. on 2009-03-11
Grub seems to be correctly installed in the MBR of the Ubuntu partition.
Did you set the bios to boot from  Ubuntu drive? 
What happens when you boot from the Ubuntu drive? Does the Grub menu appear?  Do you get any error messages?

---

### Post by addohm on 2009-09-17
> **meierfra. said:**
> Grub seems to be correctly installed in the MBR of the Ubuntu partition.
Did you set the bios to boot from  Ubuntu drive? 
What happens when you boot from the Ubuntu drive? Does the Grub menu appear?  Do you get any error messages?

That is not possible.  An Nvidia fake raid is only loaded by driver\module.  The bios can only be set to one drive, or the other, but neither will matter on a raid 0 configuration.

---

