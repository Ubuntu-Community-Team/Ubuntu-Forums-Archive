---
title: "double sata dualboot (windows7+ubuntu9.04)"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by stereopanda on 2009-09-30
Fellow Pinguin-lovers,

Since this is my first post here, and i'm a long-time reader i'd first like to thank all the people on this forum for their major support amongst linux users.
so.. to cut to the point :) i'm having a problem! A few days ago i bought a new 1TB samsung spinpoint HDD for my upcoming dualboot, with 2 spinpoints. On the first drive i've installed Windows 7 and on the second one (the new one!) i've installed ubuntu. 

See, the problem is.. everytime i try to boot into windows.. it keeps giving me all kinds of errors, like "Grub error 13" and "No-boot device-- ... something". 
I've read a lot of simmilar threads about this on the ubuntu forums but i cant find a solution.. fixing my grub has not solved the problem. ATM my settings for the first hdd are like this.

title Microsoft Windows 7
rootnoverify (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

Can someone please help me out? I'm desperate :( Cheers,
Niels

---

### Post by presence1960 on 2009-09-30
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by stereopanda on 2009-09-30
Here u go! :)

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 600457279 
    on boot drive #2 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         409,640 1,953,260,871 1,952,851,232 HFS+

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00095b47

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,918,177,064 1,918,177,002  83 Linux
/dev/sdb2       1,918,177,065 1,953,520,064    35,343,000   5 Extended
/dev/sdb5       1,918,177,128 1,953,520,064    35,342,937  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="EFI" UUID="3F3C-1AF6" TYPE="vfat" 
/dev/sdb1: UUID="4b4e9052-bba3-4859-8b9d-1087ac733ed2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="309c260f-cdd7-419d-8a87-92897c0a97fc" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/niels/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=niels)


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
# kopt=root=UUID=4b4e9052-bba3-4859-8b9d-1087ac733ed2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4b4e9052-bba3-4859-8b9d-1087ac733ed2

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        4b4e9052-bba3-4859-8b9d-1087ac733ed2
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=4b4e9052-bba3-4859-8b9d-1087ac733ed2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        4b4e9052-bba3-4859-8b9d-1087ac733ed2
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=4b4e9052-bba3-4859-8b9d-1087ac733ed2 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        4b4e9052-bba3-4859-8b9d-1087ac733ed2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4b4e9052-bba3-4859-8b9d-1087ac733ed2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        4b4e9052-bba3-4859-8b9d-1087ac733ed2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=4b4e9052-bba3-4859-8b9d-1087ac733ed2 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        4b4e9052-bba3-4859-8b9d-1087ac733ed2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows 7
rootnoverify (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=4b4e9052-bba3-4859-8b9d-1087ac733ed2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=309c260f-cdd7-419d-8a87-92897c0a97fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 307.4GB: boot/grub/menu.lst
 307.4GB: boot/grub/stage2
 307.4GB: boot/initrd.img-2.6.28-11-generic
 307.4GB: boot/initrd.img-2.6.28-15-generic
 307.3GB: boot/vmlinuz-2.6.28-11-generic
 307.4GB: boot/vmlinuz-2.6.28-15-generic
 307.4GB: initrd.img
 307.4GB: initrd.img.old
 307.4GB: vmlinuz
 307.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  57 00 00 00 61 00 72 00  2d 00 4c 00 42 00 00 00  |W...a.r.-.L.B...|
00000010  73 00 72 00 2d 00 4c 00  61 00 74 00 6e 00 2d 00  |s.r.-.L.a.t.n.-.|
00000020  4d 00 45 00 00 00 90 90  65 00 73 00 2d 00 41 00  |M.E.....e.s.-.A.|
00000030  52 00 00 00 65 00 6e 00  2d 00 54 00 54 00 00 00  |R...e.n.-.T.T...|
00000040  61 00 72 00 2d 00 4a 00  4f 00 00 00 73 00 72 00  |a.r.-.J.O...s.r.|
00000050  2d 00 43 00 79 00 72 00  6c 00 2d 00 52 00 53 00  |-.C.y.r.l.-.R.S.|
00000060  00 00 90 90 65 00 73 00  2d 00 50 00 45 00 00 00  |....e.s.-.P.E...|
00000070  65 00 6e 00 2d 00 42 00  5a 00 00 00 61 00 72 00  |e.n.-.B.Z...a.r.|
00000080  2d 00 53 00 59 00 00 00  73 00 6d 00 6e 00 2d 00  |-.S.Y...s.m.n.-.|
00000090  46 00 49 00 00 00 90 90  73 00 72 00 2d 00 4c 00  |F.I.....s.r.-.L.|
000000a0  61 00 74 00 6e 00 2d 00  52 00 53 00 00 00 90 90  |a.t.n.-.R.S.....|
000000b0  65 00 73 00 2d 00 43 00  4f 00 00 00 65 00 6e 00  |e.s.-.C.O...e.n.|
000000c0  2d 00 30 00 32 00 39 00  00 00 90 90 61 00 72 00  |-.0.2.9.....a.r.|
000000d0  2d 00 59 00 45 00 00 00  73 00 6d 00 73 00 2d 00  |-.Y.E...s.m.s.-.|
000000e0  46 00 49 00 00 00 90 90  62 00 73 00 2d 00 43 00  |F.I.....b.s.-.C.|
000000f0  79 00 72 00 6c 00 2d 00  42 00 41 00 00 00 90 90  |y.r.l.-.B.A.....|
00000100  65 00 73 00 2d 00 56 00  45 00 00 00 65 00 6e 00  |e.s.-.V.E...e.n.|
00000110  2d 00 4a 00 4d 00 00 00  61 00 72 00 2d 00 4f 00  |-.J.M...a.r.-.O.|
00000120  4d 00 00 00 73 00 6d 00  61 00 2d 00 53 00 45 00  |M...s.m.a.-.S.E.|
00000130  00 00 90 90 73 00 72 00  2d 00 43 00 79 00 72 00  |....s.r.-.C.y.r.|
00000140  6c 00 2d 00 42 00 41 00  00 00 90 90 65 00 73 00  |l.-.B.A.....e.s.|
00000150  2d 00 44 00 4f 00 00 00  65 00 6e 00 2d 00 5a 00  |-.D.O...e.n.-.Z.|
00000160  41 00 00 00 61 00 72 00  2d 00 54 00 4e 00 00 00  |A...a.r.-.T.N...|
00000170  73 00 6d 00 61 00 2d 00  4e 00 4f 00 00 00 90 90  |s.m.a.-.N.O.....|
00000180  73 00 72 00 2d 00 4c 00  61 00 74 00 6e 00 2d 00  |s.r.-.L.a.t.n.-.|
00000190  42 00 41 00 00 00 90 90  66 00 72 00 2d 00 4d 00  |B.A.....f.r.-.M.|
000001a0  43 00 00 00 65 00 73 00  2d 00 50 00 41 00 00 00  |C...e.s.-.P.A...|
000001b0  65 00 6e 00 2d 00 49 00  45 00 00 00 61 00 72 00  |e.n.-.I.E...a.r.|
000001c0  2d 00 4d 00 41 00 00 00  73 00 6d 00 6a 00 2d 00  |-.M.A...s.m.j.-.|
000001d0  53 00 45 00 00 00 90 90  62 00 73 00 2d 00 4c 00  |S.E.....b.s.-.L.|
000001e0  61 00 74 00 6e 00 2d 00  42 00 41 00 00 00 90 90  |a.t.n.-.B.A.....|
000001f0  66 00 72 00 2d 00 4c 00  55 00 00 00 65 00 73 00  |f.r.-.L.U...e.s.|
00000200

```

---

### Post by presence1960 on 2009-09-30
according to the output you posted windows is not installed. was it on sda2? If so it is unmountable. get back with the answer please.

---

### Post by louieb on 2009-09-30
I see a GPT partition table on sda1 - not used much on anything but Apple - is this an Apple PC? 

Anyway a couple of windows entries to try. - Since Windows is on the 1st drive the map commands are not needed and may confuse things.

```

title Microsoft Windows 7
rootnoverify (hd0,1)
makeactive 
chainloader +1

```
if aboved does not work try the 1st partition.
```

title Microsoft Windows 7
rootnoverify (hd0,0)
makeactive 
chainloader +1
```

---

### Post by stereopanda on 2009-10-01
> **presence1960 said:**
> according to the output you posted windows is not installed. was it on sda2? If so it is unmountable. get back with the answer please.

I installed Windows 7 on the first disk, so that would be SDA1, right? I'm pretty sure this was done correctly, because i used it for several weeks without any botting problems.

> **louieb said:**
> I see a GPT partition table on sda1 - not used much on anything but Apple - is this an Apple PC? 

Anyway a couple of windows entries to try. - Since Windows is on the 1st drive the map commands are not needed and may confuse things.

```

title Microsoft Windows 7
rootnoverify (hd0,1)
makeactive 
chainloader +1

```if aboved does not work try the 1st partition.
```

title Microsoft Windows 7
rootnoverify (hd0,0)
makeactive 
chainloader +1
```

I used the same harddrive to build a hackintosh a few months ago, so that can be reason why it's showing up as an Guid Partition Table. Never the less, i formatted this harddrive before i installed windows on it.. so i dont rly get why the GPT is still showing up. Also tried your supplied code to edit my menu.lst, but this didn't work. The (hd0,1) code popped up and GRUB 13 error. And the (hd0,0) came up with this drive not being a valid boot partition, or something like that. :(

---

### Post by louieb on 2009-10-01
Don't have any Apple PC products and never tired a GPT partition table. So when I see a thread with Apple - I usually just fly by it. 

Not even sure GRUB can boot an OS on a GPT partition table disk. Wonder if LILO could boot it. Might try looking around the Apple section of the forum to see what boot loader they use.

I do know **fdisk** does not handle GPT but **parted **can.

>  so i dont rly get why the GPT is still showing up

Guess you did not change the partition table type when you reformatted it. 
To change the partition table type In Gparted  its **Device>disk label** 
Don't know if you want to go to the trouble of changing the partition table type to **msdos** (the default and the most commony used). Re-partitoning the drive and reinstalling windows. Thats the only way I know to get GRUB to work.

---

### Post by stereopanda on 2009-10-01
Na, i don't want to use Mac OSX anymore.. just windows and ubuntu, so that's not necesary. So, correct me if i'm wrong.. you're saying that the possible trick that will fix it would be entering
```
gparted sda1>msdos
```

And after that, i need to completely format and reinstall my windows partition?
Thanks for the help so far :)

---

### Post by louieb on 2009-10-01
Close its just **sda**. After you select apply it will become a blank drive with an msdos partition table ready to partition as you like.

---

### Post by stereopanda on 2009-10-02
> **louieb said:**
> Close its just **sda**. After you select apply it will become a blank drive with an msdos partition table ready to partition as you like.

I managed to delete the partition table on my first harddrive (the one is used for OSX). Ubuntu 9.04 is now running on that one.. and i have windows 7 installed on the other disk.. so that's going perfectly well! But here's the deal.. 

I disconnected my ubuntu HDD while installing windows 7. But if i disconnect the windows 7 disk.. and connect the ubuntu disk.. i get a boot error when trying to access ubuntu! :s i'm seriously going bananas. It looks like it's neirly impossible to get this dualboot working.. or can someone please hook me up with a good step-by-step plan?

---

### Post by louieb on 2009-10-02
Well lets take a look Plug both in. Boot Ubuntu.   And run the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") again. 

if you see this
> => No boot loader is installed in the MBR of /dev/sdb


Its a simple matter of putting GRUBS stage1 code in the MBR of **sdb**

```
sudo grub
```
Make sure you change the mbr of the right drive
```
find /boot/grub/stage1
```
If nothing else has changed should return [COLOR=DarkOrange]**(hd1,0)**[/COLOR] 

```
root (hd1,0) 
setup (hd1) 
quit
```

But if you have plugged the drives in different or some way change the boot order could return [COLOR=DarkOrange](hd0,0)[/COLOR]

```
root (hd0,0) 
setup (hd0) 
quit
```

---

### Post by stereopanda on 2009-10-02
Hey guys,
 
Just to let you all know.. my friend commodore came by my house today and fixed the problem :) we still dont get what the exact problem was.. but i reinstall did the trick!
Thanks for all the help and support, appreciate it! 
 
You all rock 
 
:guitar:

---

### Post by all-knowing-moron on 2009-10-13
i am having a simalar problem but on a single sata drive
 
used windows to partion the drive for windows 
installing windows first
as sugested buy info i read some place
alocated 10gig for my windows partion on sda1
installed windows and it was working fine
 
ran the live cd i made 
partioned the drive some more for ubuntu 9.04
adding sda2 ext3 9993mb "root for ubuntu"
added sda5 swap 4096mb
added sda6 ext3 975616mb "intened for mass storage of both os using some utility i ran across 
forgot the name hind sight and more reading have lead me to belive the program is totaly broken 
havnt decided what to do for mass storage yet so left it ext3 for now
as im only allowed 4 partions in grub ?
tempted to do a multi and just let boot.ini handel it as it can do unlimited partions
but that goes against all the info i read about dualbooting befor decinding to run both os's
 
in summary
sda1 ntfs 10489 mb » windows installed and "unmountable_boot_volume"
sda2 ext3 9993 mb » ubuntu 9.04 installed and working
sda5 swap 4096 mb
sda6 ext3 975616 mb ("also reads ubuntu") selected the root to be user/info/ «? the very bottem choice on install screen!
 
ok so knowing that i have a bootable ubuntu and a usedtowas bootable windows partion
how do i fix the problem in grub?
i need explicit instuctions as im new to grub and insecure enough as it is in using it
i have no clue what the othere websites have refered to "bash this smash that"
windows boot failuer message 
stop error :0x000000ed (0x81b18900, 0xc000014f, 0x00000000, 0x00000000 )
UNMOUNTABLE_BOOT_VOLUME
 
INSTALLING LINUX CAUSED THIS PROBLEM AND IM NOT HAPPY AS I STARTED WITH WINDOWS TO AVOID THIS PROBLEM THAT I HAD READ ABOUT WHEN SETTING UP A DUAL BOOT AND INSTALLING LINUX FIRST did i misunderstand what i read and done what it was saying not to do? could swear it said linux secound windows first to avoid a boot volum failure
unfortanetly i can't find that liturature any more to refrence the problem 
having reformated this system the bookmark is gone >dont ask i dont know how my favaroits folder got coruopted on the cd. ~ grumbles ~ the othere user's favorites folders where saved "not a single mark on the cd" (looks new out the stack)
 
](*,) @linux
 
:frown: @linux
 
:cry::sad: for trying linux and having problems i dont understand how to fix
 
oh btw i want to fix not reinstal windows as windows has already been updated to sp3 from a non sp1 disk yah thats like 6 hours of dowloads nowdays (,,!,, windows) is what i want to say but problems and knowledg curve like this prevent me from going pure nix
 
first cup of ubuntu  yah and the beens are tasting bitter maybie even a lil burnt

---

### Post by presence1960 on 2009-10-13
> **all-knowing-moron said:**
> i am having a simalar problem but on a single sata drive
 
used windows to partion the drive for windows 
installing windows first
as sugested buy info i read some place
alocated 10gig for my windows partion on sda1
installed windows and it was working fine
 
ran the live cd i made 
partioned the drive some more for ubuntu 9.04
adding sda2 ext3 9993mb "root for ubuntu"
added sda5 swap 4096mb
added sda6 ext3 975616mb "intened for mass storage of both os using some utility i ran across 
forgot the name hind sight and more reading have lead me to belive the program is totaly broken 
havnt decided what to do for mass storage yet so left it ext3 for now
as im only allowed 4 partions in grub ?
tempted to do a multi and just let boot.ini handel it as it can do unlimited partions
but that goes against all the info i read about dualbooting befor decinding to run both os's
 
in summary
sda1 ntfs 10489 mb » windows installed and "unmountable_boot_volume"
sda2 ext3 9993 mb » ubuntu 9.04 installed and working
sda5 swap 4096 mb
sda6 ext3 975616 mb ("also reads ubuntu") selected the root to be user/info/ «? the very bottem choice on install screen!
 
ok so knowing that i have a bootable ubuntu and a usedtowas bootable windows partion
how do i fix the problem in grub?
i need explicit instuctions as im new to grub and insecure enough as it is in using it
i have no clue what the othere websites have refered to "bash this smash that"
windows boot failuer message 
stop error :0x000000ed (0x81b18900, 0xc000014f, 0x00000000, 0x00000000 )
UNMOUNTABLE_BOOT_VOLUME
 
INSTALLING LINUX CAUSED THIS PROBLEM AND IM NOT HAPPY AS I STARTED WITH WINDOWS TO AVOID THIS PROBLEM THAT I HAD READ ABOUT WHEN SETTING UP A DUAL BOOT AND INSTALLING LINUX FIRST did i misunderstand what i read and done what it was saying not to do? could swear it said linux secound windows first to avoid a boot volum failure
unfortanetly i can't find that liturature any more to refrence the problem 
having reformated this system the bookmark is gone >dont ask i dont know how my favaroits folder got coruopted on the cd. ~ grumbles ~ the othere user's favorites folders where saved "not a single mark on the cd" (looks new out the stack)
 
](*,) @linux
 
:frown: @linux
 
:cry::sad: for trying linux and having problems i dont understand how to fix
 
oh btw i want to fix not reinstal windows as windows has already been updated to sp3 from a non sp1 disk yah thats like 6 hours of dowloads nowdays (,,!,, windows) is what i want to say but problems and knowledg curve like this prevent me from going pure nix
 
first cup of ubuntu  yah and the beens are tasting bitter maybie even a lil burnt

GRUB does not limit partitions to 4, nor does boot .ini allow more than 4. That rule of 4 is for all hard disks. It has nothing to do with boot loaders or bootstrappers. See here: [https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

Yes you did misunderstand because it really does not matter which OS you install first. Either way will work.

You don't need an outside program to have storage. You can create an NTFS partition for storage and you will be able to read/write to it from both windows & ubuntu. I would shitcan that program and just make an NTFS partition for your data storage.

I need more info, probably info you can't provide yourself. So do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

We will see what you have exactly on your machine and go from there.

P.S. I think you have some misconceptions about dual booting and partitioning in general. You should really spend a little time getting yourself up to speed with some basic stuff if you are going to install & use Linux. Here are some links:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/](http://www.psychocats.net/)
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[https://help.ubuntu.com/9.04/switching/index.html](https://help.ubuntu.com/9.04/switching/index.html)
[http://www.tech-faq.com/hard-disk-partition.shtml](http://www.tech-faq.com/hard-disk-partition.shtml)

that should be enough to get you started

---

### Post by all-knowing-moron on 2009-10-14
and your guilty >where and how do i open a terminal ?
i cant seem to find it do i have to be booted into the cd?to have a terminal
ok booted the cd found the terminal
not having any sucsess running that comand
i have the script downloaded on both the installed and cd destop and nothing
my prompt looks like this ubuntu@ubuntu:~$ -'- (without quotes)
i type in " sudo bash ~/Desktop/boot_info_script*.sh " and get » no such file or directory
must have typed something incorectly the first try 
backspaced prompt as far as i could and copied & pasted command got the results posting momentarily
 
i do belive i see the problem
boot.ini says partion 1 and should be 0
going to try editing it

---

### Post by all-knowing-moron on 2009-10-14
============================= Boot Info Summary: ==============================
 
=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 
sda1: _________________________________________________________________________
 
File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM
 
sda2: _________________________________________________________________________
 
File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 9.04
Boot files/dirs: /boot/grub/menu.lst /etc/fstab
 
sda3: _________________________________________________________________________
 
File system: Extended Partition
Boot sector type: -
Boot sector info: 
 
sda5: _________________________________________________________________________
 
File system: swap
Boot sector type: -
Boot sector info: 
 
sda6: _________________________________________________________________________
 
File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e047e04
 
Partition Boot Start End Size Id System
 
/dev/sda1 * 63 20,487,599 20,487,537 7 HPFS/NTFS
/dev/sda2 20,498,940 40,017,914 19,518,975 83 Linux
/dev/sda3 40,017,915 1,953,520,064 1,913,502,150 5 Extended
/dev/sda5 40,017,978 48,018,284 8,000,307 82 Linux swap / Solaris
/dev/sda6 48,018,348 1,953,520,064 1,905,501,717 83 Linux
 
 
blkid -c /dev/null: ____________________________________________________________
 
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="966012CB6012B24B" TYPE="ntfs" 
/dev/sda2: UUID="9a0938d1-fb3a-4ab1-a1b5-1da166365f4f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="77449208-b603-45b4-8f95-0f2ec5186565" TYPE="swap" 
/dev/sda6: UUID="3356bc2f-863b-429d-a64c-3724d6d3b450" SEC_TYPE="ext2" TYPE="ext3" 
/dev/ramzswap0: TYPE="swap" 
 
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
 
 
================================ sda1/boot.ini: ================================
 
[boot loader] timeout=30 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS [operating systems] multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 
=========================== sda2/boot/grub/menu.lst: ===========================
 
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.
 
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
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW62kHK1QfV4P2b2znUoe/
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9a0938d1-fb3a-4ab1-a1b5-1da166365f4f ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=9a0938d1-fb3a-4ab1-a1b5-1da166365f4f
 
## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true
 
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false
 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
 
## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false
 
## Xen hypervisor options to use with the default Xen boot option
# xenhopt=
 
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
 
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single
 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all
 
## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
## indomU=true
## indomU=false
# indomU=detect
 
## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true
 
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
 
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
 
## ## End Default Options ##
 
title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        9a0938d1-fb3a-4ab1-a1b5-1da166365f4f
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=9a0938d1-fb3a-4ab1-a1b5-1da166365f4f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet
 
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        9a0938d1-fb3a-4ab1-a1b5-1da166365f4f
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=9a0938d1-fb3a-4ab1-a1b5-1da166365f4f ro single
initrd        /boot/initrd.img-2.6.28-15-generic
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9a0938d1-fb3a-4ab1-a1b5-1da166365f4f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9a0938d1-fb3a-4ab1-a1b5-1da166365f4f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
 
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9a0938d1-fb3a-4ab1-a1b5-1da166365f4f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9a0938d1-fb3a-4ab1-a1b5-1da166365f4f ro single
initrd        /boot/initrd.img-2.6.28-11-generic
 
title        Ubuntu 9.04, memtest86+
uuid        9a0938d1-fb3a-4ab1-a1b5-1da166365f4f
kernel        /boot/memtest86+.bin
quiet
 
### END DEBIAN AUTOMAGIC KERNELS LIST
 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
 
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
 
 
=============================== sda2/etc/fstab: ===============================
 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda2 during installation
UUID=9a0938d1-fb3a-4ab1-a1b5-1da166365f4f / ext3 relatime,errors=remount-ro 0 1
# /usr/local was on /dev/sda6 during installation
UUID=3356bc2f-863b-429d-a64c-3724d6d3b450 /usr/local ext3 relatime 0 2
# swap was on /dev/sda5 during installation
UUID=77449208-b603-45b4-8f95-0f2ec5186565 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
 
=================== sda2: Location of files loaded by Grub: ===================
 
 
19.5GB: boot/grub/menu.lst
19.5GB: boot/grub/stage2
19.5GB: boot/initrd.img-2.6.28-11-generic
19.5GB: boot/initrd.img-2.6.28-15-generic
19.6GB: boot/vmlinuz-2.6.28-11-generic
19.5GB: boot/vmlinuz-2.6.28-15-generic
19.5GB: initrd.img
19.5GB: initrd.img.old
19.5GB: vmlinuz
19.6GB: vmlinuz.old
=============================== StdErr Messages: ===============================
 
sed: can't read sda6/etc/issue: No such file or directory

---

### Post by presence1960 on 2009-10-14
Ok, your output looks good. Exactly what is your problem? I can't seem to make out what is wrong in your original post as it is very long winded. Try to express the problem in as little words as possible, i.e. Windows will not boot when I select it in GRUB- I get message NTLDR is missing.

I have all the info I need about your setup and boot process, now you need to tell me what your problem is.

---

### Post by presence1960 on 2009-10-14
> **all-knowing-moron said:**
> 
 
i do belive i see the problem
boot.ini says partion 1 and should be 0
going to try editing it

My windows xp is on the first partition and boot.ini says partition(1). here is my boot,ini:

```
================================ sdc1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

Here is my fdisk output:
```
raz@raz-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85858585

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00072abb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02020202

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdc2            5223        9661    35656267+   5  Extended
/dev/sdc5            5223        5744     4192933+  82  Linux swap / Solaris
/dev/sdc6            5745        8094    18876343+  83  Linux
/dev/sdc7            8095        9661    12586896   83  Linux
raz@raz-desktop:~$ 
```

My hard disk boot order in BIOS is sdc, sda, sdb.
sdc1 is XP Professional
sdc6 is Ubuntu 9.04
sdc7 is Masonux 9.04

sda1 is an ext3 data storage
sdb1 is backup and OS images

---

### Post by all-knowing-moron on 2009-10-14
my precise problem is windows will not load due to unmnountable_boot_volume
i select it in grub it starts to load then stop errors
just tryed to edit the partion tabel and add /windows 
as the mount point for sda1
epic fail 
trying dos next
note:i did not complet instal of nix again quit at step 5
BOD message :
A problem has been detected and windows has been shut down to prevent damage to your computer.
 
UNMOUNTABLE_BOOT_VOLUME
 
if this is the first you've seen this stop error screen,restart your computer. If this screen apears again, follow these steps:
check to make shur any new hardware or software is properly installed.
if this is a new instalation, ask your hardware manufactor or software manufactor for any windows updates you might need.
 
if problems contiune, disable or remove any newly installed hardware or software.
disable bios memory options such as caching or shadowing.
if you need to use safe mode to remove or disable components, restart your computer, press f8 to select advanced startup options,
and then select safe mode.
 
technical information:
*** STOP: 0X000000ED (0X81B18900, 0XC000014F, 0X00000000, 0X00000000)
:END MESSAGE
NOTES:WINDOWS WORKED BEFOR INSTALLING NIX AND GRUB
SAFEMODE WILL NOT LOAD ITHERE 
THE PROBLEM SDA1 IS UNMOUNTED FROM INSTALLING NIX OR AN ERROR I MADE WHILE PARTIONING FOR NIX
POSIBLE SOLUTION MOUNT IT IN PARTION EDITOR

---

### Post by presence1960 on 2009-10-14
> **all-knowing-moron said:**
> my precise problem is windows will not load due to unmnountable_boot_volume
i select it in grub it starts to load then stop errors

OK then, you need to run your windows XP install disk to fix windows. Boot your XP disk and follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for XP. If your XP is fixable this should do the trick. Just be aware this will overwrite GRUB on MBR with Windows. You should boot right into windows when you reboot if the repair was successful. You will be half way there now.

Next you need to restore GRUB to MBR by doing this:

```
1. Boot your computer up with Ubuntu CD/USB
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

```

Reboot and you should be good to go.

**Note:** if the first part does not fix windows then you are going to have to reinstall windows to sda1 then restore GRUB as outlined in second half of instructions after installing windows.

---

### Post by all-knowing-moron on 2009-10-14
thats not a solutions its a work around and dose not adrees the problem an unmounted sda1
if i do that im going to have more problems then i have now
thank you for responding and helping
the info on partioning pointed me in the corect direction
 
ok first go round with partion editor failed to modify the mbr
had to go thru with a complet install of nix to modify the mbr "this is obnoxsiuos and needs an apply button"
i deleted my mass storage area and created a new extended logical partion for nix
asinded /dos for the mount point to sda1 and windows boots properly now
i knew the problem wasnt with windows dame it "thus using windows disk was bs"
 
its anoying to have to load the ubuntu cd to use the partioning table in step 4 of the instalation cd for ubuntu
that should be avalible from the pre boot area of the cd and not requir a complet instalation to make partion changes
is that gparted in step 4 ? 
i would use my cd for my drive if it saported selfboot "stupid company" depends on os for boot such rediculous things i see from oem's
next up checking old and new instals of nix
 
things you might find usefull if you have same or simalur problem
image burn software : [http://fileforum.betanews.com/sendfile/1128426215/1/1255563230.1a6d0978d4c37e255d2d249a4f6207cf6cc3289a/SetupImgBurn_2.5.0.0.exe](http://fileforum.betanews.com/sendfile/1128426215/1/1255563230.1a6d0978d4c37e255d2d249a4f6207cf6cc3289a/SetupImgBurn_2.5.0.0.exe)
gparted download : [http://downloads.sourceforge.net/project/gparted/gparted-live-stable/0.4.6-1/gparted-live-0.4.6-1.iso?use_mirror=softlayer](http://downloads.sourceforge.net/project/gparted/gparted-live-stable/0.4.6-1/gparted-live-0.4.6-1.iso?use_mirror=softlayer)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
and thank you for your help in resolving my unmountable_boot_volume problem couldnt of done it with out your help! 
my coffe taste much better now sombody put some cream and sugar in it :)

---

