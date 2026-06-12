---
title: "GRUB Error 17"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by rvelez83 on 2009-04-09
"**GRUB Loading stage 1.5. GRUB loading, please wait... Error 17**"

:confused:
That is the message I'm getting right after installing Linux Mint 6 (**Ubuntu 8.10**) in dual boot with Windows XP. *I already tried setting the IDE type from AUTO to USER as suggested in some other post but still get the same message.* (Any help is greatly appreciated).

_Motherboard_: ASUS CUV4X-DLS
_BIOS_: Award Medallion v6

---

### Post by rvelez83 on 2009-04-09
BTW, this is *before* the GRUB menu even appears, not after selecting Linux or Windows.

---

### Post by ronparent on 2009-04-09
All that error message is saying is that the ubuntu partition containing grub is not being found. If you never managed a successful boot after install, it may mean that the instll may be out of range for the bootloader. Booting the live cd and starting a terminal run the command as follows:

sudo fsdisk -l

And post the output here.

---

### Post by rvelez83 on 2009-04-09
*I will being doing that in moment and posting the results.*

But since you mentioned partitions, I want to make a side note; when I installed, I did a manual partition instead of auto. I've done it before, I had an NTFS partition (WinXP) and with the free space I made a root, swap & home partition. I set all 3 of those to primary, does that have anything do with what you mentioned about being out of range? I've done it before, yet not on this system and no, it has not managed a successful start after install.

---

### Post by ronparent on 2009-04-09
The grub bootloader in mbr, in many cases contains only enough information to find the ubuntu partition only if the beginning of the partion is within 137Gb of the beginning of the disk. Incidently my deslexic hands should have entered:

sudo sfdisk -l

This an information only command that will produce information that a reader of your post might see what the problem is.

---

### Post by rvelez83 on 2009-04-09
Ok, I'll be trying that soon. Btw, now that you mention gigabytes, the HD is 200GB, after installing WinXP only 10% (about 20GBs) were left for the Linux partitions.

---

### Post by ronparent on 2009-04-09
If that is the problem, there are workarounds that should fix you up.

---

### Post by rvelez83 on 2009-04-09
Here is the output from running the command you told me ron: ** sudo sfdisk -l**
(*btw, I also attached the grub files from /boot/grub*)


Disk /dev/sda: 1020 cylinders, 63 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/61/60 (instead of 1020/63/62).
For this listing I'll assume that geometry.
Units = cylinders of 1873920 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   1089-   1090-   1993604+   6  FAT16
        start: (c,h,s) expected (0,4,8) found (0,3,59)
        end: (c,h,s) expected (1023,60,60) found (988,60,60)
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/sdb: 24321 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  21708   21709- 174377511    7  HPFS/NTFS
/dev/sdb2      21709   22455     747    6000277+  83  Linux
/dev/sdb3      22456   22828     373    2996122+  82  Linux swap / Solaris
/dev/sdb4      22829   24320    1492   11984490   83  Linux

---

### Post by ronparent on 2009-04-09
The text file manu.lst is instructing grub to find ubuntu on sda2 and window on sda1. That is not what sfdisk indicates. They are respectively installed on sdb2 (or sdb4 ?) and windows on sdb1. Have you changed your boot order in bios? My guess is that there is no boot loader on sda and so the computer is by default on sdb. Since there do not appear to be any operating systems on sda grub produces the error 17. You have two choices 1) change the boot order in bios so what is now sdb becomes sda. In which case your computer will probably boot. 2) Let me know that you want to keep the current boot order in bios. In that case I or someone else could  instruct you on how to reset grub to boot by uuid.

---

### Post by rvelez83 on 2009-04-09
I understand about sdb and sda at Linux level. But I'm not quite sure how that would interpret at BIOS level.

My drives are set as follows:
There is only one **HD** and its set to **Primary Master**.
Nothing installed on **Primary Slave**.

There is a **Disc drive** on **Secondary Master**
and there is **another Disc drive** on **Secondary Slave**

The boot order is set for Disc drive to boot first (was necessary obviously to have the install disc boot) and the HD comes second. I did at one moment change the boot order on the BIOS as part of troubleshooting, that was after it had failed anyways (prior to any BIOS changes).

So any hint on how to exactly do what you suggested in the BIOS?

---

### Post by ronparent on 2009-04-09
Your situation is totally baffling. The output of sfdisks -l shows TWO hd's. I can't thisk of under what circumstances that would occur if there is only one. Have you looked under the hood to verify only one hd is present? What is your pc?

---

### Post by meierfra. on 2009-04-09
> disk /dev/sda: 1020 cylinders, 63 heads, 62 sectors/track
Warning: The partition table looks like it was made
for C/H/S=*/61/60 (instead of 1020/63/62).
For this listing I'll assume that geometry.
Units = cylinders of 1873920 bytes, blocks of 1024 bytes, counting from 0

Device Boot Start End #cyls #blocks Id System

This looks like a flash drive or some other small device. Do  you a flash drive, or zip drive or anything like that plugged in? If yes, remove it and try booting again.

---

### Post by rvelez83 on 2009-04-09
[**meierfra.**]  You are correct about the Flash drive yes, but it was only on in that moment to copy over the grub files I attached in an earlier post.


[**ronparent**]  Its a just a generic computer and yes it has 1 HD connected to the primary IDE and it has the 2 disc drives both on the secondary drive.

---

