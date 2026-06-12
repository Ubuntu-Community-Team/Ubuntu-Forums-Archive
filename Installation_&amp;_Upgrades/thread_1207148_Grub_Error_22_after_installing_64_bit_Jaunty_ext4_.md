---
title: "Grub Error 22 after installing 64 bit Jaunty ext4 FS in a dual boot environment"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by tkrisz on 2009-07-07
Problem> can't load any OS due to Error 22 in GRUB.

Release notes speak about this problem, so i'm not surprised that it occurs, but can't fix it.
Now i have a / partition on /dev/sda2, a /home partition on /dev/sda3, both of them ext4, a swap on /dev/sda5.
I also have an XP partition on sdb1. And something on /dev/sda1, which is a surprise, i did not create that, i can't mount it.
I have no problem mounting the partitions after booting with the live CD.

I tried 2 things. 
Mounted the / partition and run grub-install as it was suggested in the release notes.
Also tried sudo grub, then finding stage1 and telling grub the info.

I noticed 1 more strange thing. I have no grub directorz at all in the /boot directory. Is that new in Jaunty?
Or i don't have grub at all?

---

### Post by ranch hand on 2009-07-07
Boot from your live CD then run;
```

sudo grub
at
grub> find stage1

```
past results.

This really should not be happening but it does on occasion.

While on your live CD take a look in your Jaunty / partition (should come up in the Home folder of the Live CD) and check your /boot/grub/menu.lst and make sure that Jaunty is on there and see if your "off brand" OS is there.

We should be able to get you booted to Jaunty and then fix the other.

---

### Post by presence1960 on 2009-07-07
right from the GRUB manual (get it here : [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)  )

```
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

```

to avoid guessing and get a better picture of your setup & boot info Boot the Live CD and download the Boot Info Script 0.32 to the desktop from here : [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)

Once downloaded open a termainal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. paste the contents of the file back here. When text has been pasted here highlight all text then click # on the toolbar to place Code tags around the text. Once we get a look at that we can try to get you up & running.

---

### Post by ranch hand on 2009-07-07
That is a good idea but I think that the probleem lies with MS screwing grub around.  Of coarse that should be shown by the script.

I have had problems with it through a live CD though.

---

### Post by tkrisz on 2009-07-08
Here's the result:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cf2bc

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,903,794     3,903,732   5 Extended
/dev/sda5                 126     3,903,794     3,903,669  82 Linux swap / Solaris
/dev/sda2    *      3,903,795    33,206,354    29,302,560  83 Linux
/dev/sda3          33,206,355   423,826,829   390,620,475  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa152a152

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,055,594   160,055,532   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="0aa0bd27-ebc8-42de-8f15-dab8122ac23c" TYPE="ext4" 
/dev/sda3: UUID="f8040743-36bf-499a-b639-d0a2ebac4915" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="ce123ca0-3250-4873-ad03-be494c90025e" 
/dev/sdb1: UUID="C8F0F50CF0F5018C" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
# kopt=root=UUID=0aa0bd27-ebc8-42de-8f15-dab8122ac23c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0aa0bd27-ebc8-42de-8f15-dab8122ac23c

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		0aa0bd27-ebc8-42de-8f15-dab8122ac23c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0aa0bd27-ebc8-42de-8f15-dab8122ac23c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		0aa0bd27-ebc8-42de-8f15-dab8122ac23c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=0aa0bd27-ebc8-42de-8f15-dab8122ac23c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		0aa0bd27-ebc8-42de-8f15-dab8122ac23c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional - magyar
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=0aa0bd27-ebc8-42de-8f15-dab8122ac23c /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=f8040743-36bf-499a-b639-d0a2ebac4915 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=ce123ca0-3250-4873-ad03-be494c90025e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   3.7GB: boot/grub/menu.lst
   2.0GB: boot/grub/stage2
   3.6GB: boot/initrd.img-2.6.28-11-generic
   3.8GB: boot/vmlinuz-2.6.28-11-generic
   3.6GB: initrd.img
   3.8GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional - magyar"  /sos

```

---

### Post by presence1960 on 2009-07-08
Ok, here is what I see. Your sda1 is an extended partition which contains your sda5 swap partition. No problem there. It looks like you installed GRUB to the MBR of both your drives. So when you boot and get the error 22 this means that your sdb HDD with windows is booting first. Think that thru for a minute. At the very top of your results it tells you that GRUB is installed on MBR of sda and looks to partition 2 of same drive for menu.lst- that is perfect. But the next line says GRUB is installed on MBR of sdb and looks on boot drive #2 for menu.lst- this is the problem. First it is looking on boot drive #2 for partition #6. sdb only has 1 partition so it is looking on partition 6 of sda. There is no such partition. Here is what you need to do. It is a two step process. You have to restore the windows bootloader to MBR of  sdb, because when you put GRUB on that disk you overwrote the windows bootloader. First go into BIOS when you boot and make sure your sdb HDD (81.9 GB) with Windows on it is set to boot first in the boot order of HDD. Then boot from the windows CD and follow this : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  _**Very important that sdb boots first in BIOS. If it doesn't the bootloader will try to write to your Ubuntu disk.**_

When finished reboot and windows should boot up for you. Then restart and go into BIOS again and put your sda HDD (250 GB) with Ubuntu as first boot in the boot order of HDD. You should be good to go , GRUB will take over when you boot. I checked your menu.lst on sda and your windows entry look perfect so you should be able to boot both OSs after this.

---

### Post by tkrisz on 2009-07-09
Thank you very much.
Meanwhile i got help on IRC as well, and they told me the 2nd step. Linux and XP is working perfectly now. As i see, the only problem that can happen is if i skip the 1st step  and remove the drive with my Ubuntu from the computer, i will have to do step 1 to use my Windows only computer. That is not in my plans, so i save that procedure.

---

### Post by justjuss on 2009-07-10
Hey Ranch Hand, Can you help me too? I'm a newbie but I've been installing a dual boot several times on my vaio laptop and with much success but this time &#65279;[SIZE=3] I just installed ubuntu8.04 on a partition next to my Win XPPro OS. How do I uninstall? My trouble is that When the 1st screen comes up and gives me the choice of which OS I want to load I cannot choose XP. It's there but it keeps switching my curser back to Ubuntu. I've never had this happen in all my dual boot installs.[/SIZE]
justJuss




> **ranch hand said:**
> Boot from your live CD then run;
```

sudo grub
at
grub> find stage1

```past results.

This really should not be happening but it does on occasion.

While on your live CD take a look in your Jaunty / partition (should come up in the Home folder of the Live CD) and check your /boot/grub/menu.lst and make sure that Jaunty is on there and see if your "off brand" OS is there.

We should be able to get you booted to Jaunty and then fix the other.

---

