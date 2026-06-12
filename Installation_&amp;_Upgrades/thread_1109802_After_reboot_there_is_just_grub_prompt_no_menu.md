---
title: "After reboot there is just grub prompt no menu ??"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by dbeg on 2009-03-29
Hello,

I have problems with booting. After installing Ubuntu on separate partition the system was booted from first partition (WinXp), without option to chose between Ubuntu and XP. So I googled a little (because I am beginner with Ubuntu) and installed grub (I booted Ubuntu from my flash drive).

But now I can't even get to WinXP nor to Ubuntu. When I reboot computer, GRUB prompt appears.

Please if there is someone that could help me, because I really wouldn't like to reinstall WinXP and Ubuntu again just to fix this.

Thank you

---

### Post by infoseeker on 2009-03-29
> **dbeg said:**
> Hello,

When I reboot computer, GRUB prompt appears.

Thank you

What is listed in the GRUB menu?

Edit: Oops...misread.  Grub prompt...   thats another story.
You probably need to reboot with yr flashdrive and setup GRUB that way.  ???

```
man grub-install
```

---

### Post by dbeg on 2009-03-29
Sorry, but I'm a bit confused. Can you please help me with some details, I don't want to screw up again.

I have following partitions, with Ubuntu on sda7 and WinXp on sda1

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24ff24ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       60800   437176845    f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           19123       60800   334778503+   7  HPFS/NTFS
/dev/sda7           12749       18219    43945776   83  Linux
/dev/sda8           18220       19122     7253316   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)



```

---

### Post by ronparent on 2009-03-29
No need for a reinstall. Installing grub overwrit the WinXP bootloader. If grub is already configured to find both Linux and windows you have a dual boot system by menu selection. If not, you configere grub to find both systems. If you so choose, you can use your win install disk to restore the windows boot record, but then you won't be able to load windows. lokat site below on how to work with grub.

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by infoseeker on 2009-03-29
My setup seems similar to yours
```
~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5c4d5c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       10198    30716280    7  HPFS/NTFS
/dev/sda3           10199       11473    10241437+   c  W95 FAT32 (LBA)
/dev/sda4           11474       30401   152039160    f  W95 Ext'd (LBA)
/dev/sda5           11474       11600     1020096   82  Linux swap / Solaris
/dev/sda6           11601       14150    20482843+  83  Linux
/dev/sda7           14151       16700    20482843+  83  Linux
/dev/sda8           16701       30401   110053251   83  Linux

```

What you have to do is reboot from your flashdrive/ubuntu CD (?) and at the prompt enter
```
sudo grub
```
```

grub > find /boot/grub/stage1 (finds your stage1 file/s)
grub > root (hd0,x)           (Specify x where your /boot partition resides as in above line)
grub > setup (hd0)            (Install GRUB in the MBR)
grub > quit                   (Exit the GRUB shell)

```

Then unmount your flashdrive and reboot.

---

### Post by dbeg on 2009-03-29
> **infoseeker said:**
> My setup seems similar to yours
```
~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5c4d5c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       10198    30716280    7  HPFS/NTFS
/dev/sda3           10199       11473    10241437+   c  W95 FAT32 (LBA)
/dev/sda4           11474       30401   152039160    f  W95 Ext'd (LBA)
/dev/sda5           11474       11600     1020096   82  Linux swap / Solaris
/dev/sda6           11601       14150    20482843+  83  Linux
/dev/sda7           14151       16700    20482843+  83  Linux
/dev/sda8           16701       30401   110053251   83  Linux

```

What you have to do is reboot from your flashdrive/ubuntu CD (?) and at the prompt enter
```
sudo grub
```
```

grub > find /boot/grub/stage1 (finds your stage1 file/s)
grub > root (hd0,x)           (Specify x where your /boot partition resides as in above line)
grub > setup (hd0)            (Install GRUB in the MBR)
grub > quit                   (Exit the GRUB shell)

```

Then unmount your flashdrive and reboot.
If I insert following commands everything seems ok, but when I reeboot computer it has no effect, GRUB prompt appears without any list.

```

grub> find /boot/grub/stage1
 (hd0,6)

grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 


```

---

### Post by ronparent on 2009-03-29
Code:

grub> find /boot/grub/stage1
 (hd0,6)

grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>


Strange. Your setup is right! To quote from this source: 

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

"Usually, this means GRUB's stage1 and stage1_5 files were able to find GRUB's stage2 in the operating system's partition but the stage2 can't find a menu.lst file to load a menu from.
Did you delete or rename the menu.lst file?
Did you move your menu.lst out of the /boot directory?"

From what you have presented so far this doesn't seem to be the case?????

---

### Post by dbeg on 2009-03-29
> **ronparent said:**
> Code:

grub> find /boot/grub/stage1
 (hd0,6)

grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>


Strange. Your setup is right! To quote from this source: 

[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

"Usually, this means GRUB's stage1 and stage1_5 files were able to find GRUB's stage2 in the operating system's partition but the stage2 can't find a menu.lst file to load a menu from.
Did you delete or rename the menu.lst file?
Did you move your menu.lst out of the /boot directory?"

From what you have presented so far this doesn't seem to be the case?????
It must be something like that, because I have no menu.lst file under /boot/grub/ on ubuntu partition.

How do I restore that file?

---

### Post by ronparent on 2009-03-29
It should have been restored by grub>setup (hd0) command? I, usfortunately can't research this further rignt now. Bump

---

### Post by infoseeker on 2009-03-29
To restore WinXP to normal (without the Linux stuff) all you have to do is insert your WindowsXP disk and reboot ....... and do a repair of the MBR.  I don't remember the exact sequence of events but all I know you have to have a command prompt where you enter something like 'fixmbr'.  Google for 'fixmbr' and you may find something.

If you want XP together with Ubuntu then do the following:



This is my '/boot/grub/menu.lst' file.  Yours should be similar. The last few lines are the most important. The kernel could be different and disk uuid will be different.

your kernel is listed under '/boot' in your installed file structure and can be seen by issuing 'ls -l /boot' once mounted somewhere on your boot device, eg.  /mnt/ubuntu.

Your disk uuid should be found listed under /dev/disk/by-uuid (as mine are):

```
# ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 49dc0f8e-075a-48d0-a5b5-23572fe2aab7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 57097aea-e205-4869-94f5-99f507b78da2 -> ../../sda8
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 8cb94148-cbde-4b69-afdd-d354334de592 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 A8BA-08AF -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 B604CE1D04CDE08B -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 d017f448-5e3c-40f8-ba5c-5450dd836fc3 -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 FE84BA2584B9DFF7 -> ../../sda1

