---
title: "Grub loader not booting my XP part"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by astroboy123 on 2009-04-24
probably very simple for all of you guys out there. but anyway.

i did a fresh install of 9.04 on my first HDD, which has the linux swap as sda1, sda2 has my XP install, sda3 is my linux and sda4 is just a fat32 partition

major minor  #blocks  name

   8        0  195360984 sda
   8        1    3144928 sda1
   8        2  114065280 sda2
   8        3   13018320 sda3
   8        4   65129400 sda4
   8       16  312571224 sdb
   8       17          1 sdb1
   8       21  312563160 sdb5

thats the print out of cat /proc/partitions

now my grub loader has the XP title in its menu.lst file and i believe it has something to do with the "rootnoverify" section in the list file, specifically the (hd0,1)

title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
chainloader    +1 

now i looked at the device.map file and it made sense to me that hd=sda and hd1=sdb my second harddrive. so i changed the (hd0,1) to (hd0,2) to link on with my xp install. yet it didnt work. coming up at the bootloader upon restart with a unknown "something filesystem" i think thats what it said.

so to recap i reinstalled ubuntu 9.04 over 8.10 becasue the old one was bloated (i made sure in the gui that when i was organising the partitions that it would only reformat the sda3  partition for ubuntu, i hoped everything else would stay the same "unformated", and by the looks of it sda4 and sdb5 work fine) went to boot XP from grub to find it doesn't boot.

thanks in advance if someone/people could help.

---

### Post by Sef on 2009-04-24
1) Is XP on the first primary partition?

2) You could copy and paste your file system here.

Applications > Accessories > Terminal

then copy and paste (or type) this command:

```
sudo fdisk -l
``` Small L

---

### Post by astroboy123 on 2009-04-24
Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         416     3144928+  82  Linux swap / Solaris
/dev/sda2   *         417       15504   114065280    7  HPFS/NTFS
/dev/sda3           15505       17226    13018320   83  Linux
/dev/sda4           17227       25841    65129400    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       41346   312567727+   f  W95 Ext'd (LBA)
/dev/sdb5               2       41346   312567696    7  HPFS/NTFS



Hey! thanks for an amazingly quick reply. yeah so thats the print out of the sudo fdisk -l you told me to do...

so is XP on the primary partition? it was before i installed JJ after that i dont know anymore, i know the partition is there but i'd have no clue if its been wiped, i mean that when i did the advanced partitioning in the JJ install i ticked the box that sayed format sda3 which is the linux partiton and i made sure there was no ticking of any box that said to format the rest of the hard drive.The Sda4 and sdb5 is basically an extended partition for my data in windows.


Thank you in adanced.

---

### Post by Sef on 2009-04-24
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         416     3144928+  82  Linux swap / Solaris
/dev/sda2   *         417       15504   114065280    7  HPFS/NTFS
/dev/sda3           15505       17226    13018320   83  Linux
/dev/sda4           17227       25841    65129400    b  W95 FAT32

The swap is on the first primary partition (sda1.)

I would have partitioned this way:

sda1: XP
sda2: Linux
sda3: home
Sda4: swap   

You might be able to clone partitions over to sdb, but I am not sure about that nor which cloner would be the best for you.  Perhaps there is another way too.  I will let someone else answer that question as this is getting out of my area of expertise.

---

### Post by Monkey_Tales on 2009-04-24
Hello,

This supergrub tool will help you with all boot/Mbr/Grub problems in Linux and Windows

[SIZE=2]"We want Linux newbies[/SIZE][SIZE=2] [/SIZE][SIZE=2]to restore their new toy, but also help the Linux advanced user make potentially dangerous operations to the MBR in a safe way. [Super Grub Disk is also a teaching tool to help you learn more about bootloaders and the booting process]("http://www.supergrubdisk.org/wiki/"). After all, booting is the most important thing your computer does -- without the boot process, you would not have an operating system to use![/SIZE]"

_[COLOR=Blue]http://www.supergrubdisk.org/[/COLOR]_

---

### Post by astroboy123 on 2009-04-24
> The swap is on the first primary partition (sda1.)

I would have partitioned this way:

sda1: XP
sda2: Linux
sda3: home
Sda4: swap   

You might be able to clone partitions over to sdb, but I am not sure about that nor which cloner would be the best for you. Perhaps there is another way too. I will let someone else answer that question as this is getting out of my area of expertise.hey thansk for showing interest, the reason i did my partitioning like i did was sda1 was the closest to the outside of the HDD so the swap file was ideal for quicker read-times and all that jazz.

Anyway im sure that the XP install is still there it's just a matter of getting Grub to notice the hard-drive.


> Hello,

This supergrub tool will help you with all boot/Mbr/Grub problems in Linux and Windows

[SIZE=2]"We want Linux newbies[/SIZE][SIZE=2]to restore their new toy, but also help the Linux advanced user make potentially dangerous operations to the MBR in a safe way. [Super Grub Disk is also a teaching tool to help you learn more about bootloaders and the booting process]("http://www.supergrubdisk.org/wiki/"). After all, booting is the most important thing your computer does -- without the boot process, you would not have an operating system to use![/SIZE]"

