---
title: "how to resize ubuntu partition?"
date: 2008-08-11
forum: General Help
---

### Post by lieja on 2008-08-11
i failed to upgrade my system due to limited space in disk partition for ubuntu..by any chance,is there a simple way or any software like partition magic to resize the partition.

---

### Post by /////// on 2008-08-11
Yes, you can use download the GParted live cd and use that to resize the partitions without formatting or deleting anything

Hope this helps

---

### Post by sandysandy on 2008-08-11
URL for gparted live CD <http://gparted.sourceforge.net/> 

here is gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

here is link for dual booting windows & ubuntu

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

regards

---

### Post by ajgreeny on 2008-08-11
Gparted is also on the live Ubuntu CD, **System>>Administration>>Partition Editor**, so need to download gparted live CD if you don't want to.

---

### Post by davidw89 on 2008-08-11
I just did it 10 minute ago.

Boot up from Ubuntu Cd/DVD. Test drive it so the first option. Once it is loaded up go to Partition Editor (System --> Administrator) and unmount the drive you are trying to resize. Once that is done you can right click on it and click resize, select the amount of space you want to resize and then click apply. Should take 30 min/1hr and then your done.

---

### Post by lieja on 2008-08-17
i juz try to resize ubuntu partiton with gparted frm ubuntu live cd but unfortunately the system is crash..i dont know what happened..so please help me..if i want to reinstall ubuntu partition..should i delete the old ubuntu partition?

---

### Post by Elfy on 2008-08-17
If you want to reinstall you cna use the old partition - but if they were too small perhaps resize them.

When you say the system crashed - did it do so while gparted was working?

How much bigger do you want the partition to be?

Run the livecd and paste the output of

```
sudo fdisk -l
```

---

### Post by lieja on 2008-08-17
here is the output of the command

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f302f2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1316    10570738+   7  HPFS/NTFS
/dev/sda2            1317        7297    48042382+   f  W95 Ext'd (LBA)
/dev/sda5            1317        2732    11373988+   7  HPFS/NTFS
/dev/sda6            4294        7297    24129598+   7  HPFS/NTFS
/dev/sda7   *        3926        4269     2763148+  83  Linux
/dev/sda8            4270        4293      192748+  82  Linux swap / Solaris
/dev/sda9            2733        3925     9582741   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3936     1007600    b  W95 FAT32


actually..i want to resize ubuntu part to be about 10G frm the previous size,2G..so that i boot frm live cd and resize frm gparted.first..i shrink the size of my ntfs part(19g)to 11g to allocate the remainning space for ubuntu..then i choose ext3 for the new partition..mayb that's my mistake..im not sure..after the gparted finish..there are a message said that the system is crashed:(

---

### Post by Elfy on 2008-08-17
It is always best to post the message - it crashed doesn't help much [noparse];)[/noparse]

What you should be doing is the following - don't know which is 19G - if it is one of sda5 - sda9 then it should be fairly easy -

resize the ntfs to gain unallocated space

resize ext3 to include unallocated space

Then your ext3 should be bigger than it was, you don't actually need to make a new partition.

The other option is to delete sda7 and sda9 assuming thta there is no data on them, do the resizeing to the ntfs. Move the partitions about until all the unallocated space is adjacent to each other and then make a new ext3 there.

---

### Post by lieja on 2008-08-17
well..its tough for me to understand that..could u give more explaination on the steps involved or several screenshot mayb:)

fyi..i've already do that part but mayb with some mistakes..the problem now is to reinstall ubuntu..:(

---

### Post by Elfy on 2008-08-17
Boot the livecd - go to system > admin menu, open the partition editor - do a screenshot of it, post it here. Please use the attachment tool - in thread menu bar looks like #

Lets see what is going on and we can go from there.

---

### Post by lieja on 2008-08-18
sorry for late reply..here is the screenshot frm gparted

[ATTACH]81948[/ATTACH]

---

### Post by Elfy on 2008-08-18
Is it sda7 you wish to resize - I assume so as it is full. It's next to sda9 which is almost empty.

If that is what you want to do then first turn off the swap from a terminal 

```
sudo swapoff -a
```

Once that is done none of the partitions should have the padlock symbol.

