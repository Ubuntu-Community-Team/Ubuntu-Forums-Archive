---
title: "HELP! Need to fix MBR"
date: 2008-11-13
forum: General Help
---

### Post by w1av on 2008-11-13
Hi,

I attempted to install a small version of Linux on an unused small partition. It had apparently overwrote my MBR. I have dual boot and can get into Ubuntu OK but can't get into WinXP which I need for recording software. What seems to happen is when I boot computer, the regulat GRUB menu comes up, and if I scroll down to start WinXP the screen goes black, like normal and it says in upper left corner "Starting...." but it HANGS indefinitely. It seems the computer is using the LAME boot loader from that other linux installation. And it can't find Windows! Please help because I need my recording software and I really don't want to have to re install Ubuntu. I installed Ubuntu on sda2 Windows is on sda1. The boot loader from what I recall from when I installed Ubuntu is on sda2. Thanks....bob:confused::confused:

---

### Post by caljohnsmith on 2008-11-13
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd3,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should restore Grub to your MBR. Try rebooting, and let me know what happens.

---

### Post by w1av on 2008-11-13
Thank you for responding! So I will get my installation disk tomorrow morning and do what you suggested. My Dad has the installation disk and will drop it off to me in morning.

My WinXP partition is on hda,first partition so in Grub-speak that would be
hd0,0

Linux is on hda2, in Grub, hd0,1.....

I installed a small version of Linux called "TinyMe" which is about 200MB...what happened was it over wrote the boot sector with it's own and I can no longer boot into Windows....can still boot into Linux (Ubuntu) on hda,2 tho....my grub boot menu still comes up. If worse comes to worse I can just re install Ubuntu and I am sure the MBR and GRUB will revert back to it's original state, but I am crossing my fingers and hope your method will work. Thanks and I will get back to you tomorrow at some point...bob

---

### Post by rsambuca on 2008-11-13
> **caljohnsmith said:**
> OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd3,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should restore Grub to your MBR. Try rebooting, and let me know what happens.

If you want the Ubuntu grub to overwrite your MBR, you will want to run the setup command as:
```
setup (hd0)
```Also, if you have to stage1 grub entries, it will give you two locations for the 'find' command.  You will want to enter your Ubuntu partition for the 'root' command.

---

### Post by w1av on 2008-11-13
OK, then rsambuca, so what I should do is run the first command like caljohnsmith suggested.....

sudo grub
grub> find /boot/grub/stage1

Then the following should appear in terminal:

grub> root (hd0,1)
grub> setup (hd0)
grub> quit

Then do what you said........... setup (hd0)????  Just dont wanna make a mistake cause I have never had this happen before.....Thanks.....I DO need GRUB to overwrite MBR so things will revert to my previous working system. The GRUB from that other linux distro apparently overwrote my UBUNTU MBR!!! With no warning!!!

---

### Post by meierfra. on 2008-11-13
> the regulat GRUB menu comes up
Is this the same menu you always got (from Ubuntu) or is a menu from TinyMe?

If it is the Ubuntu Grub menu, then you should not   reinstall grub.


If it is TinyMe  Grub menu, then you need to reinstall grub.Since you can boot into ubuntu, you don't need the Live CD for that, just do it from an Ubuntu terminal. If the output of "find /boot/grub/stage1" is indeed (hd0,1), do

```
root (hd0,1)
setup (hd0)
quit
```

(note that the instructions from caljohnsmith and rsambuca  actually agree on this)


Did you resize the Windows Partition while installing TinyMe?

 Open a  terminal in Ubuntu and post the output of 

```
sudo fdisk -lu

cat /boot/grub/menu.lst
``````

```

---

