---
title: "Need specifics on where to install boot loader."
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by wootcat on 2009-06-11
Simple question first. If I'm specifying where to install the boot loader, Ubuntu gives me the choice between the "root" of the drive (dev/sda) or the OS of the drive (dev/sda1). Which one should I choose?

I'm a Linux newbie who's been running a dual XP/Ubuntu system for a few months now. I finally installed a new HD and am trying to make a dual boot system with XP on one drive and Ubuntu on the other.
 
I'm getting a GRUB Error 17 and am trying to troubleshoot.

One thing I found in my searches is that I may have messed up my boot order and maybe I'm getting the error because the boot loader was installed in the wrong place. My system has 2 SATA drives (both 250GB) and 1 60GB IDE). My XP/Ubu combo is on one 250GB drive and the new one I want to put the "standalone" Ubuntu on is the other 250GB.

Thanks for quick help!!!!

---

### Post by dstew on 2009-06-11
If you want to dual boot using the grub boot loader, then pick /dev/sda. This will put the grub stage 1 file into the master boot record (MBR) of that drive. If that is the drive that the BIOS boots, then grub will start and get its stage 2 and menu from the Ubuntu installation, which will present you with the grub menu.

If when you try to boot you get error 17, then grub is probably mis-installed. You can re-install grub from a Live CD boot. See [this page]("http://ubuntuforums.org/showthread.php?t=224351"). I should warn you that if you really have two Ubuntu installations in your computer, you will have to figure out which one has the menu file that you want to use. If you just installed a new distribution on your second disk, you want to use the menu in that Ubuntu. You might need to use the **geometry** command or other tricks from the grub command line to figure out which disk is which, after you try the **find** command.

---

### Post by dE_logics on 2009-06-11
Pick the partition which's flagged as boot (or where where the system boots by default).

---

### Post by wootcat on 2009-06-11
Thanks!

My re-install did not work...still getting the Error 17.

I will try your suggestion. While I will have 2 Ubuntu installs on there now, I will be getting rid of the original install as soon as I can get all the files transferred over. My first install was using the method where Ubuntu is installed on the same partition as XP and they sort of co-habitate. Now I just want to give Ubu its own space and wipe the shared install as soon as I can.

---

### Post by dstew on 2009-06-11
Did you re-install grub using the Live CD method?

---

### Post by wootcat on 2009-06-11
Is there an easy way to pair up the different ways Ubuntu refers to disks? How can I find out if (hd1,0) is /dev/sdb1 or sdb2 or sdb3?

---

### Post by wootcat on 2009-06-11
> **dstew said:**
> Did you re-install grub using the Live CD method?

Not yet. I originally posted in the middle of a full reinstall. I am trying the LiveCD method now, which is why I'm trying to find out where GRUB is currently working from. 

> find /boot/grub/stage1 is returning (hd1,0)

so I need to find out which drive that is, but all I can find through other sources is the sdb1-3 labels.

---

### Post by merlinus on 2009-06-11
(hd1,0) is the second hdd, first partition (sdb1).

---

### Post by wootcat on 2009-06-11
Okay, so if my system is like this...

sda1 (first hdd, first partition, XP installed (Ubu installed inside))
sdb2 (2nd hdd, first partition, fresh Ubu install)
sdc1 (3rd hdd, first partition, extra stuff)
sdc2 (3rd hdd, 2nd partition, extra stuff)

... I should want GRUB installed on sda1, correct? So does that mean I want GRUB to install on (hd0,0)?

Thanks!

---

### Post by merlinus on 2009-06-11
Looks good to me.  But what about your two ubuntu installations?

---

### Post by wootcat on 2009-06-11
Heh. I haven't gotten that far yet. This is the first time I've done anything like this!

I was hoping after I got back to a bootable system, I would transfer over the files and then uninstall the Ubu install that's on the first hdd.

My next question is: if I reinstall GRUB to (hd0,0), do I also need to uninstall it from (hd1,0) or is that automatically taken care of in the instructions I was pointed to [here]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by dstew on 2009-06-11
I think you want to install grub to the MBR of the first (boot) disk. If so, you commands should be:```
root (hd1,0)
setup (hd0)
```The root command tells the installer where grub's stage 2 and menu are. The setup command tells the installer where to but the stage 1 of the bootloader.

---

### Post by merlinus on 2009-06-11
+1

I got confused by the OP's two ubuntu installations.

---

### Post by wootcat on 2009-06-11
Using [these]("http://ubuntuforums.org/showthread.php?t=224351") instructions, I first tried installing GRUB to (hd0,0) but got an Error 17 in the Terminal. I then tried dstew's commands and while that did run and appeared to work, upon rebooting I still got the Error 17 during boot.

