---
title: "GRUB freeze @ 1.5"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by gagagoogoo on 2009-09-06
hi hi,

total n00b here. but a very excited n00b 'cause loving this OS so far but have a bit of a prob...

made a LiveCD thing in the USB (no CD/DVD drive). booted from USB w/o any problems. really liked what i saw so installed the OS via the install shortcut on the desktop. however, on rebooting, it got stuck on GRUB 1.5 w/ only the following msg:[INDENT][COLOR=Red][B]GRUB loading stage 1.5.
GRUB loading, please wait...[/B][/COLOR]
[/INDENT]nothing else. no error msg. NADA.

my specs are:[INDENT][B]* AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
* Asus M2N-E MOBO
* 2 GB RAM
* GeForce 8800 GTS PCI-e
* 40 GB HD w/ no partition (except for the swap directory that the LiveCD created)
* Ubuntu 9.04 installed via LiveCD on 4 GB USB key[/B]
[/INDENT]and disk/partition info:[INDENT][B]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe86d1a12

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4795    38515806   83  Linux
/dev/sda2            4796        5005     1686825    5  Extended
/dev/sda5            4796        5005     1686793+  82  Linux swap / Solaris

Disk /dev/sdb: 4005 MB, 4005527552 bytes
255 heads, 32 sectors/track, 958 cylinders
Units = cylinders of 8160 * 512 = 4177920 bytes
Disk identifier: 0xf98aec39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         958     3908624    6  FAT16[/B]
[/INDENT]so googled for possible solutions and i tried to install GRUB natively:[INDENT][B]root@ubuntu:/boot/grub# sudo grub
sudo: unable to resolve host ubuntu
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit
root@ubuntu:/boot/grub#

[/B]
[/INDENT]then rebooted. so far so good or so i thought. got a wee bit further than before but still got stuck w/ this:[INDENT][B][COLOR=Red]Root from (hd0,0) ext3 ce188a9f-a709-44fe-69f-197770b4606c
[/COLOR][/B][/INDENT]pressed 'C' to try and manipulate events during this time but nothing happened.

that's pretty much as far as i got. couldn't find anybody else w/ the exact same prob so here i am at ur mercy... :)

again, complete n00b. so please forgive me if i overlooked sth really simple... 'cause i kinda like to do that every now and then  :redface:. despite this prob, love the OS and hoping someone can help me get this baby up and runnin'. thanks in advance.

ps video card stopped working when i rebooted after the last step (above). 1st time it happened. was ok after i took out the card and put it back again. probably nothing to do w/ Ubuntu but just in case...

---

### Post by lindsay7 on 2009-09-06
Have you reset the bios to start off of the hard drive first and not the usb?

---

### Post by gagagoogoo on 2009-09-06
yup. knew just enough to do that :)

is this really really weird for Ubuntu or is my prob so retarded that nobody can be bothered to answer? seriously, i have no clue. so would appreciate any input.

---

### Post by lindsay7 on 2009-09-06
can you post the resulte of typing this command in the terminal of

cat /boot/grub/menu.lst  (that is the lower case letter L)


The terminal can be found under Applications/Accessories.

---

### Post by gagagoogoo on 2009-09-06
thanks for taking the time :)

this is what i got back when i did what u just said:

[INDENT]root@ubuntu:/boot# cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
[COLOR=Red]root@ubuntu:/boot# ls /boot
abi-2.6.28-11-generic     System.map-2.6.28-11-generic
config-2.6.28-11-generic  vmcoreinfo-2.6.28-11-generic
memtest86+.bin
[/COLOR][/INDENT]
i can't even see GRUB in the /boot directory. not sure, but i thought i was able to access it before... 

argh. i'm sorry. haven't slept for 48 hrs now and getting a bit slow in the head... will look at it again tomorrow but that's what i got back from Ubuntu atm.

thanks again. g'nite!

---

