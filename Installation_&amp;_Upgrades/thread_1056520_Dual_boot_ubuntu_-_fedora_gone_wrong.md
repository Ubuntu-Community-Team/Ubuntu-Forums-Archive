---
title: "Dual boot ubuntu - fedora gone wrong"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by josefa on 2009-01-31
Earlier today I had some time on my hands so I installed F10 after an ubuntu install and to my horror it only had the option to boot F10. With an ubuntu live cd I tried to restore its grub but it didn't boot completely (F10 has it's own grup so maybe I "restored" this one).

On normal circumstances I would have done a new ubuntu install but I need a couple of folders on /home. I can't fetch them with a live cd as it says I don't have permissions.

So what should I do to either boot ubuntu or get my 2 folders from /home?

Many thanks in advance for your help.

---

### Post by taurus on 2009-01-31
I assume you are either running F10 right now or Ubuntu LiveCD since you can't boot Ubuntu from your harddrive.  Assuming you are running F10, can you post the outputs of these commands from a terminal.  You probably just need to add entry in /boot/grub/grub.conf for your Ubuntu.

```
fdisk -l
blkid
cat /etc/fstab
df -h
```
p.s.  No need to put sudo in front of the first two commands since you can log in as root in F10.

---

### Post by josefa on 2009-02-01
This is what I get.

```

fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfce28df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11587    93071360   83  Linux
/dev/sda2           14265       14593     2642692+   5  Extended
/dev/sda3           11588       11612      200812+  83  Linux
/dev/sda4           11613       14264    21302190   8e  Linux LVM
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris


blkid
/dev/sda1: UUID="b64c0c42-5cac-4d3b-be30-9d7c8f10c606" TYPE="ext3" 
/dev/sda3: LABEL="/boot" UUID="c25517f6-3d2f-43a8-b40b-0a0b8654406d" TYPE="ext3" 
/dev/sda4: UUID="j4XR2y-7Zpo-7LyR-WL1n-1NRH-Ex7F-4zyBj3" TYPE="lvm2pv" 
/dev/sda5: UUID="ef3fe7c4-846e-435b-99aa-f7cf2e63bdf5" TYPE="swap" 
/dev/loop0: TYPE="squashfs"


cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 441M  2.0M  439M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 441M  2.0M  439M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 441M     0  441M   0% /lib/init/rw
varrun                441M   92K  441M   1% /var/run
varlock               441M     0  441M   0% /var/lock
udev                  441M  2.8M  438M   1% /dev
tmpfs                 441M  104K  441M   1% /dev/shm
rootfs                441M   90M  352M  21% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 441M   12K  441M   1% /tmp
/dev/sda3             190M   14M  167M   8% /media/_boot
/dev/sda1             108G  2.2G  100G   3% /media/disk
```

---

### Post by taurus on 2009-02-01
Which partition (/dev/sda1 or /dev/sda3) is your Ubuntu's root filesystem?  Or do you have a separate /boot partition for Ubuntu?  If you're not sure, look at the outputs of these commands.

```
ls -la /media/_boot
ls -la /media/disk
```

p.s.  Looks like /dev/sda3 is /boot from the partition label.  Is it /boot partition for Ubuntu?

---

### Post by josefa on 2009-02-01
```
ls -la /media/_boot

total 7476
drwxr-xr-x 5 root root    1024 2009-01-31 20:42 .
drwxr-xr-x 4 root root     120 2009-02-01 17:45 ..
-rw-r--r-- 1 root root   90889 2008-11-18 17:30 config-2.6.27.5-117.fc10.i686
drwxr-xr-x 3 root root    1024 2009-01-31 20:40 efi
drwxr-xr-x 2 root root    1024 2009-01-31 20:55 grub
-rw------- 1 root root 3843216 2009-01-31 20:42 initrd-2.6.27.5-117.fc10.i686.img
drwx------ 2 root root   12288 2009-01-31 20:30 lost+found
-rw-r--r-- 1 root root 1089949 2008-11-18 17:30 System.map-2.6.27.5-117.fc10.i686
-rwxr-xr-x 1 root root 2570960 2008-11-18 17:30 vmlinuz-2.6.27.5-117.fc10.i686

ls -la /media/disk

ls: cannot access /media/disk/var: Input/output error
ls: cannot access /media/disk/usr: Input/output error
ls: cannot access /media/disk/proc: Input/output error
total 76
drwxr-xr-x  20 root root  4096 2009-01-30 19:36 .
drwxr-xr-x   4 root root   120 2009-02-01 17:45 ..
drwxr-xr-x   2 root root  4096 2009-01-30 19:36 bin
drwxr-xr-x   3 root root  4096 2009-01-30 19:36 boot
lrwxrwxrwx   1 root root    11 2009-01-30 19:19 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-29 23:04 dev
drwxr-xr-x 122 root root  4096 2009-01-31 18:03 etc
drwxr-xr-x   3 root root  4096 2009-01-30 19:32 home
lrwxrwxrwx   1 root root    32 2009-01-30 19:36 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2009-01-30 19:36 lib
drwx------   2 root root 16384 2009-01-30 19:19 lost+found
drwxr-xr-x   3 root root  4096 2009-01-31 16:27 media
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 22:53 opt
d?????????   ? ?    ?        ?                ? proc
drwxr-xr-x   5 root root  4096 2009-01-30 19:45 root
drwxr-xr-x   2 root root  4096 2009-01-30 19:36 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 22:53 srv
drwxr-xr-x   2 root root  4096 2008-10-14 13:02 sys
drwxrwxrwt   9 root root  4096 2009-01-31 18:03 tmp
d?????????   ? ?    ?        ?                ? usr
d?????????   ? ?    ?        ?                ? var
lrwxrwxrwx   1 root root    29 2009-01-30 19:36 vmlinuz -> boot/vmlinuz-2.6.27-7-generic
```