### Post by w1av on 2008-11-13
What happens is when I boot computer, my regular GRUB menu comes up like always from UBUNTU....I installed UBUNTU a few weeks ago (8.04) on first hard drive, second partition....Win XP is on first hard drive, first partition. The TinyMe linux was "installed" on hard drive 1, fourth partition. So it is a dual boot and has been working great till I installed TinyMe and it screwed up my MBR. So it must be a TinyMe boot that occurs because when I do boot into Ubuntu, I get all the info scrolling across a black screen with white characters.....showing boot progress....it never did that before. Then Ubuntu does come up no problem....its like another bootloader or mbr is running now. I did notice booting from the LIVE CD of Tiny Me, the same characters scroll by when booting. I didnt resize Windows partition at all because I already had that spare partition....it was an unused FAT32 partition. I figured I would try to install a small linux just for fun...but it bit me hard!

Heres what you wanted me to post:

bob@bob-desktop:~$ sudo su
[sudo] password for bob: 
root@bob-desktop:/home/bob# sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000dfbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    79976672    39988305    7  HPFS/NTFS
/dev/sda2        79976673   138571019    29297173+  83  Linux
/dev/sda3       138571020   142480106     1954543+  82  Linux swap / Solaris
/dev/sda4       142480107   156300542     6910218   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00078af8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    77369039    38684488+   b  W95 FAT32
/dev/sdb2        77369040   155910824    39270892+   b  W95 FAT32
/dev/sdb3       155910825   234436544    39262860    b  W95 FAT32
root@bob-desktop:/home/bob# cat /boot/grub/menu.lst
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

## Pretty colours
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
# kopt=root=UUID=567b3e42-98e1-4334-8875-f011bd10e54c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=567b3e42-98e1-4334-8875-f011bd10e54c ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=567b3e42-98e1-4334-8875-f011bd10e54c ro single
initrd		/boot/initrd.img-2.6.24-21-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=567b3e42-98e1-4334-8875-f011bd10e54c ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=567b3e42-98e1-4334-8875-f011bd10e54c ro single
#initrd		/boot/initrd.img-2.6.24-16-generic

#title		Ubuntu 8.04.1, memtest86+
#root		(hd0,1)
#kernel		/boot/memtest86+.bin
#quiet

title            TinyMe Linux
root             (hd0,3)
kernel           /boot/vmlinuz-2.6.18.8.tex6.lgc ro quiet splash
initrd           /boot/initrd-2.6.18.8.tex6.lgc.img


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

root@bob-desktop:/home/bob#

---

### Post by meierfra. on 2008-11-13
Go ahead and reinstall grub (see the edit in my last post). But I doubt it will make any difference. It seems more likely that something happened to the Windows boot sector. Just give me a minute and I'll find instructions to restore your boot sector.

Did you add the "TinyMe" entry  to menu.lst or did "TinyMe" do that?

---

### Post by w1av on 2008-11-13
Wow, I never had any boot problems before...OK I will wait for your help...thank you so much....bob:)

---

### Post by meierfra. on 2008-11-14
If reinstalling grub did not solve the problem try this to restore the XP boot sector by its backup (I stole these instruction from one of caljohnsmith post):


```
sudo apt-get install testdisk
sudo testdisk
```

After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the XP partition, choose "boot", then choose "Backup BS", and have testdisk write the backup boot sector to the partition boot sector.

---

### Post by w1av on 2008-11-14
Is it this code I have to type in? It won't work! I can only get as far as the first line but I get an error! I type it in terminal exactly like this:   root (hd0,1) press enter and get error 




root (hd0,1)
setup (hd0)
quit



I can't get the code to work!!!! here is what I get:

root@bob-desktop:/home/bob# root(hd0,1)
bash: syntax error near unexpected token `hd0,1'
root@bob-desktop:/home/bob# root (hd0,1)
bash: syntax error near unexpected token `hd0,1'
root@bob-desktop:/home/bob# root (hd0,1)

---

### Post by meierfra. on 2008-11-14
Sorry, you need to do

```
sudo grub
```

first, to get to the grub prompt.

---

### Post by w1av on 2008-11-14
I have big problem....here's as far as I got with testdisk after I typed in the XP partition: there is no boot option????

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  4978  80 63   79976610

Boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Backup boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.



[  Quit  ]  [  List  ]  [Rebuild BS][Repair MFT][  Dump  ]
                            Return to Advanced menu

---