### Post by presence1960 on 2009-09-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by gagagoogoo on 2009-09-07
sorry for the late reply. just went through about 2 days worth of sleep :)

anyway, here's the result:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 10490445.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe86d1a12

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    10,490,444    10,490,382  83 Linux
/dev/sda2          77,031,675    80,405,324     3,373,650   5 Extended
/dev/sda5          77,031,738    80,405,324     3,373,587  82 Linux swap / Solaris
/dev/sda3          10,490,445    77,031,674    66,541,230   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4005 MB, 4005527552 bytes
255 heads, 32 sectors/track, 958 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf98aec39

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,817,279     7,817,248   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ce188a9f-a709-44fe-b49f-197770b4606c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="F7CA-47EC" TYPE="vfat" 
/dev/sda5: TYPE="swap" UUID="be93b728-5126-49be-a9bd-c88d71292b3d" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="TOSHIBA" UUID="BA7A-4755" TYPE="vfat" 

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
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=ce188a9f-a709-44fe-b49f-197770b4606c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ce188a9f-a709-44fe-b49f-197770b4606c

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
uuid        ce188a9f-a709-44fe-b49f-197770b4606c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ce188a9f-a709-44fe-b49f-197770b4606c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ce188a9f-a709-44fe-b49f-197770b4606c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ce188a9f-a709-44fe-b49f-197770b4606c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ce188a9f-a709-44fe-b49f-197770b4606c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ce188a9f-a709-44fe-b49f-197770b4606c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=be93b728-5126-49be-a9bd-c88d71292b3d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.8GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   1.9GB: boot/initrd.img-2.6.28-11-generic
   1.8GB: boot/vmlinuz-2.6.28-11-generic
   1.9GB: initrd.img
   1.8GB: vmlinuz
```

(was wondering how ppl got the code in the box... thx!)

after the initial the postings i have now created a partition as can be seen above (trying to see if that *persistence* thing can be done w/ relevant data being saved on the HD instead of the USB).

anyway, would appreciate any feedback. still in me honeymoon period w/ Ubuntu and don't really wanna give up on it. thanks!

---

### Post by presence1960 on 2009-09-07
everything appears to be in order. Try reinstalling GRUB, but don't do it as root. I see you were at a root prompt with the commands you posted above.

Boot from the LIve Cd & choose "try Ubuntu without any changes". When the desktop loads open a terminal and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type **sudo grub**. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,0)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In # 6 use setup (hd0)
```

---

### Post by gagagoogoo on 2009-09-07
i already tried that and was first thing i posted... above. just tried it again and i got the same thing:

```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 
```

---

### Post by presence1960 on 2009-09-07
> **gagagoogoo said:**
> i already tried that and was first thing i posted... above. just tried it again and i got the same thing:

```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 
```

well it succeeded, so GRUB is installed properly. maybe something went wrong with the Ubuntu install. That's all I can think of because your output from the boot info script looks good and according to the text you just posted GRUB is installed. I would try reinstalling Ubuntu.

---

### Post by gagagoogoo on 2009-09-07
will try again. will be the 3rd try so a bit skeptical. or perhaps try another distro and see if the same thing happens. 

was really hoping Ubuntu would work. oh well, thanks anyway.

---

### Post by stalkingwolf on 2009-09-09
First be patient.  The members here are all volunteers and all over the world.  Sometimes it just takes some time for the right one to come along.
Bumping is ok usually once a day is enough.

Second you might try installing 8.04LTS.  I had to do that with my nc8000.
you can also try hitting ESC when it starts grub and using the recovery mode
and fix broken packages.

---

### Post by gagagoogoo on 2009-09-11
apologies if i sounded a bit too rushed. 7 days of constant attempts to fix my pc may have got to me a bit.

regardless, it's up and running now :guitar: 

was more of a hardware issue than anything else. usb install did the trick. i'm afraid can't really contribute much to the topic. thanks anyways.

---

