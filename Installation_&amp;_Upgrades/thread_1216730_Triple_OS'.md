---
title: "Triple OS'"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by emeraldgirl08 on 2009-07-18
I'm curious about W7 and Fedora so I ordered a small hard drive. It is a 40 gb (37.1gb) and I'm wondering how big I should make the partitions. My brother installed W7 and it's taking up around 9 gb of HD space. I know Fedora will require a lot less than that. I may also download OpenSuse or Linux Mint to play around with in the future.

I'm thinking of creating an NTFS partition about 12gb for W7. For Fedora I will allocate 8 Ggb. That leaves me with 16 gb (or close to that). I don't know about creating a FAT32 partition as I will need space for the OpenSuse or Linux Mint. 

This will be for a desktop that already has a 232 gb HDD with Win XP pro on it. I want to leave that alone which is why I have the extra HDD. 

Anybody have any suggestions for me?

---

### Post by ajgreeny on 2009-07-18
Can't help with the Win7 as I know almost nothing about it, and don't really want to either, but you can certainly put the linux distros on as you suggested.  If you must have a fat32 partition, keep it small, or you will run out of space, and you will have your main disk available, anyway. Also consider a shared /data partition for all the linux OSs, so as to keep your root partitions smaller; each /home folder will then only contain the various config files and folders needed by each distro.  Whatever else you do, don't be tempted to have a /home partition shared by different linux distros, that way lies a bundle of trouble.

---

### Post by emeraldgirl08 on 2009-07-20
Okay things are turning out better than I thought. I had a hard time getting my partitions in order but after a day of pulling hair out I finally got some nice partitions and also downloaded OpenSuse and Arch.

I know I know. M$ is a resource depleting pig but I'm learning all I can about comps and M$ is something I'm familiar with. I also love linux (most of the time!) and now have: Fedora, Ubuntu 8.04-9.04, OpenSuse, Arch, Win7, and Xp Pro. I think that should keep me busy for awhile :P

---

### Post by presence1960 on 2009-07-20
+1 to ajgreeny's suggestion about sharing /home among distros. You don't want to open that can of worms!

I don't like Windows but I installed Windows 7 because I build & repair computers so I have to keep my knowledge current, especially since most people use windows. I don't try to convert anyone to linux. I patiently wait for them to ask or bring it up in conversation. Actually 7 seems better than Vista but it is still windows.

---

### Post by emeraldgirl08 on 2009-07-20
Yeah. breaking up linux into /root, /home, etc is a little advanced for me now so no worries about sharing home. 

Yeah. I use what works for me so I don't really worry about the OS.

---

### Post by emeraldgirl08 on 2009-07-21
Okay. I did install W7 and Ubuntu on the same drive. This drive I should mention is an IDE drive.

The other drive is a SATA and has XP solely on it. I didn't do anything fancy yet b/c the Xp drive isn't mine (sisters) and I was just getting a feel.

I wasn't too sure on how to do a boot with this configuration. I thought if I unplugged the xp drive I could use the W7/Ubuntu drive. During installation I placed the boot menu into Win 7's boot drive. I wasn't sure if it would make a mess. To my surprise when I rebooted after installing Grub showed Jaunty and then Vista (I know Jaunty calls W7 that). So. I was content and ready to read up on how to chainload or whatever you do to make a working "boot menu" for all three OS' upon start up.

This morning I was going to update Jaunty because I didn't get a chance to after installation yesterday (family members needed to use this comp). So Grub comes up with the choices and I choose Jaunty. I get almost all the way done with my updates and the power goes out!

Not good.

I wait an hour for it to come back on (since I live in the boonies I gotta wait!) and then resume my update. After installation I wait for the updates to be applied and install the mediuniverse restricted somethings-or-other to get flash, videos, etc to work. I reboot and since my niece is begging me to create an account for her in W7 (and Ubuntu) I go to boot W7 and get a "cannot find OS disc. Please insert OS disc..." 

What broke my boot for W7? Was it the updates b/c I noticed a new kernel was installed. I'm not too sure but if anyone can help I'd appreciate it. Sorry this was SO long too. I just feel the more detail the better.

---

### Post by eternalsword on 2009-07-21
can you boot fine into Jaunty?  Also what's your current /boot/grub/menu.lst file look like?

---

### Post by presence1960 on 2009-07-22
let's get all the info about your setup and boot info in one swoop. boot into Ubuntu, or if you can't boot the Ubuntu Live CD and choose "try ubuntu without any changes". When the desktop loads download to the desktop the boot info script 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)
Once downloaded to desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on your desktop. Paste the entire contents of that file back here. When pasted here highlight all text and click the # sign on the toolbar to place code tags around the text.