---

### Post by merlinus on 2009-06-11
You might check the boot order of your hdds in bios.

Also, post /boot/grub/menu.lst

---

### Post by dstew on 2009-06-11
Do you get a grub menu? Or, do you get error 17 before any menu appears?

---

### Post by wootcat on 2009-06-11
My boot order is:

sda
sdb
sdc

Forgive me from being totally neo, but I tried /boot/grub/menu.lst and got "No such file and directory", there's not even a grub directory.

---

### Post by wootcat on 2009-06-11
> **dstew said:**
> Do you get a grub menu? Or, do you get error 17 before any menu appears?

Before the grub menu.

---

### Post by merlinus on 2009-06-11
```

cat /boot/grub/menu.lst

```

---

### Post by wootcat on 2009-06-11
> ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 
Is what I get. Could this be because of running from the LiveCD?

---

### Post by wootcat on 2009-06-11
If I can't get this figured out today and I'm needing to access some of my Windows files, is there a way to at least get my system back to booting as it was so I can get to my Windows stuff (sacrilege!) Ideally, in a way we can continue to troubleshoot this, but if not, I can always try a reinstall later with what I've learned here.

And again, I can't thank you all enough for your help!

---

### Post by merlinus on 2009-06-11
Boot from windows cd, choose recovery (or restore), and then fix mbr (or repair boot sector).

Something like those menu choices.....  I haven't used windows in a loooooonggg time.

---

### Post by wootcat on 2009-06-12
I tried booting from my Windows CD. The only option that appeared to be right was Automated Recovery. When that loaded, it asked me to insert the Windows Automated System Recovery Disk (floppy), which I don't have. 

So, for right now, I'm stuck in LiveCD mode and still getting the Error 17 messages if I try to boot off of hdd.

One odd thing I noticed. If I told the system to boot from CD and I let the "Press any key to boot from CD" prompt time out, I got my old boot loader screen. If I selected Windows from there, the system turned around and rebooted, so that didn't work either, but I was surprised to see that boot loader screen.

Any idea why I can't seem to find the menu.lst?

---

### Post by merlinus on 2009-06-12
Boot into ubuntu, open a terminal and enter:

```

cat /boot/grub/menu.lst

```If you are running from the live cd, then this file will not exist, as it resides on your ubuntu partition which is not mounted.

You can mount your ubuntu partition manually, as long as you know which one it is on.

```

sudo fdisk -l

```

should tell which one.

---

### Post by wootcat on 2009-06-12
Right now I can't boot anything, all this I'm doing now is from the LiveCD.

Here's the menu.lst from the NEW Ubuntu I installed.

```
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
# kopt=root=UUID=ca687dac-28f8-4656-9ef9-e0f469a055f0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ca687dac-28f8-4656-9ef9-e0f469a055f0

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
uuid		ca687dac-28f8-4656-9ef9-e0f469a055f0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ca687dac-28f8-4656-9ef9-e0f469a055f0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ca687dac-28f8-4656-9ef9-e0f469a055f0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ca687dac-28f8-4656-9ef9-e0f469a055f0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ca687dac-28f8-4656-9ef9-e0f469a055f0
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

---

### Post by merlinus on 2009-06-12
If you look at the end of the file, you will see that there are two entries for windows.  Which is the correct one?

This may help to identify which one is correct:

```

sudo fdisk -l
df -h
mount

```

---

### Post by wootcat on 2009-06-12
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
chainloader	+1

```

This is the correct one.

---

### Post by merlinus on 2009-06-12
Then delete the other one, and restart.

---

### Post by louieb on 2009-06-12
Changing the boot order of you hard drives is a common reason to get grub error 17.

Are your drives all the same (sata or pata)  a mix will sometimes cause the grub installer to be confused. Leading to grub error 17 and others.


