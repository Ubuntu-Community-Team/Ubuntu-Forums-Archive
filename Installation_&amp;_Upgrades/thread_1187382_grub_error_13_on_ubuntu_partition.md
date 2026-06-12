---
title: "grub error 13 on ubuntu partition"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by ZaaBI_AlonSo on 2009-06-14
hello,
well here is my story, i had ubuntu 8.10, everything was perfect, upgraded to 9.04 everything still perfect changed the filesystem from ext3 to ext4, still everything was perfect, then i installed the updates, it updated the kernell too, installed -13 generic and now i can't even boot on my ubuntu partition on the new kenrel, it says

Error 13

invalid or unsupportable format

so what can i do? help please
....

---

### Post by merlinus on 2009-06-14
Grub may be looking for ubuntu on the wrong partition.  If you know which one it is, press e when you see the menu, press e again and edit the boot line to the correct root, and press b to boot.

If it works you can edit /boot/grub/menu.lst to make the change permanent.

---

### Post by Shazaam on 2009-06-14
[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)
(new hermanzone grub webpage)
Have you tried booting to an older kernel? When the pc boots hit your Esc key to get the grub kernel list.

---

### Post by ZaaBI_AlonSo on 2009-06-14
> **Shazaam said:**
> [http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)
(new hermanzone grub webpage)
Have you tried booting to an older kernel? When the pc boots hit your Esc key to get the grub kernel list.


well have just tried to edit the menu.lst and

can't even boot at my Svista partition now grub can't even start 
i've changed -13 to -12, changed back to -13 and still nothing happens help needed...

---

### Post by ZaaBI_AlonSo on 2009-06-14
> **merlinus said:**
> Grub may be looking for ubuntu on the wrong partition.  If you know which one it is, press e when you see the menu, press e again and edit the boot line to the correct root, and press b to boot.

If it works you can edit /boot/grub/menu.lst to make the change permanent.
:L

tried to boot from the command line of grub by searching the kenrell and pressing boot
but it reaches a point where it says:

kenrnel panic



i think that can't find the filesystem or sth...

---

### Post by ZaaBI_AlonSo on 2009-06-14
now i'm on a live cd how can i fix the problem guys?

here is my fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x450bc052

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15362   123392000    7  HPFS/NTFS
/dev/sda2           15363       30401   120800767+   5  Extended
/dev/sda5           15363       15424      497983+  82  Linux swap / Solaris
/dev/sda6           15425       30401   120302721   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
128 heads, 63 sectors/track, 60565 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0xb34f0fcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60565   244198048+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74da5d32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
ubuntu@ubuntu:~$ s

---

### Post by presence1960 on 2009-06-14
is windows on sda1 or sdb1? why don't you download the boot info script from here to your desktop : [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Then open a terminal and run ```
sudo bash ~/Desktop/boot_info_script*.sh 
```

This will give a better picture of your setup. It will produce a RESULTS.txt file on your desktop. Paste the contents of that file back here. Highlight the pasted text and click # in the toolbar to place code tags around the text.

---

### Post by ZaaBI_AlonSo on 2009-06-14
ok here are the results

everything is installed on sda, sdb has only data

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Lilo is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #1 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x450bc052

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   246,786,047   246,784,000   7 HPFS/NTFS
/dev/sda2         246,790,530   488,392,064   241,601,535   5 Extended
/dev/sda5         246,790,593   247,786,559       995,967  82 Linux swap / Solaris
/dev/sda6         247,786,623   488,392,064   240,605,442  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
128 heads, 63 sectors/track, 60565 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb34f0fcc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,396,159   488,396,097   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x74da5d32

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="303027B130277CCA" LABEL="Vista" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="07355e1e-10be-48fd-8900-ecb0b86de019" 
/dev/sda6: UUID="9ee72317-2f13-4017-b9ae-74c370f87f58" TYPE="ext4" 
/dev/sdb1: UUID="771A15E65ACC05D9" LABEL="Data" TYPE="ntfs" 
/dev/sdc1: UUID="ACA0BAA6A0BA7684" LABEL="ZaaB" TYPE="ntfs" 

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
/dev/sdc1 on /media/ZaaB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/disk type ext4 (rw,nosuid,nodev,uhelper=hal)


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
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/black light-green/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9ee72317-2f13-4017-b9ae-74c370f87f58 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9ee72317-2f13-4017-b9ae-74c370f87f58

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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
# howmany=1

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

uuid		9ee72317-2f13-4017-b9ae-74c370f87f58
splashimage=(hd0,5)/boot/images/grub_skull.xpm.gz

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		9ee72317-2f13-4017-b9ae-74c370f87f58
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9ee72317-2f13-4017-b9ae-74c370f87f58 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, memtest86+
uuid		9ee72317-2f13-4017-b9ae-74c370f87f58
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=9ee72317-2f13-4017-b9ae-74c370f87f58 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=07355e1e-10be-48fd-8900-ecb0b86de019 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Data ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0
#/dev/sdd1 /media/New ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda6: Location of files loaded by Grub: ===================


 126.9GB: boot/grub/menu.lst
 182.9GB: boot/grub/stage2
 182.8GB: boot/initrd.img-2.6.24-21-generic
 182.9GB: boot/initrd.img-2.6.24-21-generic.bak
 182.8GB: boot/initrd.img-2.6.27-14-generic
 182.9GB: boot/initrd.img-2.6.28-11-generic
 182.9GB: boot/initrd.img-2.6.28-12-generic
 182.9GB: boot/initrd.img-2.6.28-13-generic
 182.9GB: boot/vmlinuz-2.6.24-21-generic
 182.9GB: boot/vmlinuz-2.6.27-14-generic
 182.9GB: boot/vmlinuz-2.6.28-11-generic
 182.8GB: boot/vmlinuz-2.6.28-12-generic
 182.9GB: boot/vmlinuz-2.6.28-13-generic
 182.9GB: initrd.img
 182.9GB: initrd.img.old
 182.9GB: vmlinuz
 182.8GB: vmlinuz.old
```