This will give us all info about your setup including what the previous poster asked for.

---

### Post by emeraldgirl08 on 2009-07-22
I'll get the boot info in the morning. It's around 12 am here and I'll be up "bright-eyed and bushy-tailed" in the morning with that report :P

---

### Post by emeraldgirl08 on 2009-07-22
Okay. Here is the result of that terminal command.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02317b99

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   488,128,511   488,126,464   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1bfbae8d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             208,845    42,620,444    42,411,600   7 HPFS/NTFS
/dev/sdb3          42,620,445    78,156,224    35,535,780   5 Extended
/dev/sdb5          42,620,508    76,581,854    33,961,347  83 Linux
/dev/sdb6          76,581,918    78,156,224     1,574,307  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019099648 bytes
256 heads, 63 sectors/track, 971 cylinders, total 15662304 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x001c2022

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    15,661,295    15,661,233   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3A084A380849F403" TYPE="ntfs" 
/dev/sdb1: UUID="A8286C86286C54FA" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdb2: UUID="FAF470B4F470752B" TYPE="ntfs" 
/dev/sdb5: UUID="f1e6eaa9-f542-4c89-90a4-18cefc12e3cc" TYPE="ext3" 
/dev/sdb6: UUID="af713095-9747-4d6f-8f74-fc128bb6731c" TYPE="swap" 
/dev/sdc1: UUID="7C2C-7475" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shinigami/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shinigami)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=f1e6eaa9-f542-4c89-90a4-18cefc12e3cc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f1e6eaa9-f542-4c89-90a4-18cefc12e3cc

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		f1e6eaa9-f542-4c89-90a4-18cefc12e3cc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f1e6eaa9-f542-4c89-90a4-18cefc12e3cc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		f1e6eaa9-f542-4c89-90a4-18cefc12e3cc
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=f1e6eaa9-f542-4c89-90a4-18cefc12e3cc ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		f1e6eaa9-f542-4c89-90a4-18cefc12e3cc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f1e6eaa9-f542-4c89-90a4-18cefc12e3cc ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		f1e6eaa9-f542-4c89-90a4-18cefc12e3cc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f1e6eaa9-f542-4c89-90a4-18cefc12e3cc ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		f1e6eaa9-f542-4c89-90a4-18cefc12e3cc
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f1e6eaa9-f542-4c89-90a4-18cefc12e3cc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=af713095-9747-4d6f-8f74-fc128bb6731c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/menu.lst
  30.2GB: boot/grub/stage2
  30.2GB: boot/initrd.img-2.6.28-11-generic
  30.2GB: boot/initrd.img-2.6.28-13-generic
  30.2GB: boot/vmlinuz-2.6.28-11-generic
  30.1GB: boot/vmlinuz-2.6.28-13-generic
  30.2GB: initrd.img
  30.2GB: initrd.img.old
  30.1GB: vmlinuz
  30.2GB: vmlinuz.old