Please follow the instructions in this post [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  and post the RESULTS.txt file back here. 

I hope you haven't overwritten the boot code in your XP partition. If its still good then the [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") will be able to boot windows. For that matter it should be able to boot your Ubuntu install too.

---

### Post by wootcat on 2009-06-12
> **merlinus said:**
> Then delete the other one, and restart.

I tried to edit it and save it, but I was not allowed. I don't have permission to save the file.

---

### Post by wootcat on 2009-06-12
> **louieb said:**
> Changing the boot order of you hard drives is a common reason to get grub error 17.

Are your drives all the same (sata or pata)  a mix will sometimes cause the grub installer to be confused. Leading to grub error 17 and others.


Please follow the instructions in this post [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")  and post the RESULTS.txt file back here. 

I hope you haven't overwritten the boot code in your XP partition. If its still good then the [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") will be able to boot windows. For that matter it should be able to boot your Ubuntu install too.

Here is the RESULTS.txt:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

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

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com /wubildr.mbr

sdc2: _________________________________________________________________________

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
Disk identifier: 0x07c707c6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007aa7f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   476,327,249   476,327,187  83 Linux
/dev/sdb2         476,327,250   488,392,064    12,064,815   5 Extended
/dev/sdb5         476,327,313   488,392,064    12,064,752  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb968b968

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    65,529,134    65,529,072   c W95 FAT32 (LBA)
/dev/sdc2          65,529,135   117,226,304    51,697,170   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="36A44AF4A44AB661" TYPE="ntfs" 
/dev/sdb1: UUID="ca687dac-28f8-4656-9ef9-e0f469a055f0" TYPE="ext3" 
/dev/sdb5: UUID="5bde1cfc-dad2-462c-8ff4-4fa388a00b91" TYPE="swap" 
/dev/sdc1: LABEL="DARKSIDE" UUID="5409-B86D" TYPE="vfat" 
/dev/sdc2: LABEL="GHOST2" UUID="1C9E-77B5" TYPE="vfat" 

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
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


==================== sda1/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=36A44AF4A44AB661 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=36A44AF4A44AB661 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=36A44AF4A44AB661 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=36A44AF4A44AB661 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=36A44AF4A44AB661 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


======================== sda1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

c:\wubildr.mbr="Ubuntu"


================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.04"

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.0GB: ubuntu/disks/boot/grub/menu.lst
   3.9GB: ubuntu/disks/boot/initrd.img-2.6.27-11-generic
  20.5GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
   3.5GB: ubuntu/disks/boot/vmlinuz-2.6.27-11-generic
   3.5GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic

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
# kopt=root=UUID=ca687dac-28f8-4656-9ef9-e0f469a055f0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ca687dac-28f8-4656-9ef9-e0f469a055f0

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
uuid		ca687dac-28f8-4656-9ef9-e0f469a055f0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ca687dac-28f8-4656-9ef9-e0f469a055f0 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ca687dac-28f8-4656-9ef9-e0f469a055f0
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ca687dac-28f8-4656-9ef9-e0f469a055f0 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ca687dac-28f8-4656-9ef9-e0f469a055f0
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
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


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
UUID=ca687dac-28f8-4656-9ef9-e0f469a055f0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5bde1cfc-dad2-462c-8ff4-4fa388a00b91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  61.7GB: boot/grub/menu.lst
  61.8GB: boot/grub/stage2
  61.8GB: boot/initrd.img-2.6.28-11-generic
  61.7GB: boot/vmlinuz-2.6.28-11-generic
  61.8GB: initrd.img
  61.7GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

c:\wubildr.mbr="Ubuntu"


================================ sdc1/BOOT.INI: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

c:\wubildr.mbr="Ubuntu"

```

---

### Post by louieb on 2009-06-13
Are you not getting to the GRUB menu? Looks like you should get the menu on sdb1.  And at least Ubuntu on sdb1 should boot.

Can't help with your wubi installs haven't used wubi. but if your hard drive install on sdb2 doesn't boot then the Super Grub disk is your best and easiest bet to get at least that working. Have you tried it yet. 


Two copies of windows will sometimes confuse each other best to use the hide command. Try this

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
[COLOR=Red]unhide (hd0,0)
hide (hd2,0)[/COLOR]
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on [COLOR=Red]/dev/sdc1[/COLOR] ([COLOR=Magenta]was pointing to sdb1[/COLOR])
title        Microsoft Windows XP Professional
[COLOR=Red]unhide (hd2,0)
hide (hd0,0)[/COLOR]
 
[COLOR=Red]root        (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)[/COLOR]
chainloader    +1

```

---

### Post by wootcat on 2009-06-13
> **louieb said:**
> Are you not getting to the GRUB menu? Looks like you should get the menu on sdb1.  And at least Ubuntu on sdb1 should boot.

No, I am not. Although, when I booted from the Windows CD and forgot to hit the key to boot from CD, I did get the GRUB menu, but when I selected Windows, the computer promptly rebooted, so though it did launch, it did not work. But the GRUB menu does not load when I try to boot normally. This is what I see on the boot screen:

```
List all PCI devices 
*(lists them)*
Verifying DMI Pool Data...
GRUB Loading stage1.5.

GRUB loading, please wait
Error 17
```

> Can't help with your wubi installs haven't used wubi.

I have no idea what wubi is.

> but if your hard drive install on sdb2 doesn't boot then the Super Grub disk is your best and easiest bet to get at least that working. Have you tried it yet.

No I have not. From what I'm reading here, it looks like one problem might be the two Windows installs I have (sda1 and sdc1). The sdc1 is really not used for anything and just might be an old install when I was doing some troubleshooting a couple years ago. The whole sdc hdd is not used much (just an extra drive), so do you think I might have better luck if I tried a fresh new Ubuntu install on sdb2 with sdc disconnected completely? 

If I did that, would that mean I wouldn't have to worry about this:

> Two copies of windows will sometimes confuse each other best to use the hide command. Try this

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
[COLOR=Red]unhide (hd0,0)
hide (hd2,0)[/COLOR]
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on [COLOR=Red]/dev/sdc1[/COLOR] ([COLOR=Magenta]was pointing to sdb1[/COLOR])
title        Microsoft Windows XP Professional
[COLOR=Red]unhide (hd2,0)
hide (hd0,0)[/COLOR]
 
[COLOR=Red]root        (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)[/COLOR]
chainloader    +1

```

I have to go out of town Monday evening for a week, so if I can't get this to dual boot reliably by then, I'll have to find some way to get it to just boot back into Windows for the week (or back to the dual boot to the Ubuntu install on sda1 like it was before I tried this fresh install on sdb).

Thanks to everyone trying to help me figure this out!

---

### Post by wootcat on 2009-06-13
If I needed to be able to boot into my Windows on sda1 tonight, is there an easy way while still working on this trouble?

Thanks!

---

### Post by merlinus on 2009-06-13
supergrub is a live disk that should allow you to do this.

---

### Post by wootcat on 2009-06-13
I don't think the supergrub disk is an option for me as the only thing I can run on my computer right now is the Ubuntu LiveCD and I can't eject that to burn the supergrub disk.

---

### Post by louieb on 2009-06-13
If sdc is a pata drive (flat ribbon cable to it) go ahead and disconnect it. or just disconnect it any way.  

You say you got the the grub menu when the win CD was in. Did you try the Ubuntu option then?

You may not know what wubi is but  Ubuntu on sda1 was installed with wubi. (wubi installs Ubuntu inside windows.) 

The two most common ways to change a drives MBR back to where it will will boot windows is the recovery console on a windows CD. and the Super Grub disk. Other way are described here. [IDBS Remove/Replace/Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

---

### Post by wootcat on 2009-06-14
Okay, things are a bit better now. I got another computer and was able to burn a SuperGrub disc. I played around with it for a little while but it was making little sense to me. At one point, it said the disc could help with multiple hdd setups, but only ones with 2 hdds.

I got a little desperate and went ahead and disconnected sdc. On a lark, I thought I'd try letting the computer do it's bootup thing to see if I got the Error 17 message again and to my surprise, I got a GRUB menu and was able to boot into XP and Ubuntu! Just disconnecting that spare drive (with the other unused XP install) worked!

So now I have Ubuntu running (I'm assuming from sdb since I'm not seeing any of the users or settings from the wubi (yay, I know what that means now!) install. My next step is I want to move all the files/settings for all the users on my wubi install to my new standalone Ubuntu install on sdb. 

Strangely, I am 95% certain that when I installed, Ubu found the other users and I set them up, copying over their settings and documents. But now they are not there and my account is the only one. How can I get my wubi accounts and files over to this new install?

Would it be easier to maybe just run the install again without sbc since that appears to be the main cause of the trouble? Please advise.

Thanks again to everyone who helped me out here! I hope someday all this makes a bit more sense to me. The community here has been great and really makes me want to get to a point where I can contribute back.

Oh, and one peculiar thing I noticed about the GRUB menu. Even though sdc is no longer connected, the menu lists Windows Microsoft XP twice. Booting from the first one worked fine, and I haven't tried the 2nd one. I'm not sure why it's there.

Thanks all!

---

### Post by louieb on 2009-06-14
Glad it was a simple fix. Even if it did take days to figure out how to do it.

> **wootcat said:**
> ...about the GRUB menu. Even though sdc is no longer connected, the menu lists Windows Microsoft XP twice...

It was put in the menu when grub was installed. Even though the drives not there the menu has not changed.

You can manually edit it out or run update-grub (I think . not sure).    
to manual edit - brings it up in the text editor where you can remove or comment out the lines. 

```
gksudo gedit /boot/grub/menu.lst
```
to run update-grub
```
sudo update-grub
```

---

### Post by wootcat on 2009-06-14
Okay. Now. :)

I have a wubi-installed Ubuntu on sda1 that I want to eventually remove. It has about 4 accounts in addition to mine.

I have my new Ubuntu install on sdb. It only has my account.

Is there an easy way to move users from the sda install to the sdb install? I'd like all their settings and files on the new install so I can remove the original install.

Thanks!

---