---

### Post by mhgsys on 2009-06-14
to recover grub :

Bootup a live cd, open a terminal and do the following.

```


sudo grub

```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```


find /boot/grub/stage1

```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)



```

root (hd?,?)

```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```


setup (hd0)

```
Finally exit the grub shell
```


quit

```

Reboot: this should get your linux working.

Then edit your /boot/grub/menu.lst and add:
```

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1

```

This should get your dual boot (vista) going.

---

### Post by presence1960 on 2009-06-14
kernel 2.6.28-13 has correct UUID.
If your previous kernel boots I would use that for now. Maybe remove the new kernel in Synaptic and reinstall it. 

Where is your recovery boot option for the new kernel? It is not in menu.lst. Did you remove it? Not a wise thing to do. You may need it one day. If you don't want it to show in your menu you can comment it out. If you didn't remove it then that could be a sign your update messed up.

I would recommend leaving at least the previous kernel in your menu.lst so if you have problems with the new kernel you can boot into the older kernel.

If I remember correctly I had problems initially with this kernel too. I remember marking it for complete removal in Synaptic. The next time it updated it worked fine.

Sorry I can't come up with anything else

---

### Post by ZaaBI_AlonSo on 2009-06-14
> **mhgsys said:**
> to recover grub :

Bootup a live cd, open a terminal and do the following.

```


sudo grub

```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```


find /boot/grub/stage1

```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)



```

root (hd?,?)

```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```


setup (hd0)

```
Finally exit the grub shell
```


quit

```

Reboot: this should get your linux working.

Then edit your /boot/grub/menu.lst and add:
```

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1

```

This should get your dual boot (vista) going.


allready tryied that nothing happens

---

### Post by ZaaBI_AlonSo on 2009-06-14
> **presence1960 said:**
> kernel 2.6.28-13 has correct UUID.
If your previous kernel boots I would use that for now. Maybe remove the new kernel in Synaptic and reinstall it. 

Where is your recovery boot option for the new kernel? It is not in menu.lst. Did you remove it? Not a wise thing to do. You may need it one day. If you don't want it to show in your menu you can comment it out. If you didn't remove it then that could be a sign your update messed up.

I would recommend leaving at least the previous kernel in your menu.lst so if you have problems with the new kernel you can boot into the older kernel.

If I remember correctly I had problems initially with this kernel too. I remember marking it for complete removal in Synaptic. The next time it updated it worked fine.

Sorry I can't come up with anything else

right now nothing works, i think everything is messed up
i 'll format the partition i think...
this will be called ubuntu night...

thnxz for you help guys...

---

### Post by mhgsys on 2009-06-14
Nothing works?

ehmz, 
Stupid thought.

Is your bios booting the right drive?

---