```

FYI the link to download wasn't working. I got an error code for it. Good thing I had that program saved from a time I was working on my laptop :)

---

### Post by eternalsword on 2009-07-22
I'm not 100% on this, but I think in your /boot/grub/menu.lst file, the line
```
rootnoverify	(hd0,0)
```
should be
```
rootnoverify	(hd1,0)
```

I can't be certain since you're combining a sata drive and an ide drive, and I've never had that scenario before.  But it won't hurt to try.

You'll need to be root to edit that file, so
```
gksu gedit /boot/grub/menu.lst
```

If it doesn't work, just revert it back.

Edit:
On second look, it might also be
```
rootnoverify	(hd0,1)
```

or
```
rootnoverify	(hd1,1)
```

---

### Post by oldfred on 2009-07-22
You mention 2 drives but you have 3? I added a new drive with plans to uninstall an old drive, so I had 4 drives 3 sata & 1 pata when I installed Ubuntu 64 bit.

These were the windows entrys for my working XP on my first drive and the not used but found XP on my third drive. When I uninstalled the third drive I had to renumber a lot of things. If Windows is on your first drive add this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

Because windows had to be the first drive, you have to use the map command to make it first even if it is not:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1 
#title        Microsoft Windows XP Professional
#rootnoverify    (hd3,0)
#savedefault
#map        (hd0) (hd3)
#map        (hd3) (hd0)
#chainloader    +1

This was my 'd' drive. I commented out these lines, if you use this uncomment and adjust to your drive & partition. You have additonal windows partitions on b1, b2 & c1 or hd1,0, hd1,1 or hd1,0 and map of hd0 from hd1 and/or hd0 from hd2, if they are bootable.

Also back with an old motherboard, sata & pata drives did not always boot in the same order. I had to use the UUID's to correct to get the system to boot grub everytime. My new motherboard allows me to set boot order in the bios.

---

### Post by presence1960 on 2009-07-22
emeraldgirl, I am getting this info from your Boot Info Script results.txt file you posted. GRUB is installed onto MBR of sdb. When you boot GRUB menu comes up so in your boot order in BIOS your sdb is set to boot first in hard disk boot order. This is as it should be because any other hard disk booting first will not bring up GRUB. Your windows 7 install has a separate boot partition (sdb1) and the OS is on sdb2. That is good also. You must boot win 7 from the separate boot partition, if one was created during install.

Now BIOS and Ubuntu sometimes read the order of hard disks differently. Ubuntu has sda as #1, but BIOS has sdb. In the case of chainloading BIOS order of disks is what you want. So your menu.lst entry for win7 is correct at (hd0,0) with no map lines because windows is on the same disk that is booting first. You only need map lines when windows is on a disk that boots second , third, etc. This is corect in menu.lst:

> 
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1




 Your XP is on sda and that choice should be incorporated into win 7 for boot, you should get a choice of win 7 or XP when you boot win 7. Or you can create a separate entry in menu.lst for XP:

> title          Windows XP
rootnoverify   (hdx,0)
map            (hd0) (hdx)
map            (hdx) (hd0)
chainloader    +1
where x is the number of your sda disk in BIOS boot order. remember in GRUB disk and partition numbering starts at 0. First disk is (hd0), second disk is (hd1). Same for partitions: first partition starts at 0. so the second partition on the first disk = (hd0,1)

Everything appears in order to me. I would insert the disk as prompted. Something must have happened to mess up win 7 when the power went out. You may have to restore GRUB after doing this.

Sorry about the delay, I had work and tonight is one of my daughter's Tae Kwon Do nights.

---

### Post by emeraldgirl08 on 2009-07-23
:D

Thanks SO much for answering guys!

My sis' desktop had been running Vista but we all know how Vista turns out! 

It stank!

So now we have the three OS' I mentioned. I still have other distros of linux I'd like to experiment with once I learn a little more. At this point I think Terminal Commands are a must to learn! This dilemma I'm in actually is pretty much teaching me more things :)

So anyway. I just got in from work and only had like five minutes this afternoon to get that txt report from Terminal and send it. I'll get a chance sometimes in the AM or maybe PM to try it out. I'll be sure to read a little more before I work on it tho! 

You guys are the best! If you were here I'd give you a BIG HUG :)

Thank you!

BTW my sisters comp has all kinds of BIOS things like the ability to do some overclocking, flash the BIOS w/o logging into any OS, manipulate SATA behavior (to mimic IDE... or something like that), etc. See. These things aren't even an option in my old trusty T30 Thinkpad so I was sorta winging it yesterday. Anyway got some surfing to do.

Nite!

---

### Post by presence1960 on 2009-07-23
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

go here for a free pdf Ubuntu Pocket Guide. Excellent source of info.

---

### Post by emeraldgirl08 on 2009-07-26
:confused:

This is killing me!

I really don't know what my /boot/grub/menu.lst should look like! I really would like to get this resolved.

My SATA drive is the Windows XP Pro.

IDE is the W7 (first partition) and Jaunty (second partition). 

I'm going to get a chance to get on the desktop for a couple of minutes later. If anyone could tell me what to add- please do!

I know I have to add a line for Xp Professional but as far as the mapping and hd0,1 stuff I get confused.

Thanks.

---

### Post by presence1960 on 2009-07-26
```
title           Windows XP
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1 
```

I am assuming sdc is a flash card or drive so add this  to menu.lst for XP.

Did you get win 7 to boot yet?

---

### Post by emeraldgirl08 on 2009-07-26
Yes I forgot to mention that I had a Flash Card connected at the time.

I did get on a for a bit yesterday morning and changed somethings around on my menu.lst. I have a backup copy so I can always restore it. Someone's either always on the desktop or I'm not here to work on it. 

I'll insert that paragraph you posted into my menu.lst in a little bit. My brother is using it right now so I don't know exactly when he will be done. It's 12:35 am here in Arizona so...I'm a little worn out. I may fall asleep while waiting so if I do I'll try it first open chance I get today.

Thanks.

---

### Post by presence1960 on 2009-07-26
don't let this kill you, Rome wasn't built in a day. Let's think this through here. You do get a GRUB menu when you boot right? If yes, then that means your sdb drive is set to boot first in the hard disk order in BIOS. look at the top of your RESULTS.txt file you posted and you will see that GRUB is installed to MBR of sdb (40 GB). If any other hard disk boots first GRUB will not come up.

Ubuntu and BIOS sometimes read the order of hard disks differently as is evidenced in your file you posted. It has sda (250 GB) as first disk, but that is not true because BIOS boots sdb first. This is important to understand. When adding the chainload entry you must use the order of your disks in BIOS. In BIOS you have sdb (40 GB) first and sda (250 GB) second. XP is on sda. So XP is on the second hard disk. Thus the entry for XP is (hd1,0) which equates to the second disk (1) first partition (0). In GRUB disk & partition numbering starts at 0.

The reason you need those map lines with the hard disk #'s in there is windows just will not boot if it is not on the disk that boots first. So those map lines include the disk that boots first (hd0) and the disk windows xp is on (hd1). This "tricks" windows into thinking it is on the device that boots first. 

On the other hand win 7 does not need the map lines because it is on the device that boots first (sdb).

---

### Post by emeraldgirl08 on 2009-07-27
Help.

I added these lines to my /menu.lst and now I can't even stay on Ubuntu longer than a couple of seconds. It just shuts down.
[B]
Changed this:[/B] ```
rootnoverify	(hd0,0)
```

**To this:**  ```
rootnoverify	(hd1,0)
```

**And added this:**

```
title           Windows XP
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1
```

I am using my lappy now to send this message. The Windows XP loads fine on it's own when I don't use GRUB to try and boot it. When I choose to boot from the HDD that holds W7 and Ubuntu it will not boot XP or W7. Ubuntu will log on and then after displaying the desktop will shut off and restart the comp.

Any suggestions?

---

### Post by oldfred on 2009-07-27
I think you are real close. presence1960's title for the boot on (hd1,0) should be the Windows 7. and the XP should be the (hd0,0) entry. Otherwise his entries look correct to me. 

When you say you boot windows are you just choosing the drive to boot in the bios. If you were unplugging the second drive or the first drive it changes the drive order (sda vs sdb) and the second drive will think it is first.

Map is only required for drives that are not hd0 in GRUB or sda in linux for windows, windows wants to be hd0 no matter what so grub makes it think it is hd0 even if it is not.

You can also edit in Windows the boot.ini file to give you the two windows choices, but I have never done that.

If your ubuntu is crashing after boot that is a total separate issue not related to booting. Do you get any error message, does it only boot to a command line, or does it just reboot. It would probalby be better to open a new thread with that problem after you can boot correctly.

Additional help:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by emeraldgirl08 on 2009-07-27
The text report generated by the Ubuntuzilla prog on page 1 is how I have the desktop pretty much set up- minus the 8 gb CF card that was plugged in.

I really didn't know what to do so I loaded up the W7 disk and went into repair. It did something with the GRUB. I think it threw it out! There is no GRUB anymore. The desktop just loads into W7 (which is where I'm typing from now).

:D lol

Time to get my nose back to the grindstone. I may check the W7 forums and see if I can get any help there. A big thanks for the help anyway OldFred :)

---

### Post by oldfred on 2009-07-27
If you want to try to reinstall GRUB:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)
be sure to read several of the messages following as one or two of the instructions leave out a step. See #8 as a fix to #1 of the graphical installs using the install CD. Or use the text install

---

### Post by presence1960 on 2009-07-28
Emerald, I would say at this point reinstall Ubuntu. it would seem the power outtage during your updates did some damage to your OS. Those lines you edited in menu.lst have no effect on Ubuntu. They only tell GRUB where to look to boot windows when you select that entry. When you boot Ubuntu that entry has no effect because it is not being used.

If there are any files on Ubuntu you wish to save then boot from the Live CD and choose "try ubuntu without any changes..." when the desktop loads open the file browser and move any files you wish to save to sda or a flash drive. Then try installing Ubuntu again. When you get to the Ready to install window click the advanced button (see attached pic). This will allow you to choose where to install GRUB. You want it on MBR of your Win 7/Ubuntu hard disk, whch should be sdb. So choose sdb from the drop down menu to put GRUB on MBR.

---

### Post by presence1960 on 2009-07-28
Emerald, here is that screenshot, PM's won't let you post an attachment.

---

### Post by emeraldgirl08 on 2009-07-30
Okay.

I haven't reinstalled Jaunty yet. I did however figure out why I was not able to edit my menu.lst file.

It was b/c I didn't use terminal to gksu edit /boot/grub/menu.lst! I had a eureka moment this morning during some downtime and edited the boot menu to look like:

```
jaunty
jaunty (recovery mode)

Windows 7
```

I took XP off the list for now. I did save the original menu.lst file before I altered it. Now to try that mapping script you gave me presence :)

I'm on my R52 now so I'm on another project.

---

