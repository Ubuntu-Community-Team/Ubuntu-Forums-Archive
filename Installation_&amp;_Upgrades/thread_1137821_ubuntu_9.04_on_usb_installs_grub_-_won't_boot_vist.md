---
title: "ubuntu 9.04 on usb installs grub - won't boot vista without usb!!"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by ezertuchev on 2009-04-25
I've just installed ubuntu 9.04 on a USB stick to run on my laptop (I'd already installed ubuntu since 8.04 on my desktop and I love it). My laptop came pre-installed with vista. Now the issue is that GRUB is on the USB stick, so if I don't have it plugged in, I can't load vista at all!!

Since I'm a bit linux-challenged, I thought (or hoped) that by installing ubuntu on the usb stick, GRUB would not be an issue, and I could just turn on the computer and have it load vista as always; and whenever I wanted to run ubuntu, I would just press F10 and boot directly from the USB.

Can I fix things so I can do just that? or would I have to fix the MBR for vista and install ubuntu from scratch?

HELP!

Eduardo

---

### Post by meierfra. on 2009-04-26
To fix your problem, you need to install grub to the MBR of the external drive and and repair the MBR of the internal drive.
Open a terminal in Ubuntu (Applications->Accessories->Terminal

** Step 1 Install Grub to the MBR of the external drive.**

```

sudo grub

```

and at the "grub>" prompt.

```

 find /boot/grub/stage2

```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)
(if it returned 'file not found', try  'find /grub/stage2' and  'find /stage2' )

Still at the "grub>" prompt:

```

root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")


** Step 2) Install a Windows Style MBR to the internal drive: **


```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

(Here "/dev/sda" needs to be the device name of your internal drive. It
probably is "/dev/sda" but you should double check via "sudo fdisk -lu")


**Step 3  Edit Menu.lst so that you can boot to Vista from the Grub menu.**

Open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Look for the item which looks something like

title Windows Vista
root (hd0,Z)
savedefault
chainloader +1

where Z is some number.

Replace the line

root (hd0,Z)


by the the three lines

root (hd1,Z)
map (hd0) (hd1)
map (hd1) (hd0)

Save the file.

Set your Bios to boot from the USB drive.  If the USB drive is not plugged in, you should boot directly into Vista. But if  USB drive is plugged in, you should get the Grub menu, which lets you boot into Vista and Ubuntu.


If you need additional help, post the output of

```
sudo fdisk -lu
```

---

### Post by Jammanuser on 2009-04-26
Is it possible that your Vista drive is not first in the boot sequence in the BIOS? To enter your BIOS, at startup hit F2, Del, or similar (it should show what key you need to press at the first splash screen you get to right after turning on your computer). Then, simply look around for something called "Boot sequence", "Boot Order", and other such entries. Select that, and you should be able to tell whether or not your Vista drive is first in the boot sequence. If it is not, then simply move it all the way up by pushing the "U" key. And then save the changes, and exit the BIOS.

-Jam man

:guitar:

---

### Post by ezertuchev on 2009-05-02
Thanks for your replies!

As it turns out, however, I got stuck at

sudo apt-get install lilo

The terminal gives the following message

sudo apt-get install lilo
[sudo] password for edux: 
E: Can't block /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Impossible to block administration directory (/var/lib/dpkg/), is another process using it?