### Post by meierfra. on 2009-04-09
It starts to sound like a bios issue. But let's check out whether grub is configured correctly:

Boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags)  The results of that script will help clarify your setup .

---

### Post by rvelez83 on 2009-04-10
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 6 Felicia
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7363dd21

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   348,755,084   348,755,022   7 HPFS/NTFS
/dev/sdb2         348,755,085   360,755,639    12,000,555  83 Linux
/dev/sdb3         360,755,640   366,747,884     5,992,245  82 Linux swap / Solaris
/dev/sdb4         366,747,885   390,716,864    23,968,980  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="A2209E7B209E55DF" TYPE="ntfs" 
/dev/sdb2: UUID="690e2d29-5ea3-4ec4-9104-df50d85e9c05" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="8676cabc-6320-455e-baea-edbd699873b2" TYPE="swap" 
/dev/sdb4: UUID="cdc54308-b6f5-4d2d-bbf2-52518ecd8ee8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mint/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mint)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdb2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/default.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
##      altoptions=(single-user) single
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

title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,1)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda2 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=690e2d29-5ea3-4ec4-9104-df50d85e9c05 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=cdc54308-b6f5-4d2d-bbf2-52518ecd8ee8 /home           ext3    relatime        0       2
# /dev/sda3
UUID=8676cabc-6320-455e-baea-edbd699873b2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 184.4GB: boot/grub/menu.lst
 184.5GB: boot/grub/stage2
 184.5GB: boot/initrd.img-2.6.27-7-generic
 184.5GB: boot/vmlinuz-2.6.27-7-generic
 184.5GB: initrd.img
 184.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sda sdc sdd sde

---

### Post by meierfra. on 2009-04-10
Grub is configured correctly, so we have to hunt for other causes.

A few things to try:

1)   You only  seemed to have one hard drive plugged in when you run the boot_info_script, but still the  drive was reported as /dev/sdb.  So maybe your hard drive is not plugged in correctly or plugged into the wrong place. Or is there still something else plugged in which could confuse  Ubuntu?

2)   Run a file system  check:

Boot from the LiveCD, open a terminal
```
sudo umount /dev/sdb2
sudo e2fsck -fyv /dev/sdb2
```
(it's ok if the first command returns "/dev/sdb2 is not mounted")

3) Check out your bios one more time. Look for setting related to  "LBA", "AHCI", "IDE", "RAID" . Try out various setting, but make sure to record the original settings. 

4)  Your boot files are  beyond the 137 GB limit, which can cause grub error 18  and in some rare cases also grub error 17.  So if all else fails you might consider reinstalling and create a small 200 MB boot partition at the beginning of the hard drive

---

### Post by rvelez83 on 2009-04-15
Without doing anything else to this installation. I took a HD I have for testing purposes and I installed it with Linux alone. It booted perfectly.

Would that then confirm what you say in:
"*4) Your boot files are beyond the 137 GB limit,...*" ?

---

### Post by meierfra. on 2009-04-15
> Would that then confirm what you say in:
"4) Your boot files are beyond the 137 GB limit,..." ? 

Not really. I still think you should work through 1)-4) from my previous post, in particular since creating a separated boot partition will be the most work. At least, do 2) before you try 4)..

---

### Post by donpedrodos on 2009-05-03
> => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
Your bootinfo summery shows a disk named "/dev/sdb"

Looking inside your menu.lst
> kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda2 ro quiet splash 
There is the root set on "/dev/sda#"

So Grub finds a **SDB** as the drive and you are trying to point to a **SDA**-drive.

Could this be the problem?

I find Grub somehowe very confusing about disk name/numbering.
i still stugle with how to find out about what disk belongs to what hd# number.
By example, a sda does not mean hd0, could be hd3 or so :confused:
Also in one list there could be a hda but in another list it is suddenly a sdb :confused:
What to follow as being correct?

---

### Post by meierfra. on 2009-05-03
> By example, a sda does not mean hd0, could be hd3 or so
(hd3) is the notation used by Grub at boot up. Grub at boot up gets its information from the bios and (hd3) just means the fourth hard drive in the boot priority order in the bios.

sda is used by Ubuntu.  The name "sda" is assigned by the kernel during boot up according to the "udev" rules.  The kernel does not know the boot order in the bios, so there is no way to ensure that  (hd0) means sda.


> What to follow as being correct?

You have to first figure out which program  actually looks at the instruction:

 > title Linux Mint 6, kernel 2.6.27-7-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet


The line "root (hd0,1)" is read by  Grub during boot up.  Grub uses "(hd?,?}" to denoted hard drives.   That why  "(hd0,1)" appears  here. (hd0,1) means the second partition on the first hard drive.   Since only one hard drive is plugged in, this will be the Linux Mint partition.

The second line when calls the kernel on the Linux Mint partition. Grub does not read the "root=/dev/sda2" instruction, but just passes it on to the kernel. So to figure out whether "/dev/sda2" is correct or not, we would have to know what name the Linux Mint kernel assigns to the Linux Mint partition. Unfortunately, we do not know that. We only know that the kernel on the LiveCD assigns /dev/sdb2 to  Linux Mint partition.

But at this stage it does not really matter whether "root=/dev/sda2" is correct.  Since grub does not read it, a wrong "root=/dev/sda2" cannot cause a Grub error. It would cause an error message from the kernel.

So once the Grub error 17 has been cured, one just has to wait and see whether to kernel complains about the "root=/dev/sda2".

---

