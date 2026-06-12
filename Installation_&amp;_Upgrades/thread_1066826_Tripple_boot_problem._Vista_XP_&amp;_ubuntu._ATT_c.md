---
title: "Tripple boot problem. Vista XP &amp; ubuntu. ATT: caljohnsmith and others"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Hachi-Roku on 2009-02-11
Hey hey.

Ive moved overseas and bought a new laptop with vista. This is very hard because my vista is in german...and im not!

Ive done half a days worth of research on the topic and found alot of information but not in the correct 'order' to fix my problem. Ive found people  have had a similar problem when installing in the order of XP, vista, ubuntu. but i have the order vista, XP, ubuntu. 


I have a similar problem to the last half of this;

[http://ubuntuforums.org/showthread.php?t=1015416]("http://ubuntuforums.org/showthread.php?t=1015416")

... i think. And i need some help.

**I wrote  ATT: caljohnsmith and others in the title as i was really impressed by the help given by these people.... it was very Ubuntu of them! good to see.** Now i plea to there (and others) good spirits for my problem!!


So i have vista preinstalled and i installed XP (problem riddled itself), and then ubuntu 8.10.

prior to installing xp and ubuntu i modified the partitions in the vista disk management. this went haywire for some reason and i find i have a very messy partition table. I created space where i wanted ubuntu but during the install this space was labelled with 'unusable'. So to install ubuntu i resized the xp partition and found that it has made a ext3 partition within the XP partition... so now i cant even delete the XP partition and start again! grrr.

Now i boot up and grub gives me options for ubuntu and vista. no XP.
but when i select the vista option it actually boots into XP.

Like in the thread specified... i think i need help with boot sectors and boot management but this is a little above my complete understanding.

Ill post the same text outputs as in the thread i mentioned and i hope someone that understands it better than i do can help me.

thanks!!!!!!!!!!

---

### Post by Hachi-Roku on 2009-02-11
So in terminal i typed
```
sudo fdisk -lu
```

and got result
```
 
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   143861735    70393844    7  HPFS/NTFS
/dev/sda3       246945792   322455903    37755056    7  HPFS/NTFS
/dev/sda4       322456680   488392064    82967692+   f  W95 Ext'd (LBA)
/dev/sda5       322456743   354233249    15888253+   7  HPFS/NTFS
/dev/sda6       354233313   482833574    64300131   83  Linux
/dev/sda7       482833638   488392064     2779213+  82  Linux swap / Solaris

```

So using gparted i figured out;

sda1 is the wierd eisa config partition for vista
sda2 is vista os
between sda2 & 3  is 49GB of unallocated space (the space the ubuntu installer said was unusable) 
sda3 is the 'data' partition which was preloaded with vista
sda4 is the original XP partition that was converted to ext3
sda5 is the XP ntfs within sd4
sda6 is the ubuntu partition within sd4
sda7 is swap

attached is a screenshot of gparted. this might explain things better than i can.





After using this command
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```



i get this output
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfc5c1ce5

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Unknown
/dev/sda2    *      3,074,048   143,861,735   140,787,688   7 HPFS/NTFS
/dev/sda3         246,945,792   322,455,903    75,510,112   7 HPFS/NTFS
/dev/sda4         322,456,680   488,392,064   165,935,385   f W95 Ext d (LBA)
/dev/sda5         322,456,743   354,233,249    31,776,507   7 HPFS/NTFS
/dev/sda6         354,233,313   482,833,574   128,600,262  83 Linux
/dev/sda7         482,833,638   488,392,064     5,558,427  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="066688D46688C641" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="24928C68928C4072" LABEL="Vista" TYPE="ntfs" 
/dev/sda3: UUID="1EF49024F48FFFE7" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="5640FD5340FD3A77" TYPE="ntfs" 
/dev/sda6: UUID="b5e80f34-9440-49b7-b107-05602a8b1828" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="dbad0e9f-2520-46ce-be17-e4f555615cf9" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/jon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jon)

================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=b5e80f34-9440-49b7-b107-05602a8b1828 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b5e80f34-9440-49b7-b107-05602a8b1828

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b5e80f34-9440-49b7-b107-05602a8b1828
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b5e80f34-9440-49b7-b107-05602a8b1828 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b5e80f34-9440-49b7-b107-05602a8b1828
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b5e80f34-9440-49b7-b107-05602a8b1828 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b5e80f34-9440-49b7-b107-05602a8b1828
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b5e80f34-9440-49b7-b107-05602a8b1828 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=dbad0e9f-2520-46ce-be17-e4f555615cf9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 232.0GB: boot/grub/menu.lst
 232.0GB: boot/grub/stage2
 232.0GB: boot/initrd.img-2.6.27-7-generic
 232.0GB: boot/vmlinuz-2.6.27-7-generic
 232.0GB: initrd.img
 232.0GB: vmlinuz

```


My goal is to leave all the partitions as is (as strange as they may be) and change the boot managment so i can boot all three OS's from grub.


I hope this makes sense to someone!

thankyou!!!

---

### Post by caljohnsmith on 2009-02-11
It looks like you have a couple of issues currently preventing you from booting Vista and XP separately from Grub, but they should be fixable. Here's some of the things I notice about your setup:
[LIST]
[*]Since you installed XP to a logical partition (sda5), XP put its boot files in your Vista partition and also modified the Vista boot sector to boot XP's "ntldr" boot file rather than Vista's "bootmgr" boot file.
[*]Your XP sda5 partition boot sector will also need fixing since you want to boot XP directly from sda5.
[/LIST]
I would recommend following meierfra's excellent [XP/Vista/Win7 tutorial]("http://ubuntuforums.org/showthread.php?t=813628") about how to boot XP from a logical partition, and also in that tutorial you will find how to fix your Vista partition so that it can boot independent of XP. If you have any problems, I would suggest posting to that thread, because meierfra can help you sort out any problems with XP/Vista better than I can. Good luck and let me know how it goes though.

---

### Post by Hachi-Roku on 2009-02-12
So i followed that tutorial you recommended. I must say... it is very good. I got through it with minor adaptations until the rebuild vistas boot sector. the only vista disk i had was the recovery disk.... in my atempt to follow the tutorial with it, the disc ended up wiping my hdd. so bye bye all OS's. 

Looks like i have to start again! Which isnt so bad... hopefully ill be able to make the partition table a bit neater now.

I'll let you know how i go.

Thankyou very much for helping me!

J

---

### Post by caljohnsmith on 2009-02-12
Sorry to hear your Vista Recovery CD wiped your HDD, but unfortunately that's quite common with OEM recovery CDs. Just as a small suggestion, when you go to reinstall XP after Vista again, I would recommend giving XP its own primary partition, and also I would recommend "hiding" the Vista partition so that XP does not put its boot files in the Vista partition nor modify its boot sector. You can hide an NTFS partition by doing:
```
sudo sfdisk -c /dev/sda [COLOR="Blue"]<partition number>[/COLOR] 17
```
And replace <partition number> with the partition number, so to hide sda2 would look like:
```
sudo sfdisk -c /dev/sda [COLOR="Blue"]2[/COLOR] 17
```
Then once you are done installing XP, you can unhide Vista by doing:
```
sudo sfdisk -c /dev/sda [COLOR="Blue"]<partition number>[/COLOR] 7
```
Anyway, good luck and let me know how it goes.

---

### Post by Hachi-Roku on 2009-02-12
hmmm interesting. Ill definetely give that a go.


Can this be done with a live cd? just asking because i know xp takes over linux when installed.

last time i installed xp i had no drivers at all. not even ethernet ones.... im going to do a websearch for toshiba drivers first to see if its even worth installing xp.

Thanks!!!
J

---

### Post by caljohnsmith on 2009-02-12
Yes, you can do those commands from a Live CD. :)

---

### Post by Hachi-Roku on 2009-02-12
Cool. Ill give it a shot tomorrow and let you know!!

Thanks!

J

---

### Post by Hachi-Roku on 2009-02-14
Ok... So i reinstalled vista (yes i shuddered),
Then hid the partition with the code you provided,
Intalled xp (with another shudder),
Xp took over the boot flag and mbr... but in its own partition this time!!
Then i installed ubuntu.

Installation went as normal and everything seems to be fine! I can boot into all 3 OS's from grub. with no problems as yet.

Im not sure if xp is on a primary or logical. Last time it went logical because i already had too many primarys. i just let the installer do its thing and it seems to be all good.

Many thanks for all your help!!! The hidden partition code did the trick!

long live ubuntu!

Jon

---

### Post by caljohnsmith on 2009-02-14
That's great news, Jon, glad to hear all your OS installations went smoothly and you can boot them all separately now; cheers and enjoy Ubuntu, XP, and Vista. :)

---