_[COLOR=Blue]http://www.supergrubdisk.org/[/COLOR]_Hey i ain't sure if your trying to like give me a different loader or something, but it sounds interesting.


EDIT- ok so i found out what the error was when i choose my xp install in the grub 

" Error 13: Invalid or unsupported excutable format"

ok is there a way to reload the grub file like:

sudo grub-reload
or
sudo rcgrub start 

i don't know something like that?

ok so i found update-grub and i think thats what i was looking for.
also i think grub knows that (hd0,2) is the windows partition but i got an error 17: cannot mount selected partition 
when i was trying to boot windows from that partition after i activited it using supergrub tool.

---

### Post by astroboy123 on 2009-04-24
shameless bump.

---

### Post by meierfra. on 2009-04-24
Try 

title Microsoft Windows XP Professional
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


**If that  did not work:**

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)

---

### Post by Sef on 2009-04-24
> shameless bump.


Please wait at least 24 hours with no new posts before bumping your thread.   Bumping too soon may result in a warning or infraction.

---

### Post by astroboy123 on 2009-04-25
> **Sef said:**
> Please wait at least 24 hours with no new posts before bumping your thread.   Bumping too soon may result in a warning or infraction.
sorry dude =)
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 256309504 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63. According to the info in the boot 
                       sector, sdb5 has 625121216 sectors, but according to 
                       the info from fdisk, it has 625135392 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     6,289,919     6,289,857  82 Linux swap / Solaris
/dev/sda2    *      6,289,920   234,420,479   228,130,560   7 HPFS/NTFS
/dev/sda3         234,420,480   260,457,119    26,036,640  83 Linux
/dev/sda4         260,457,120   390,715,919   130,258,800   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   625,151,519   625,135,455   f W95 Ext d (LBA)
/dev/sdb5              16,128   625,151,519   625,135,392   7 HPFS/NTFS

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb5 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: TYPE="swap" UUID="3ee1ccad-3639-4b81-831c-836544256b63" 
/dev/sda3: UUID="ce72d216-93b4-4a7a-8838-5e10a35f10d1" TYPE="ext3" 
/dev/sda4: UUID="D0E5-59DE" TYPE="vfat" 
/dev/sdb5: UUID="8E24E82324E80FCF" TYPE="ntfs" 

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
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lachlan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lachlan)


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
# kopt=root=UUID=ce72d216-93b4-4a7a-8838-5e10a35f10d1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ce72d216-93b4-4a7a-8838-5e10a35f10d1

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
uuid        ce72d216-93b4-4a7a-8838-5e10a35f10d1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ce72d216-93b4-4a7a-8838-5e10a35f10d1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ce72d216-93b4-4a7a-8838-5e10a35f10d1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ce72d216-93b4-4a7a-8838-5e10a35f10d1 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ce72d216-93b4-4a7a-8838-5e10a35f10d1
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Professional
rootnoverify (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=ce72d216-93b4-4a7a-8838-5e10a35f10d1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=3ee1ccad-3639-4b81-831c-836544256b63 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 126.2GB: boot/grub/menu.lst
 131.2GB: boot/grub/stage2
 131.2GB: boot/initrd.img-2.6.28-11-generic
 131.2GB: boot/vmlinuz-2.6.28-11-generic
 131.2GB: initrd.img
 131.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```i'm yet to try out what meierfta said , but ill edit this post after i reboot, so i'd thought i'd post it's current status.

EDIT- i tryed rebooting with what meirefta said and nope, no workie. by looking at that results print out i think grub doesn't know waht type of FS is on sda2 so what file do i have to change for it to recongise the NTFS?

---

### Post by meierfra. on 2009-04-25
> sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda2 and 
                       looks at sector 256309504 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''


It seem that you installed grub to the boot sector of the XP partition.  This deleted  the code necessary for  booting XP. To fix it:


 Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to the Ubuntu desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition and choose
"boot"
"BackupBS"
Type "Y" to confirm
Press  press "q" a few times to quit  testdisk.


Also change your Windows item in menu.lst to

title Microsoft Windows XP Professional
rootnoverify (hd0,1)
chainloader +1


Reboot and see whether you can boot into XP.

---

### Post by astroboy123 on 2009-04-25
> **meierfra. said:**
> It seem that you installed grub to the boot sector of the XP partition.  This deleted  the code necessary for  booting XP. To fix it:


 Download the [testdisk-6.10.linux26.tar.bz2 package]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") to the Ubuntu desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```
Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition and choose
"boot"
"BackupBS"
Type "Y" to confirm
Press  press "q" a few times to quit  testdisk.


Also change your Windows item in menu.lst to

title Microsoft Windows XP Professional
rootnoverify (hd0,1)
chainloader +1


Reboot and see whether you can boot into XP.

It worked! thanks alot! seriously thank you and thanks to the others that tried and did help!

ok so i got a few questions.
What did i do wrong in my install of JJ that went so wrong? for this to happen?
What can i do to make the FS Automount when i log in. like i know that its displayed as a removable HDD but it's not actually mounted. you have to click it and then it mounts so i can access the data?

---

