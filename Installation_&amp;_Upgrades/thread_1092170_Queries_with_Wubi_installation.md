---
title: "Queries with Wubi installation"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by karthik_jce on 2009-03-10
Hi Experts,

I am considering installing ubuntu with Wubi in windows XP, I have the following queries regarding this,

1. Is Wubi fully functional i.e with all applications, 3D desktops, support for Nvidia graphics card etc.
2. Does it install a boot loader i.e like Grub ?
3. Is is easy to uninstall ?
4. Can we have KDE with this wubi i.e Kubuntu ?

Thanks
Karthigeyan

---

### Post by Partyboi2 on 2009-03-10
>  1. Is Wubi fully functional i.e with all applications, 3D desktops, support for Nvidia graphics card etc. Yes 
>  2. Does it install a boot loader i.e like Grub ?
Wubi uses the windows boot loader.
>  3. Is is easy to uninstall ?
You can uninstall it just like you do other programs in windows by add-remove programs option.
>  4. Can we have KDE with this wubi i.e Kubuntu ?
Yes

---

### Post by ssjs on 2009-04-18
Hi experts,

I'm new to Wubi, and Linux and Ubuntu in general.
I've just installed Wubi and ended up in the GRUB bootloader, with which I'm unfortunately absolutely clueless.
Can anyone guide me?

Thanks!

---

### Post by meierfra. on 2009-04-18
In order to get a clearer picture of your setup, I suggest to boot  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by ssjs on 2009-04-18
Thanks a lot for the prompt reply!


```
============================= Boot Info Summary: ==============================

 => ThinkPad is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /BOOT.INI /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcccdcccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   146,044,079   146,044,017   7 HPFS/NTFS
/dev/sda2         146,044,080   156,295,439    10,251,360  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DAC8013AC8011703" LABEL="IBM_PRELOAD" TYPE="ntfs" 
/dev/sda2: LABEL="SERVICEV001" UUID="1B33-0A00" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


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

================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

c:\wubildr.mbr="Ubuntu"


================================== sda1 Wubi: ==================================

ubuntu/boot/root.disk was found, but could not be mounted

================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\ = "PC-DOS"


================================ sda2/BOOT.INI: ================================

[boot loader]

timeout=0

default=C:\

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\ = "PC-DOS"

=============================== StdErr Messages: ===============================

mount: you must specify the filesystem type
umount: /tmp/BootInfo/Wubi: not mounted
umount: /tmp/BootInfo/Wubi: not mounted
```

---

### Post by meierfra. on 2009-04-18
> root.disk was found, but could not be mounted


Looks like there is a problem with root.disk. (root.disk is the file containing the Wubi install.)
So I suggest to run a file system check on root.disk
Boot from the Ubuntu  LiveCD,  open a terminal

```

sudo mount /dev/sda1 /mnt

sudo e2fsck -fyv /mnt/ubuntu/disks/root.disk
```


Reboot and see whether you can now boot into Ubuntu.

---

### Post by ssjs on 2009-04-21
Thanks! but still not working :(

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo e2fsck -fyv /mnt/ubuntu/disks/root.disk
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /mnt/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by meierfra. on 2009-04-21
It seems root.disk is damaged. Since this is a fresh install it does not make much sense trying to repair root.disk. 

So I suggest to uninstall wubi (either via "add/remove programs" or  by deleting the folder Ubuntu)  Defrag your Windows partition a few times.  Check the Ubuntu CD for errors. Then reinstalled Wubi. 

You might also consider a regular Ubuntu install instead of a Wubi install.

---

