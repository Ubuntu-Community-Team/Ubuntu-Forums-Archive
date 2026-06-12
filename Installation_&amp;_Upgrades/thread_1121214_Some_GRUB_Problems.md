---
title: "Some GRUB Problems"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by JCoster on 2009-04-09
Hi all.
I've just got myself a new laptop and am attempting to triple boot Ubuntu 8.10, Vista Home Premium 64-bit and Business 32-bit.  The reasons why I need both 32 and 64- bit versions of Vista are trivial, yet still it is necessary.
I installed them in the following order:
- Vista 64
- Vista 32
- Ubuntu

I have all three on the same disk in separate partitions, and a fourth partition (NTFS) for data.  I do not have a swap partition.

My bootloader is at the stage where there are four options:
- Ubuntu
- Ubuntu recovery
- Ubuntu memtest
- Windows Loader

Ubuntu loads fine but when I enter Windows Loader I get the Windows loader between the two separate Windows installs, which too boot fine.

I just ideally would like all three OS's to boot from the GRUB menu rather than the Windows being booted from a submenu, if you will.

Here is my current GRUB menu.lst:
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
# kopt=root=UUID=fe26315f-c92b-43a8-88c7-85da792ffdd7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fe26315f-c92b-43a8-88c7-85da792ffdd7

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
uuid		fe26315f-c92b-43a8-88c7-85da792ffdd7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fe26315f-c92b-43a8-88c7-85da792ffdd7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		fe26315f-c92b-43a8-88c7-85da792ffdd7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fe26315f-c92b-43a8-88c7-85da792ffdd7 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		fe26315f-c92b-43a8-88c7-85da792ffdd7
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

And here is my fdisk -l output:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x349d8e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           55364       60801    43680735   83  Linux
/dev/sda2   *        1915       38393   293009520    7  HPFS/NTFS
/dev/sda3           38393       51447   104857600    7  HPFS/NTFS
/dev/sda4           51447       55363    31457280    7  HPFS/NTFS

Partition table entries are not in disk order

```

sda1 = Ubuntu ext3
sda2 = Vista 64-bit
sda3 = NTFS data partition
sda4 = Vista 32-bit

But yeah, i'm pretty confused as to what i should do next.

Any ideas would be greatly appreciated.

Thanks in advance,
JC

---

### Post by ronparent on 2009-04-09
If I follow you correctly, your vista installed on (hd0,1) contains a vista bootloader. I think you have to locate it and disable it and then add an instruction in menu.lst to boot to vista on (hd3,0). Not being familiar enough with the vista bootloader protocol, you are on your own there.

---

### Post by JCoster on 2009-04-09
The *hd(x,x)* locations...  are these explained anywhere?  And how can I find out which partition is which?

From what i have previously understood, the syntax is as follows:
hd(physical_drive,partition)

Is this correct?

---

### Post by brayden13 on 2009-04-09
Yes I think so, well anyway you would have to fidn some way of disabling the Vista bootloader and add some info to the bottom of your menu.lst file so you can boot into the two vista versions.

---

### Post by ronparent on 2009-04-09
sda is (hd0) in grub terminalogy

sdb is (hd2), etc

The numbers after the comma refer to the partition which are numbered from 0.

ie sda2 is (hd0,1) etc.

---

### Post by meierfra. on 2009-04-09
You will have to  edit the Vista boot loader a few times,  copy the boot files from  Vista  64 to Vista 32  and edit menu.lst:


[SIZE="3"][COLOR=blue] Boot into Vista 64[/COLOR][/SIZE]


** Step 1 Edit the Vista 64 boot loader**

Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open the  command line as an administrator. Type



```
  
bcdedit /set {bootmgr} device boot

```


[SIZE="3"][COLOR=blue] Boot into Ubuntu.[/COLOR] [/SIZE]
and open a terminal (Applications->Accessories->Terminal) 


** Step 2 Add Vista 32 to "menu.lst" **

Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Change  your current  Windows Vista item to

title  Vista  64
root		(hd0,1)
savedefault
makeactive
chainloader	+1

(so just change the title)


Add this after the Vista 64 item:

title Vista 32
root (hd0,3)
savedefault
makeactive
chainloader +1
Save the file.


** Step 3 Copy the boot files from Vista 64 to Vista 32 **

Back in the terminal type

```
sudo mkdir /mnt/Vista{64,32}
sudo mount /dev/sda2 /mnt/Vista64
sudo mount /dev/sda4 /mnt/Vista32
sudo cp /mnt/Vista{64,32}/bootmgr
sudo cp -R /mnt/Vista{64,32}/Boot

```
Sometimes the directory  Boot  is called BOOT instead. Use  "ls -l /mnt/Vista64/" the determine the correct spelling. 


[SIZE="3"][COLOR=blue] Boot into Vista 64[/COLOR][/SIZE]
by choosing Vista 64 at the grub menu, and then again at the Vista 64 boot menu.

**Step 4  Edit the Vista 64 boot loader  **

Open the Vista 64 command line just as above. Type

```

bcdedit /set {bootmgr} default {current}
bcdedit /set {bootmgr} timeout 0

```

[SIZE="3"][COLOR=blue] Boot into Vista 32[/COLOR][/SIZE]
by choosing Vista 32 at the grub menu, and then again at the Vista 32 boot menu.

**Step 5  Edit the Vista 32 boot loader  **

Open the Vista 32 command line just as above. Type

```

bcdedit /set {bootmgr} default {current}
bcdedit /set {bootmgr} timeout 0

```

That's it. From now on picking one of the Vista's at the Grub menu, should boot you directly into that Vista.

---

### Post by JCoster on 2009-04-10
Thanks a lot meierfra, that's just what i needed...
I'll give it a go this afternoon and let you know the result!
Thank you once again,
JC

---

### Post by JCoster on 2009-04-11
Thanks, that really did the trick.

Absolutely excellent help,
JC

---

### Post by meierfra. on 2009-04-11
> that really did the trick.
Great. Enjoy all you OS's.

> Absolutely excellent help,

I have given similar instructions before, improving  them each time. But this was actually the first time I did  it for Vista/Vista, all the previous cases  were XP/Vista or XP/Win 7. So I had to modify my instructions and I'm glad it worked out  as planned.

---