Right click sda9 - resize, move slider from right to left - apply.

Right click sda7 - resize, move slider to take up unallocated space.

---

### Post by lieja on 2008-08-18
yes..u r absolutely rite..at first,my ubuntu partition contain only 2 partitions, ext3 and swap.as u c the ext3 is almost full..so i want to extend the space from sda5 free space..so that, i shrink that partition and allocate as ext2..mayb that's my mistake..so..can i still fix the system or juz reinstall new system??

---

### Post by Elfy on 2008-08-18
No you don't need to reinstall - if you added the ext2 by mistake

delete the ext2 partition and resize the ext3 one to the left - if it won't let you do that then - move the ext3 to the left and then resize on the right.

When you have done that post back as you need to check something else before you reboot.

---

### Post by lieja on 2008-08-18
yup..i've finish do that except delete the ext2 but still cannot enter ubuntu system..guess i should reinstall:( luckily..there r no important stuff on the system..juz to install some application for my system

---

### Post by Elfy on 2008-08-18
So you've managed to resize the buntu install partition have you? You need to check the UUID of the drive you want to boot, form the livecd run

```
sudo blkid
```

Then you need to check both the menu.lst and fstab for your installation to make sure they match. Navigate in nautilus to the ubuntu partition and find

/etc/fstab
/boot/grub/menu.lst

If you are at all unsure about what you need to do - then post all 3 here, that is blkid, fstab and menu.lst

---

### Post by lieja on 2008-08-19
i couldnt find the menu.lst file

---

### Post by Elfy on 2008-08-19
Open a terminal and do this to mount the drive

```
sudo mkdir /recovery
sudo mount -t ext3 /dev/sda7 /recovery
cat /recovery/boot/grub/meu.lst
cat /recovery/etc/fstab
sudo blkid
```

Post the outputs

---

### Post by lieja on 2008-08-19
still cant find the menu.lst file..the file also doesnt exist when i use file browser to search that file.there is boot folder but not grub..however here is the output i got from sudo blkid

ubuntu@ubuntu:~$ sudo mkdir /recovery
ubuntu@ubuntu:~$ sudo mount -t ext3/dev/sda7/recovery
ubuntu@ubuntu:~$ cat /recovery/boot/grub/menu.lst
cat: /recovery/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat /recovery/etc/fstab
cat: /recovery/etc/fstab: No such file or directory
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="1414BFE114BFC450" TYPE="ntfs" 
/dev/sda5: UUID="A4E45F05E45ED8DE" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="9E783DD8783DB03F" TYPE="ntfs" 
/dev/sda7: UUID="85f7a8e9-6843-4231-b314-53976d4b2a2f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="6ab3273e-783f-495c-acff-9ecc0a3b57d2" TYPE="swap" 
/dev/sdb1: LABEL="0199790673" UUID="DC4F-758E" TYPE="vfat" 
ubuntu@ubuntu:~$

---

### Post by Elfy on 2008-08-19
Can you do this then - if you have left the livecd you will need to remake /recovery and mount sda7 again, if not just the last 3

```
sudo mkdir /recovery
sudo mount -t ext3 /dev/sda7 /recovery

cd /recovery/
ls
sudo fdisk -l
```

---

### Post by Uchiha_madara on 2008-08-19
Type This Command :

> cfdisk

and repartition it

---

### Post by lieja on 2008-08-20
i juz notice that the command line still can be used by the system that i mention before was crashed..when i type command like network-admin..the warning come out said something like error in display

---

### Post by Elfy on 2008-08-20
Have you managed to run the commands I gave?

Does the system boot in normal or recovery mode?

I'm quite happy to try and help but if you don't answer questions I'm not going to be able to do so.

---

### Post by lieja on 2008-08-20
> **forestpixie said:**
> Have you managed to run the commands I gave?

Does the system boot in normal or recovery mode?

I'm quite happy to try and help but if you don't answer questions I'm not going to be able to do so.

sorry for that:)
actually..i got annoying with running the livecd each time i want to give the output of the command u want..beside that,i dont know how to copy the output frm CLI(i mean the black screen).i juz installed the new ubuntu on other partition..can i juz run the command at the new system to look through the old system error? so..i can copy paste the result frm gui