(Sorry if that's not entirely accurate, I had to translate, since my ubuntu is in spanish)

I tried installing lilo from synaptic, but it gives the same error msg.

Jammanuser, I've already tried that, but anyway it still calls for grub.

Thanks again for your replies.

Eduardo

---

### Post by meierfra. on 2009-05-02
> E: Can't block /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Impossible to block administration directory (/var/lib/dpkg/), is another process using it?


Was the "update manager" running at the same time? Or Synaptics?  
Only one process at a time is  allowed to install programs. So  wait until the other process has finished and  close it. 

If this did not solve the problem, reboot and try again.

---

### Post by ezertuchev on 2009-05-02
Thank you, Meierfra
 
I managed to install lilo, had to change linux to english to do that.
 
I fixed the Vista MBR and now it's working well.
 
However, I am unable to boot from the ubuntu USB. I get a message upon startup that says "No active partition", and then Vista starts up.
 
I changed the boot order from the bios, to boot first from the USB, but all I get is that message.
 
I have no problem in installing Ubuntu 9.04 again, but I don't know how to avoid getting into the same problem again. Any ideas?
 
Thanks again,
 
Eduardo

---

### Post by meierfra. on 2009-05-02
> However, I am unable to boot from the ubuntu USB. I get a message upon startup that says "No active partition", 

Some bios refuse to  boot a hard drive without an active primary partition partition. So you need to set the boot flag to one of the first four partitions on your external drive:

```
sudo sfdisk -A1 /dev/sdb
```

(this assumes that your external drive is /dev/sdb.  Also if you don't have  a /dev/sdb1 partition,  you might have to use "-A2" in place of "-A1" (or "-A3" or "-A4")

---

### Post by ezertuchev on 2009-05-03
Thanks Meierfra,

As it turns out, however, it still won't boot ubuntu from the USB stick, says operating system not found.

I checked the USB Stick partitions with the sudo fdisk -lu command and now the main partition shows up with an "*" on it, as does my linux partition on my other computer (the one I used to check it), but the laptop refuses to boot from it.

I've thought about using live USB, but I'd rather have a complete instalation on the USB stick, so I can have my own operating system while my wife continues to use Vista.

Any ideas??

Thanks again!

Eduardo

---

### Post by meierfra. on 2009-05-03
Maybe your  bios have a problem with booting a USB drive.
But  let's first check whether grub is setup correctly:

Make sure your USB drive is plugged in. Then boot from the Ubuntu Live CD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by ezertuchev on 2009-05-03
Here it is:

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb3a2cc7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,033,054    20,032,992   7 HPFS/NTFS
/dev/sda2          20,033,055   488,395,119   468,362,065   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5e2da15

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    14,892,254    14,892,192  83 Linux
/dev/sdc2          14,892,255    15,647,309       755,055   5 Extended
/dev/sdc5          14,892,318    15,647,309       754,992  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0298E5CD98E5BEF3" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda2: UUID="3C1E48751E482A6A" TYPE="ntfs" 
/dev/sdc1: UUID="f9b8a92f-8acb-4a05-a75b-dde535fc8750" TYPE="ext3" 
/dev/sdc5: UUID="deb56ab0-1156-484e-a9b5-fc35cee46022" TYPE="swap" 

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
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=f9b8a92f-8acb-4a05-a75b-dde535fc8750 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f9b8a92f-8acb-4a05-a75b-dde535fc8750

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f9b8a92f-8acb-4a05-a75b-dde535fc8750
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f9b8a92f-8acb-4a05-a75b-dde535fc8750 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f9b8a92f-8acb-4a05-a75b-dde535fc8750
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f9b8a92f-8acb-4a05-a75b-dde535fc8750 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f9b8a92f-8acb-4a05-a75b-dde535fc8750
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=f9b8a92f-8acb-4a05-a75b-dde535fc8750 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=deb56ab0-1156-484e-a9b5-fc35cee46022 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   7.4GB: boot/grub/menu.lst
    .9GB: boot/grub/stage2
    .9GB: boot/initrd.img-2.6.28-11-generic
   6.9GB: boot/vmlinuz-2.6.28-11-generic
    .9GB: initrd.img
   6.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by meierfra. on 2009-05-03
It seems you installed lilo the external drive, overwriting grub.  Your items for Windows on menu.lst are also slightly off.  So try this:


Boot from the Ubuntu live cd. Open a terminal and do

```
sudo grub
```

and at the "grub>" prompt:

```
root (hd2,1)  (edit: I meant to say (hd2,0)"
setup (hd2)
quit
```


Reboot  with the bios set to boot from the USB drive. 
Hopefully you will get the grub menu and are able to boot into Ubuntu.

Once you booted into ubuntu you need to edit menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

Change


title        Windows Vista (loader)
rootnoverify    [COLOR="Red"](hd0,0) [/COLOR]
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1


to

title        Windows Vista (loader)
rootnoverify    [COLOR="Red"](hd1,0)[/COLOR]
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1

and 


title        Windows Vista (loader)
rootnoverify    [COLOR="Red"](hd0,1)[/COLOR]
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1


to

title        Windows Vista (loader)
rootnoverify    [COLOR="Red"](hd1,1)[/COLOR]
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1


Save the file and reboot. See whether you can boot into Vista from the Grub menu.  Do you have two different Vista? Or is one of the Windows 7? 

If you aren't able to boot into Ubuntu or Vista, report any error message you got.

---

### Post by ezertuchev on 2009-05-03
I get an error on the first line:

```
Error 21: Selected disk does not exist
```

and when I run 

```
find /boot/grub/stage2
```

it returns (hd1,0)

---

### Post by ezertuchev on 2009-05-03
Just one quick question, though...

This procedure won't bring me back to square one? I mean, now I can boot vista as before (without GRUB) whenever the USB Stick is not plugged in. I don't want to have GRUB again, I just want to boot from the USB stick when choosing to do so from the bios.

I hope the question is clear, I don't quite know how to phrase it.

Thanks!!

Eduardo

---

### Post by ezertuchev on 2009-05-03
By the way, regarding the Vista thing, it's not that I have two vista partitions; one of them has the Gateway recovery system, while the other actually holds the Vista OS. Whenever I want to reset my system, I just run a program that lets me boot from the recovery partition and brings things back to factory settings.

---

### Post by meierfra. on 2009-05-03
OK  Try


```
sudo grub
root (hd1,0)
setup (hd1)
quit
```


> This procedure won't bring me back to square one? I 

No. It installs grub to the MBR of the USB drive. So it won't interfere with booting from the internal drive.

---

### Post by meierfra. on 2009-05-03
Sorry, I seem to be sleeping. I just fixed a typo in my previous post.

(it needs to be "root (hd1,0)")

---

### Post by ezertuchev on 2009-05-03
I get the following error:

No boot signature in partition

```
Intel UNDI, PXE-2.1 (build 082)
Copyright (C) 1997-2000 Intel Corporation

For Realtek RLT8100E/8101E Fast Ethernet Network Adapter v1.02 (060529)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
Operating System not found
```

does this mean that its trying to boot from the LAN???

My laptop, upon startup, asks to press F10 for boot options, and then displays the following Boot Menu:

```
2. USB HDD: LG USB Drive-(USB 2.0)
4. IDE CD: HL-DT-ST DVDRAM GSA-T20N-(
5. SATA HDD: WDC WD2500BEVS-22UST0-(S1)
7. Boot to LAN: Realtek Boot Agent
```

I'm obviously choosing the #2 option USB HDD (it highlights when chosen), and pressing enter.

Am I doing something wrong???

---

### Post by meierfra. on 2009-05-03
Did you use "root (hd0,1), setup (hd1)"?  Did you get any error message after "setup (hd1)"?

Could you run the boot_info_script again, so that I can see whether grub is  now correctly configured. 


> does this mean that its trying to boot from the LAN???
Maybe.  

You also don't have  a "/dev/sdb" (only  "/dev/sda" and "/dev/sdc") 

So maybe your hard drives are not plugged in correctly or  some setting in your bios are messed up.  If your change some setting in your bios, make sure to record the original setting before hand.

---

### Post by ezertuchev on 2009-05-03
Here's the output of boot_info_script again

```
============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb3a2cc7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,033,054    20,032,992   7 HPFS/NTFS
/dev/sda2          20,033,055   488,395,119   468,362,065   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb5e2da15

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    14,892,254    14,892,192  83 Linux
/dev/sdc2          14,892,255    15,647,309       755,055   5 Extended
/dev/sdc5          14,892,318    15,647,309       754,992  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0298E5CD98E5BEF3" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda2: UUID="3C1E48751E482A6A" TYPE="ntfs" 
/dev/sdc1: UUID="f9b8a92f-8acb-4a05-a75b-dde535fc8750" TYPE="ext3" 
/dev/sdc5: UUID="deb56ab0-1156-484e-a9b5-fc35cee46022" TYPE="swap" 

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
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
timeout        10

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
# kopt=root=UUID=f9b8a92f-8acb-4a05-a75b-dde535fc8750 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f9b8a92f-8acb-4a05-a75b-dde535fc8750

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f9b8a92f-8acb-4a05-a75b-dde535fc8750
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f9b8a92f-8acb-4a05-a75b-dde535fc8750 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f9b8a92f-8acb-4a05-a75b-dde535fc8750
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f9b8a92f-8acb-4a05-a75b-dde535fc8750 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f9b8a92f-8acb-4a05-a75b-dde535fc8750
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=f9b8a92f-8acb-4a05-a75b-dde535fc8750 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=deb56ab0-1156-484e-a9b5-fc35cee46022 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   7.4GB: boot/grub/menu.lst
    .9GB: boot/grub/stage2
    .9GB: boot/initrd.img-2.6.28-11-generic
   6.9GB: boot/vmlinuz-2.6.28-11-generic
    .9GB: initrd.img
   6.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

I'm going to try again, in the meantime. I'll let you know.

Eduardo

---

### Post by ezertuchev on 2009-05-03
Success!!! Now it automatically boots to Vista without the USB stick, and it boots to GRUB (and to ubuntu) automatically whenever the USB stick is plugged in.

That last bit was it! the root(hd1,0) command did it.

Thank you very much, Meierfra!!

I hope this post can help other people with the same problem.

Thanks again.

---

### Post by ezertuchev on 2009-08-29
Hello meierfra,
 
Following up on the help you gave me for my vista mbr problem, I come back for more help.
 
I still have the same Gateway laptop with vista on it. It has a recovery partition for resetting the system to factory settings, which says something like 'protected by pc angel'. Gateway includes an utility called Gateway Recovery Manager, which restarts the computer to boot the recovery partition.
 
I guess something we changed during the mbr recovery process didn't work as expected, because now the computer won't boot to the recovery partition. I have a somewhat cluttered vista system and would like to reset it.
 
I know this is an ubuntu forum, but since you were the one who so kindly helped me with this problem, I thought you might have an insight on how to solve it. By the way, I've lost the USB stick on which ubuntu was installed, but I do still have my ubuntu live cd copy.
 
I hope you can help me.
 
Thanks!
 
Eduardo

---

### Post by meierfra. on 2010-01-28
> because now the computer won't boot to the recovery partition.

Did you try booting into the recovery partition from the entry on your  grub menu?  If yes, what happens?  Any error messages?

You might also see what happens when you set the boot flag to the recovery partition:

```
sudo sfdisk -A1 /dev/sda
```

and then boot from the internal drive. The symbol after A is the number "1" not the letter "l".

(to  boot into Vista from the internal drive, you have to reverse this. Either  boot into Vista from the Grub menu once or use "sudo sfdisk -A2 /dev/sda")

Report any error messages you get.

---

### Post by meierfra. on 2010-01-28
I  just noticed that the  boot flag already is on  /dev/sda1, which is strange.  So also try:


```
sudo lilo -A2 /dev/sda
```
and then  boot from the internal drive.

If none of this helps, we have to have a look at your bcd on /dev/sda1 and /dev/sda2.

---

### Post by ezertuchev on 2010-01-28
will this work from ubuntu installed via wubi? I mean, as a program on vista? I lost my usb stick with ubuntu on it, so I had to reinstall, but because I didn't want to get into trouble again, I installed it via wubi.
 
My concern is if I will be able to boot back onto ubuntu or not once I make this change.

---

### Post by meierfra. on 2010-01-28
Could you run the boot info script again, so that I can have a look at your new setup.

---

### Post by ezertuchev on 2010-02-01
Here are the results

```

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 250.1 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xfb3a2cc7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,033,054    20,032,992   7 HPFS/NTFS
/dev/sda2          20,033,055   488,395,119   468,362,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       ed280e57-dce8-44d9-8c03-4fcb4d887351   ext4                                     
/dev/sda1        0298E5CD98E5BEF3                       ntfs       RECOVERY                      
/dev/sda2        3C1E48751E482A6A                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /host                    fuseblk    (rw)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 3c1e48751e482a6a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 3c1e48751e482a6a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 3c1e48751e482a6a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 3c1e48751e482a6a
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0298e5cd98e5bef3
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 3c1e48751e482a6a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

The Vista recovery partition is located on sda1, and the regular vista partition is located on the sda2.

Sorry for the delay, I had some trouble getting online this weekend.

Thanks!

Eduardo Z.

---

### Post by meierfra. on 2010-02-01
1)  See what happens when you select  the Vista entries at  the Grub menu (try them both)

If 1) did not work:

2)   Put the boot   flag on /dev/sda2

```
sudo sfdisk -A2 /dev/sda
```
Reboot.

If you aren't able to boot into Ubuntu/Windows any more after this, set the boot flag back to /dev/sda1.  Boot from the Ubuntu LiveCD and do "sudo sfdisk -A1 /dev/sda".

If none of this worked, come back here and let me know exactly what happened during the various tries.

---