---

### Post by taurus on 2009-02-01
Now post

```
cat /media/_boot/grub/menu.lst
```

---

### Post by josefa on 2009-02-01
```
cat /media/_boot/grub/menu.lst

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=190b4706-284f-4557-841a-06563a3efb4c rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img

```

---

### Post by taurus on 2009-02-01
That's your grub.conf from F10.  I guess you don't have a separate /boot for Ubuntu then.  Now, we have to look in /dev/sda1--/media/disk--instead.

```
cat /media/disk/boot/grub/menu.lst
```

---

### Post by josefa on 2009-02-01
```
cat /media/disk/boot/grub/menu.lst

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
timeout		3

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
# kopt=root=UUID=b64c0c42-5cac-4d3b-be30-9d7c8f10c606 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b64c0c42-5cac-4d3b-be30-9d7c8f10c606

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
uuid		b64c0c42-5cac-4d3b-be30-9d7c8f10c606
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b64c0c42-5cac-4d3b-be30-9d7c8f10c606 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		b64c0c42-5cac-4d3b-be30-9d7c8f10c606
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b64c0c42-5cac-4d3b-be30-9d7c8f10c606 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		b64c0c42-5cac-4d3b-be30-9d7c8f10c606
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by taurus on 2009-02-01
> **josefa said:**
> ```
cat /media/_boot/grub/menu.lst

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
**[COLOR="Blue"]timeout=5[/COLOR]**
splashimage=(hd0,2)/grub/splash.xpm.gz
**[COLOR="Blue"]#[/COLOR]**hiddenmenu
title Fedora (2.6.27.5-117.fc10.i686)
	root (hd0,2)
	kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=UUID=190b4706-284f-4557-841a-06563a3efb4c rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.i686.img

```
Okay, edit /media/_boot/grub/grub.conf (since you installed GRUB to MBR when you installed F10) and change the _timeout_ from 0 to 5 (or whatever seconds you want it to wait) or else it will boot up the first entry.  Also, place a # in front of the _hiddenmenu_ so you would see GRUB menu.

Then, scroll down to the end and add the following lines for your Ubuntu.

```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		b64c0c42-5cac-4d3b-be30-9d7c8f10c606
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b64c0c42-5cac-4d3b-be30-9d7c8f10c606 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```
Save it and reboot.

---

### Post by josefa on 2009-02-01
I'm on ubuntu live cd, I can't edit grub.conf on F10. Is there any workaround or a way to boot F10 and edit it from there?

---

### Post by taurus on 2009-02-01
What do you mean you can't edit grub.conf on F10?

Applications -> Accessories -> Terminal
```
gksudo gedit /media/_boot/grub/grub.conf
```
Otherwise, just boot up F10 and modify the /boot/grub/grub.conf from F10 then.

---

### Post by josefa on 2009-02-01
You are the man! rebooting now.

---

### Post by msu3 on 2009-02-02
Hm, the same thing happened to me too today. Except here's my output:
```

fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc147ffe0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1280       33151   256000000    7  HPFS/NTFS
/dev/sda4           33152       38913    46283265    5  Extended
/dev/sda5           33152       33177      208813+  83  Linux
/dev/sda6           33178       38913    46074388+  8e  Linux LVM

blkid
/dev/sda6: UUID="rmUN8b-r6t4-r1hT-VV6X-pfUB-Xwal-6vDPU0" TYPE="lvm2pv" 
/dev/sda5: LABEL="/boot" UUID="cf138d38-b634-4d58-8527-4b35c6cbbb33" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="BA80451E8044E28D" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="7454471B5446E00A" LABEL="OS" TYPE="ntfs" 
/dev/mapper/live-rw: LABEL="F10-i686-Live" UUID="51e0bdfc-1a89-45e0-b993-9953dc69e6b8" TYPE="ext3" 
/dev/mapper/live-osimg-min: LABEL="F10-i686-Live" UUID="51e0bdfc-1a89-45e0-b993-9953dc69e6b8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/VolGroup00-LogVol00: LABEL="F10-i686-Live" UUID="2a705c4e-61ee-45ce-af57-46b578c98846" TYPE="ext3" 
/dev/mapper/VolGroup00-LogVol01: TYPE="swap" UUID="e1cca421-4d6b-4188-8eee-3f116e7bfa74" 
/dev/VolGroup00/LogVol00: LABEL="F10-i686-Live" UUID="2a705c4e-61ee-45ce-af57-46b578c98846" TYPE="ext3" 
/dev/VolGroup00/LogVol01: TYPE="swap" UUID="e1cca421-4d6b-4188-8eee-3f116e7bfa74" 

cat /etc/fstab

#
# /etc/fstab
# Created by anaconda on Sun Feb  1 22:37:25 2009
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or vol_id(8) for more info
#
/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
UUID=cf138d38-b634-4d58-8527-4b35c6cbbb33 /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup00-LogVol00
                       38G  4.5G   34G  12% /
/dev/sda5             198M   21M  167M  12% /boot
tmpfs                 1.8G   76K  1.8G   1% /dev/shm

&#65279;
```

for ```
ls -la /media/_boot
ls -la /media/disk

```
I get no such file or directory. Same with the /media/_boot/grub/menu.lst

I actually installed Ubuntu through wubi. The weird thing is that after installing wubi, I reinstalled Windows, not remembering that I had Ubuntu also. So I reinstalled wubi, leading me to have 2 instances of Ubuntu at the boot screen. Don't know if that has anything to do with it. I CD installed Fedora and just downloaded and burned Ubuntu.

Thanks for any help, I just got Ubuntu last week and am trying to get things to work so I can learn linux on both.

---