---

### Post by Elfy on 2008-08-20
If you've got ubuntu running then we don't need to see it - if you have manged to resize the partitions and every thing is running properly then the problem is solved is it not.

Yes it can be annoying having to run the livecd - but when I asked you to do it you were still having problems ;)

---

### Post by lieja on 2008-08-20
actually..i still want to fix the problem in the old system..the new ubuntu i juz installed is hardy..the old one is gutsy. i juz getting excited when there r someone trying to help me here..thanks a bunch:)

---

### Post by Elfy on 2008-08-20
Well ok, from hardy run

```
sudo fdisk -l
df -h
```

Post the output of those and we can see if the gutsy partition is mounted. Then I can show you how to get the information we need.

Can you clarify these points please

- has partition been resized 
- you now have 2 installations of ubuntu, 1 working , 1 not

---

### Post by lieja on 2008-08-20
coolll...:guitar:then here's the output of the command u ask for:KS
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f302f2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1316    10570738+   7  HPFS/NTFS
/dev/sda2            1317        7297    48042382+   f  W95 Ext'd (LBA)
/dev/sda5            1317        2732    11373988+   7  HPFS/NTFS
/dev/sda6   *        2733        4269    12345921   83  Linux
/dev/sda7            4270        4293      192748+  82  Linux swap / Solaris
/dev/sda8            4294        5787    12000523+   7  HPFS/NTFS
/dev/sda9            5788        7227    11566768+  83  Linux
/dev/sda10           7228        7297      562243+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3936     1007600    b  W95 FAT32
liza@liza-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9              11G  2.2G  8.3G  21% /
varrun                474M  104K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
udev                  474M   72K  474M   1% /dev
devshm                474M  188K  474M   1% /dev/shm
lrm                   474M   38M  436M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       11G  2.2G  8.3G  21% /home/liza/.gvfs
/dev/sdb1             983M  654M  329M  67% /media/0199790673
/dev/sda6              12G  2.5G  8.8G  23% /media/disk
/dev/sda8              12G   11G  1.2G  91% /media/disk-1

```

---

### Post by Elfy on 2008-08-20
Ok please run these commands and paste the output

```
ls /media/disk/
cat /media/disk/boot/grub/menu.lst
cat /media/disk/etc/fstab
cat /boot/grub/menu.lst
```

---

### Post by lieja on 2008-08-20
```
liza@liza-laptop:~$ ls /media/disk/
bin    dev   initrd      lost+found  opt       root  sys  var
boot   etc   initrd.img  media       proc      sbin  tmp  vmlinuz
cdrom  home  lib         mnt         recovery  srv   usr
liza@liza-laptop:~$ cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=85f7a8e9-6843-4231-b314-53976d4b2a2f ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=85f7a8e9-6843-4231-b314-53976d4b2a2f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=85f7a8e9-6843-4231-b314-53976d4b2a2f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
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

liza@liza-laptop:~$ cat /media/disk/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=85f7a8e9-6843-4231-b314-53976d4b2a2f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=6ab3273e-783f-495c-acff-9ecc0a3b57d2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
liza@liza-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=227a265c-fb15-47a0-a20c-4af9371c5aea ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=227a265c-fb15-47a0-a20c-4af9371c5aea ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=227a265c-fb15-47a0-a20c-4af9371c5aea ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,8)
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=85f7a8e9-6843-4231-b314-53976d4b2a2f ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=85f7a8e9-6843-4231-b314-53976d4b2a2f ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 7.10, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


```

---

### Post by Elfy on 2008-08-20
Well everything looks fine - you should be able to access your old gutsy install from the new list you get when you boot. The old gutsy install is at the bottom after XP.

The partitions appear to be 75% empty, you do have 2 swap partitions and probably only need 1 - but I think for the moment as long as everything is working properly I would leave well alone.

From post 27 - > actually..i still want to fix the problem in the old system..
From post 1 - > i failed to upgrade my system due to limited space in disk partition for ubuntu..


So as you have the hardy version now is the problem solved. If you want to get your data from you old /home, as long as you have rights to the gutsy /home you should be able to copy the data - then you could if you so wished remove the contenst from that drive and have more storage.

---