```

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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		60

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
# kopt=root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49dc0f8e-075a-48d0-a5b5-23572fe2aab7

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
# defoptions=vga=791

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


title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro vga=791
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro single vga=791
initrd		/boot/initrd.img-2.6.27-11-generic



title		Ubuntu 8.10, memtest86+
uuid		49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by meierfra. on 2009-03-29
In order to get a clearer picture of your setup, I suggest to boot into  from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags) The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by dbeg on 2009-03-30
Thanks, unfortunately I wont't be able to try this until tomorow afternoon, when I'll be back home. I'll report then.

Thanks for support!

PS: I am able to manually boot into WinXP,
but I wasn't able to boot into ubuntu. I was using this link
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

grub>  root (hd0,1)
grub>  kernel /vmlinuz root=/dev/sda7
grub>  initrd /initrd.img
Error 15: File not found

But this file is there beside vmlinuz file.

---

### Post by dbeg on 2009-03-31
> **infoseeker said:**
> To restore WinXP to normal (without the Linux stuff) all you have to do is insert your WindowsXP disk and reboot ....... and do a repair of the MBR.  I don't remember the exact sequence of events but all I know you have to have a command prompt where you enter something like 'fixmbr'.  Google for 'fixmbr' and you may find something.

If you want XP together with Ubuntu then do the following:



This is my '/boot/grub/menu.lst' file.  Yours should be similar. The last few lines are the most important. The kernel could be different and disk uuid will be different.

your kernel is listed under '/boot' in your installed file structure and can be seen by issuing 'ls -l /boot' once mounted somewhere on your boot device, eg.  /mnt/ubuntu.

Your disk uuid should be found listed under /dev/disk/by-uuid (as mine are):

```
# ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 49dc0f8e-075a-48d0-a5b5-23572fe2aab7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 57097aea-e205-4869-94f5-99f507b78da2 -> ../../sda8
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 8cb94148-cbde-4b69-afdd-d354334de592 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 A8BA-08AF -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 B604CE1D04CDE08B -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 d017f448-5e3c-40f8-ba5c-5450dd836fc3 -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 FE84BA2584B9DFF7 -> ../../sda1

```

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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		60

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
# kopt=root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49dc0f8e-075a-48d0-a5b5-23572fe2aab7

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
# defoptions=vga=791

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


title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro vga=791
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro single vga=791
initrd		/boot/initrd.img-2.6.27-11-generic



title		Ubuntu 8.10, memtest86+
uuid		49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Hi, I'm back. I've restored menu.lst file, so now there is a menu at startup as it should be.

BUT, I still can't boot ubuntu.
Obviously, I didn't deleted just menu.lst but also initrd.img-2.6.27-7-generic file, which isn't in /boot/ directory as I think it should be. 

Is this the same file, as the one, that is one level higher (initrd.img without this long extension)? Can I run this file in menu.lst?

---

### Post by HUMZ on 2009-12-08
> **infoseeker said:**
> To restore WinXP to normal (without the Linux stuff) all you have to do is insert your WindowsXP disk and reboot ....... and do a repair of the MBR.  I don't remember the exact sequence of events but all I know you have to have a command prompt where you enter something like 'fixmbr'.  Google for 'fixmbr' and you may find something.

If you want XP together with Ubuntu then do the following:



This is my '/boot/grub/menu.lst' file.  Yours should be similar. The last few lines are the most important. The kernel could be different and disk uuid will be different.

your kernel is listed under '/boot' in your installed file structure and can be seen by issuing 'ls -l /boot' once mounted somewhere on your boot device, eg.  /mnt/ubuntu.

Your disk uuid should be found listed under /dev/disk/by-uuid (as mine are):

```
# ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 49dc0f8e-075a-48d0-a5b5-23572fe2aab7 -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 57097aea-e205-4869-94f5-99f507b78da2 -> ../../sda8
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 8cb94148-cbde-4b69-afdd-d354334de592 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 A8BA-08AF -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 B604CE1D04CDE08B -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 d017f448-5e3c-40f8-ba5c-5450dd836fc3 -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-03-29 22:58 FE84BA2584B9DFF7 -> ../../sda1

``````
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
default        4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        60

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
# kopt=root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49dc0f8e-075a-48d0-a5b5-23572fe2aab7

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
# defoptions=vga=791

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


title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro vga=791
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=49dc0f8e-075a-48d0-a5b5-23572fe2aab7 ro single vga=791
initrd        /boot/initrd.img-2.6.27-11-generic



title        Ubuntu 8.10, memtest86+
uuid        49dc0f8e-075a-48d0-a5b5-23572fe2aab7
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```


I installed Ubuntu Karmic Koala 9.10 and Windows 7 and was not able to boot either OS's, the GRUB prompt kept appearing, I found out my menu.lst file was missing and this helped me recreate one manually!  Thanks a lot man!

---

