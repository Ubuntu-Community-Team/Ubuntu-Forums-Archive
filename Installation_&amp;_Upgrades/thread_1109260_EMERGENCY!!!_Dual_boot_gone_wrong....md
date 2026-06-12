---
title: "EMERGENCY!!! Dual boot gone wrong..."
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by gundam1965 on 2009-03-28
Alright guys, I need some critical help. I just installed Ubuntu 8.04 on my home desktop, attempting to dual boot My vista 64bit business. I was following this guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3)

It was fairly straight forward and basically said partition and install, the grub boot loader would take care of the rest. I already had a partition set aside when I first set up my computer, so i just threw in my disc and got started.

OK, my partition I had originally set aside was 250gb, and I decided it would be overkill, so I used a guided partition that took 50Gb from my vista partition and would make that my Linux partition, I figured I would just reallocate the other 250gb partition later. The install went smoothly and I just rebooted a few minutes ago. Here comes the problem.

The grub boot loader doesn't give me the vista boot option, only 3 linux options, the regular boot, recovery boot, and something else. I really need some help. I know very little about this kind of thing and have only used basic command line things. I don't really know what information or files to post that show information.

i know the partitions are still there and haven't changed, they are listed under places in linux and i can access them. Please someone help me get my vista back...

---

### Post by prezbedard on 2009-03-28
I'm thinking you may be able to fix this by editing menu.list under /boot/grub

You will need to know the drive/partion that windows is on. Hopefully someone more knowledgeable can chime in on this.

---

### Post by Cope57 on 2009-03-28
Backups on CD / DVD or external hard drives, and then there never is a emergency.

Just a reinstall.

---

### Post by tommcd on 2009-03-28
So can you boot up Ubuntu? If so, open a terminal (applications > accessories > terminal) and post the output of:
```
sudo fdisk -l
```
Then run:
```
cat /boot/grub/menu.lst
```
and then post everything after the line:
### END DEBIAN AUTOMAGIC KERNELS LIST

The fdisk command will list your partitions. If Vista is still there it will tell us where it is. The menu.lst file is where the menu entry to boot Vista is. It should be right after the "END DEBIAN AUTOMAGIC KERNELS" line.

(I'll be going out for a bit. I'll pick this up a bit later in case no one else helps you fix it).

---

### Post by gundam1965 on 2009-03-28
sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39e939e8

Device Boot Start End Blocks Id System
/dev/sda1 1 6374 51199123+ 83 Linux
/dev/sda2 6375 121108 921600855 f W95 Ext'd (LBA)
/dev/sda5 * 25497 82604 458719978+ 7 HPFS/NTFS
/dev/sda6 89238 121108 256003776 7 HPFS/NTFS
/dev/sda7 6375 24715 147324019+ 83 Linux
/dev/sda8 24716 25496 6273351 82 Linux swap / Solaris

Partition table entries are not in disk order


cat /boot/grub/menu.lst

## ## End Default Options ##

title Ubuntu 8.04.2, kernel 2.6.24-23-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=9b9a908d-bf21-4b8e-8466-8994f3f7ee91 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet

title Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=9b9a908d-bf21-4b8e-8466-8994f3f7ee91 ro single
initrd /boot/initrd.img-2.6.24-23-generic

title Ubuntu 8.04.2, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST 

nothing after that

---

### Post by meierfra. on 2009-03-28
Did you delete or reformat any partition while installing Ubuntu? It looks like you no longer have the partition containing the Vista boot files.

To confirm this diagnosis  suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by gundam1965 on 2009-03-28
Here goes:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x39e939e8

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   102,398,309   102,398,247  83 Linux
/dev/sda2         102,398,310 1,945,600,019 1,843,201,710   f W95 Ext d (LBA)
/dev/sda5    *    409,593,303 1,327,033,259   917,439,957   7 HPFS/NTFS
/dev/sda6       1,433,592,468 1,945,600,019   512,007,552   7 HPFS/NTFS
/dev/sda7         102,398,436   397,046,474   294,648,039  83 Linux
/dev/sda8         397,046,538   409,593,239    12,546,702  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8c6f75b2-71db-43d2-b1ad-d11e8d360635" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="822873DB2873CD23" TYPE="ntfs" 
/dev/sda6: UUID="7E401A394019F91B" TYPE="ntfs" 
/dev/sda7: UUID="9b9a908d-bf21-4b8e-8466-8994f3f7ee91" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="d9bf86b9-32ee-4c67-bfc3-b4776c312ed1" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jadams/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jadams)
/dev/scd0 on /media/cdrom1 type udf (ro,nosuid,nodev,utf8,user=jadams)
/dev/sda6 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=9b9a908d-bf21-4b8e-8466-8994f3f7ee91 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=9b9a908d-bf21-4b8e-8466-8994f3f7ee91 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=9b9a908d-bf21-4b8e-8466-8994f3f7ee91 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+

