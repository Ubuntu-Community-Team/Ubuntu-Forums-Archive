---
title: "Cannot boot Windows XP after install Ubuntu"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by johnschong on 2009-08-13
I cannot boot Windows XP after install Ubuntu.

First I've only a hard disk and I have few partitions.

Before install Ubuntu, my hard disk was partition like this:

Windows XP  ------   Free Space  ---------  FAT32

And in the Ubuntu installer, I partition my hard disk like this:

Windows XP  -------  Linux Boot -------------  Linux Swap ---------- Linux /

I've deleted the FAT32 partition.

--------------------------------------------------------------------

Here is a menu part of my /boot/grub/menu.lst

```

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW quiet splash 
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW  single
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

```Why no Winedows XP added?

-----------------------------------------------------------------

fdisk -l :

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1beb1bea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       34089   273811860    f  W95 Ext'd (LBA)
/dev/sda2   *       34090       38913    38748780   83  Linux
/dev/sda5               2       33692   270622926    7  HPFS/NTFS
/dev/sda6           33693       33716      192748+  83  Linux
/dev/sda7           33717       34089     2996091   82  Linux swap / Solaris


```Can any one help me to fix this problem? :):)

---

### Post by johnschong on 2009-08-13
Why my Windows Drive only have WINDOWS, Program Files, Document and Setting, and 

pagefile.sys

Don't have boot.ini

And I try to use the windows disk to fixmbr, but after I put this disk inside and boot, and it's blank after setup is insect.............................

---

### Post by presence1960 on 2009-08-13
it looks like you have your windows on a logical partition. That is not good. To get a more clear look at your setup boot into Ubuntu and download to the desktop the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/"). Once on the desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a results.txt file on the desktop. paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by johnschong on 2009-08-13
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1beb1bea

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   547,639,784   547,623,720   f W95 Ext d (LBA)
/dev/sda5              16,128   541,261,979   541,245,852   7 HPFS/NTFS
/dev/sda6         541,262,043   541,647,539       385,497  83 Linux
/dev/sda7         541,647,603   547,639,784     5,992,182  82 Linux swap / Solaris
/dev/sda2    *    547,639,785   625,137,344    77,497,560  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: UUID="1ff97544-1ebd-452a-8340-a7c6160b132a" TYPE="ext3" 
/dev/sda5: UUID="18886C04886BDF2E" TYPE="ntfs" 
/dev/sda6: UUID="f4f8c4a9-a8a1-4758-87b9-25f2809af9bb" TYPE="ext3" 
/dev/sda7: UUID="67db238b-2454-4d59-8cbe-acbba959f167" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
/dev/sda6 on /boot type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/johnson/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=johnson)


============================= sda6/grub/menu.lst: =============================

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
# kopt=root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW

## default grub root device
## e.g. groot=(hd0,0)
# groot=f4f8c4a9-a8a1-4758-87b9-25f2809af9bb

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW quiet splash 
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW  single
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /memtest86+.bin
quiet

title Windows XP Professional
root (hd0,6)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda6: Location of files loaded by Grub: ===================


 277.3GB: grub/menu.lst
 277.3GB: grub/stage2
 277.1GB: initrd.img-2.6.28-11-generic
 277.1GB: initrd.img-2.6.28-14-generic
 277.1GB: vmlinuz-2.6.28-11-generic
 277.1GB: vmlinuz-2.6.28-14-generic

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
# kopt=root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW

## default grub root device
## e.g. groot=(hd0,0)
# groot=f4f8c4a9-a8a1-4758-87b9-25f2809af9bb

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW quiet splash 
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-14-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW  single
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /vmlinuz-2.6.28-11-generic root=UUID=1ff97544-1ebd-452a-8340-a7c6160b132a ro locale=zh_TW  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f4f8c4a9-a8a1-4758-87b9-25f2809af9bb
kernel        /memtest86+.bin
quiet

title Windows XP Professional
root (hd0,6)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=1ff97544-1ebd-452a-8340-a7c6160b132a /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda6 during installation
UUID=f4f8c4a9-a8a1-4758-87b9-25f2809af9bb /boot           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=67db238b-2454-4d59-8cbe-acbba959f167 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 280.5GB: boot/grub/menu.lst
 280.5GB: boot/grub/stage2
 280.4GB: boot/initrd.img-2.6.28-11-generic
 280.4GB: boot/initrd.img-2.6.28-14-generic
 280.4GB: boot/vmlinuz-2.6.28-11-generic
 280.3GB: boot/vmlinuz-2.6.28-14-generic
 280.4GB: initrd.img
 280.4GB: initrd.img.old
 280.3GB: vmlinuz
 280.4GB: vmlinuz.old

```

You are right, my windows is on logical partition, that mean the installer think this is not a bootable partition?
In Windows, this system drive called D:, not C:

---

### Post by presence1960 on 2009-08-13
I am confused about a couple things. This first:

```
sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst


```

What exactly is on sda6? Your GRUB is pointing to sda6. it looks like sda2 is your Ubuntu partition:

```
sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
```

Your XP is on a logical partition, you may possibly get it booting from GRUB- see [here]("https://www.linuxquestions.org/questions/linux-software-2/grub-windows-on-logical-partition-607114/")

personally I would repartition my hard disk using [gparted Live CD]("http://gparted.sourceforge.net/livecd.php")

Make sure you create a primary NTFS partition for XP. Linux can boot from logical partitions without any extra work- unlike Windows.

Create your partitions first then install. Of course back up any data you don't want to lose. If you have a recovery CD/partition you will have to use that first, which will put your hard disk back to the image that came from the factory. Then you will have to defrag XP and then resize it's partition to create space for Ubuntu. If you need help post back.

---

### Post by johnschong on 2009-08-13
Thank you for your help, sir

That mean I have to add these?

title           Microsoft Windows XP
root            (hd0,7)
savedefault
makeactive
chainloader     +1
My cause is hd(0,7)?

grub is on sda6 because I have part a 200 mb ext3 and mounted it to /boot and sda2 is mounted to /

---

### Post by presence1960 on 2009-08-13
> **johnschong said:**
> Thank you for your help, sir

I just got laid off yesterday from my full time job, so I have some free time. I am going to my part time job in a little. I will be back  around 9 PM EST this evening after Tae Kwon DO.

---

### Post by johnschong on 2009-08-13
I am a Chinese, live in HK, ha

---

### Post by johnschong on 2009-08-13
I have a try already, but it doesn't work.

is say Error

Thanks again...

I probably will backup my data, and delete all partition and rebuild two primary partition for windows and linux.

I am enjoy in Ubuntu's function, it looks can drag some hidden function out by some method.

---

### Post by ronaldprettyman on 2009-08-13
> **johnschong said:**
> I have a try already, but it doesn't work.

is say Error

Boot xp cd
Restore mod
x:\fixmbr
x:\fixboot
XP FIXED

Boot Ubuntu install cd
Mount root partition
eg.
```
sudo mount /dev/sda2 /mnt
```
your want to check to see what partition is your root partition, 
```
fdisk -l
```
it will be the big ext3 one
maybe hda3 sda2 sda4
what ever it is just add /dev to the beginning like above
then chroot into the root partition
```
mount -o bind /dev /mnt/dev
mount -o proc /mnt/proc
chroot /mnt /bin/bash
```
Reinstall grub
```
grub-install /dev/sda
```
replace sda with your main disk, hda or sda

---

### Post by johnschong on 2009-08-13
> **ronaldprettyman said:**
> Boot xp cd
Restore mod
x:\fixmbr
x:\fixboot
XP FIXED

Boot Ubuntu install cd
Mount root partition
eg.
```
sudo mount /dev/sda2 /mnt
```your want to check to see what partition is your root partition, 
```
fdisk -l
```it will be the big ext3 one
maybe hda3 sda2 sda4
what ever it is just add /dev to the beginning like above
then chroot into the root partition
```
mount -o bind /dev /mnt/dev
mount -o proc /mnt/proc
chroot /mnt /bin/bash
```Reinstall grub
```
grub-install /dev/sda
```replace sda with your main disk, hda or sda


It looks useful, however, I tried to boot with xp disc, boot it displayed nothing only a blank black screen after the prompt "Setup is insecting................."

---

### Post by johnschong on 2009-08-13
According to presence1960:

He will format his disk if he were me.

So I will reinstall windows and ubuntu tomorrow.

---

### Post by ronaldprettyman on 2009-08-13
> **johnschong said:**
> It looks useful, however, I tried to boot with xp disc, boot it displayed nothing only a blank black screen after the prompt "Setup is insecting................."

Are you using a raid setup for your disk?

---

### Post by johnschong on 2009-08-13
Sure not, I don't have so many money:)

---

### Post by presence1960 on 2009-08-13
the problem is that XP is installed on a logical partition inside an extended partition. I posted a link with a method some have used to get Windows to boot from GRUB when installed on a logical partition. Most people who have tried to boot XP on a logical partition from GRUB have failed. Only a handful have been successful. Here is the link: [https://www.linuxquestions.org/questions/linux-software-2/grub-windows-on-logical-partition-607114/](https://www.linuxquestions.org/questions/linux-software-2/grub-windows-on-logical-partition-607114/)

I just got laid off from my full time job. One day when I get bored I am going to redo my machine and install XP on a logical partition and see if the edit of boot.ini suggested in that link works or not.

P.S. I just looked at my partition table and I don't have to redo the whole machine. I already have an extended partition with jaunty, swap & Mint 5 on logical partitions. I can use the Mint 5 partition to install XP and then see if the directions from that link will actually allow me to boot XP installed to a logical partition from GRUB.

I also am aware when there are 2 versions of windows installed one becomes a logical partition and the bootloader of one serves to boot both versions. That is an entirely different scenario and does not apply here.

He is missing boot.ini & NTLDR, even if he recovers them he probably can't boot XP from the logical partition unless he follows the advice on that link.

---