### Post by w1av on 2008-11-14
I did have some luck with the first suggestion....sudo grub, then type in root (hd0,1)  setup (hd0) quit...seemed to go thru with no error...I will re boot to see if it helped...

---

### Post by w1av on 2008-11-14
No difference....I think as a last resort I can just re install Ubuntu and maybe that will recognize my Windows partition and it will work again....otherwise I am really in trouble here!!! I have all my music software and files in there on Windows!!! H E L P!!!!!!
I did try testdisk but it came back with an error.....Look below: What else can I try????

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
Partition Start End Size in sectors
1 * HPFS - NTFS 0 1 1 4978 80 63 79976610

Boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Backup boot sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.



[ Quit ] [ List ] [Rebuild BS][Repair MFT][ Dump ]
Return to Advanced menu

---

### Post by meierfra. on 2008-11-14
> think as a last resort I can just re install Ubuntu and maybe that will recognize my Windows partitio

Reinstalling Ubuntu will not help. There is some kind of problem with Windows.

> 
Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
Don't worry about that. It's pretty common and should not cause a problem.

> Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.



[ Quit ] [ List ] [Rebuild BS][Repair MFT][ Dump 

Well, the backup is identical with the  bootsector. So forget about that idea.

But try the "Rebuild BS" option.  If the rebuild boot sector is different from the current boot sector, choose "write" to write the new boot sector to the partition.

---

### Post by w1av on 2008-11-14
There is no option at bottom of testdisk to choose "Backup BS".....did you mean "Rebuild BS"????? Re: HELP! Need to fix MBR
If reinstalling grub did not solve the problem try this to restore the XP boot sector by its backup (I stole these instruction from one of caljohnsmith post):


Code:

sudo apt-get install testdisk
sudo testdisk

After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the XP partition, choose "boot", then choose **[COLOR="Red"]"Backup BS"[/COLOR]**, and have testdisk write the backup boot sector to the partition boot sector.
__________________

---

### Post by w1av on 2008-11-14
**[COLOR="DarkRed"]OK the rebuiuld seemed to work...here's what I got:[/COLOR]**

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  4978  80 63   79976610

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.





[  Quit  ]  [  List  ]  [Rebuild BS][Repair MFT][  Dump  ]
                            Return to Advanced menu

---

### Post by meierfra. on 2008-11-14
See my last post. But wait with the "rebuild BS" .

---

### Post by meierfra. on 2008-11-14
> OK the rebuiuld seemed to work...here's what I got:

O.K. go ahead and reboot (ignore my previous post)

---

### Post by w1av on 2008-11-14
woops, I already did a rebuild BS.......I hope this will work! I will reboot and see...

---

### Post by w1av on 2008-11-14
Naaaa...no good! I don't know what else to do now. Is it possible to use a WinXP full install disk to repair MBR? Please help if you know of any other option......

---

### Post by meierfra. on 2008-11-14
> Is it possible to use a WinXP full install disk to repair MBR?

Yes, that was essentially going to be my next suggestion. But lets first see whether you can access the Windows partition from ubuntu:


```
sudo mount -t ntfs-3g /dev/sda1 /mnt

ls -l  /mnt
```

---

### Post by meierfra. on 2008-11-14
Well it's time for me to call it a day. Try these next:

1) Edit menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

Replace the Windows item by

title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
chainloader +1


(I doubt that this will make a difference, but I don't want to miss an easy fix)


If this did not help:

2)  Boot from the XP CD. Enter the the repair console by pressing "r". Then

```
fixboot

chkdsk /r
```


"chkdsk /r" can take a while. Run it as often as needed (that is until it does not find anymore errors).  Type "exit" to reboot.


If this did not help:

3)    Boot from the XP CD and do a "Windows Repair".

---

### Post by w1av on 2008-11-14
OK Thanks for helping, and I rebooted a couple of times to no avail. I will do the steps above you mentioned last night and see what happens. I am waiting to build a new computer with a friend soon so maybe this will motivate me! Luckily I did store all my music files and important data to my slave drive and I believe I can still access the Windows partition in Nautilus....but I will try those things tonight...thanks...bob

---