root        (hd0,6)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows Vista
root            (hd0,4)
chainloader +1

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=9b9a908d-bf21-4b8e-8466-8994f3f7ee91 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=d9bf86b9-32ee-4c67-bfc3-b4776c312ed1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 108.2GB: boot/grub/menu.lst
 108.3GB: boot/grub/stage2
 108.3GB: boot/initrd.img-2.6.24-23-generic
 108.3GB: boot/vmlinuz-2.6.24-23-generic
 108.3GB: initrd.img
 108.3GB: vmlinuz
```

---

### Post by gundam1965 on 2009-03-28
oh, btw, the lines after ### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows Vista
root            (hd0,4)
chainloader +1

I put those there as per advice from another forum.  It didnt work.

---

### Post by brayden13 on 2009-03-28
did you try having it like this:
```
title Windows Vista
root (hd0,1)
chainloader +1

```
Well that might work as. I'm not 100% sure that will work. I'll have a look at my boot loader for example now.
I had a look at it and for some reason but i do not really care i have two windows vista come up when i use the grub dualboot. but as i said i do not care. one of them is in hd0,0 and the other is in hd0,1. they both work for me. it might work for you.

---

### Post by tommcd on 2009-03-28
It does look like you deleted a partition at some point. Your /dev/sda5 is physically after /dev/sda8 according to fdisk. It looks like Vista may have ended up on a logical partition also. It is difficult to boot Windows from logical partitions. I think it is possible though. 
Try changing **root** to **rootnoverify** in your grub menu entry like this:
```
title Windows Vista
rootnoverify (hd0,4)
chainloader +1

```
You could also try adding **makeactive** like this:
```
title Windows Vista
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1
```
If none of these work, please try to post what errors you get when you try to boot Vista.

---

### Post by gundam1965 on 2009-03-28
Boy, sounds like this install went seriously bad.  I'l post more as I try things, working on 

title Windows Vista
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1

the other one didnt work

---

### Post by gundam1965 on 2009-03-28
alright that didnt work either

title Windows Vista
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1

Error 12: Invalid Device Requested

---

### Post by ronparent on 2009-03-28
gundam1965

The document below seems to explain your predictament. Look under error #12.

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by meierfra. on 2009-03-28
Ok. Your boot files are  indeed missing. To fix your problem follow this tutorial
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)

In Step 1 use

title Windows Vista
rootnoverify (hd0,4)
chainloader +1


In Step 2 skip the  command "E:\boot\bootsect.exe /nt60  C:"

You have to carry out Step 3 (and  the device name for your Vista drive is  indeed /dev/sda)

---

### Post by gundam1965 on 2009-03-29
working on it now, had to download a vista recovery last night cause i cant find mine.  God I hope it works.  If it does, i'm buying drinks all around.

---

### Post by gundam1965 on 2009-03-29
meierfra, your a lifesaver.  If we ever meet i'm buying you a drink.

---

### Post by meierfra. on 2009-03-29
> meierfra, your a lifesaver

Glad to be of help. Have fun with Vista and Ubuntu.

---

### Post by tommcd on 2009-03-29
> **meierfra. said:**
> Ok. Your boot files are  indeed missing. To fix your problem follow this tutorial
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)


Meiefra,
Just out of curiosty, how did you determine the boot files were missing? The output from Gundam's boot info script said for /dev/sda5:
> 
Boot files/dirs:   /Windows/System32/winload.exe



So did that mean the boot files were missing? Or was it something else?

Good fix btw!

---

### Post by meierfra. on 2009-03-30
> how did you determine the boot files were missing? The output from Gundam's boot info script said for /dev/sda5:
Quote:
Boot files/dirs: /Windows/System32/winload.exe

So did that mean the boot files were missing?

Yes.   "bootmgr" and "Boot" are missing.

Actually, the " fdisk" output already told me that the boot files were missing:  Vista always puts those files on a **primary** fat or ntfs partition and  the OP does not have  such a partition

---

