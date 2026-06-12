---
title: "Partition Mess... Triple Booting"
date: 2008-08-28
forum: General Help
---

### Post by metroidnemesis13 on 2008-08-28
So, I've been using Windows for, say, 13 years and I'm sick of it crashing all the time, so I decided to install Ubuntu, and since my hard drive is 300 GB, I wanted to create 3 seperate partitions (one for my existing XP setup, one for Vista, and one for Ubuntu).  I've made quite a mess and sort of recovered with the SuperGrub program, and now I'm stuck.  This is what my GRUB loader screen looks like.  I'll explain in a second.  

Ubuntu blah blah (its the regular boot up)
Ubuntu recovery mode
Ubuntu ramtest
Ubuntu blah blah (its the regular boot up)
Ubuntu recovery mode
Ubuntu ramtest
Other Operating Systems:
Vista (loader)
Vista (loader)
Microsoft Windows XP Home Ed

What I actually have in partitions is a single Ubuntu partition (35.66, a swap partition (1.57 gb), a Windows XP Pro partition (55.88) which I was going to install vista on (the upgrade, thats why there are two vista loader partitions on there, I had a separate hard drive with two types of the vista install files that I was going to install and it must have incorporated that into the GRUB bootloader.  The hard drive is unplugged now and the partitions are still listed).  Those are all under "extended", and the NTFS WIN XP partition is 186.36 gb, on its own (not listed under extended; that's my main partition)

I would like to make the GRUB menu look like this at boot up, and actually be able to boot the right sectors...

Ubuntu
Vista (right now called Professional)
XP Home

The thing is, the only boots that work right now are the first Ubuntu on the list (it boots at hd(1,5) but I have to go in and manually change it to hd(0,5) to boot.  The other boot I've tried is the Vista line under Operating Systems, and it boots XP home ed on hd(0,0).... I've tried various number combos and I can't seem to pull up anything but Ubuntu and XP.  I'm a complete novice and I have practically no clue as to what I'm doing or what to do, so if you explain something or try to help, make it so a ten year old can do it.  Thank you very very much... I hope this gets figured out because it's beyond my understanding.

---

### Post by Bliepo32 on 2008-08-28
Could you just post the contents of menu.lst? You can view it by using this command:

```
sudo cat /boot/grub/menu.lst
```

---

### Post by metroidnemesis13 on 2008-08-28
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
# kopt=root=UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,5)
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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Windows Vista/Longhorn (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Bliepo32 on 2008-08-28
Alright. You will need to edit your menu.lst. But before we do anything at all, we will make a back-up first (just in case). Do it by running the following command:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Then we are going to edit menu.lst. Run the following command:

```
gksu gedit /boot/grub/menu.lst
```

If everything goes all right, you will now see a text editor. Select everything, and replace it with this:

```

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd1,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd1,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=fe85eac4-f565-4c15-8ca5-4fbb3136ed0f ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd1,5)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```

---

### Post by metroidnemesis13 on 2008-08-28
Okay, so I did what you told me to, and the ubuntu lines dont boot (I can boot ubuntu by changing 1,5 to 0,5 still) and now Vista Loader boots XP Home ed but the XP home line doesn't boot.  It did delete those 3 extra ubuntu lines though (thank you!)

---

### Post by metroidnemesis13 on 2008-08-28
Okay, I fixed all ubuntu lines myself and the XP home edition line, but the vista line still tells me the partition isnt there... how do I make that point to xp professional?  Thanks...

---

### Post by Bliepo32 on 2008-08-29
Can you please tell me how you partitioned your harddisk? Because that would be of great help.

---

### Post by metroidnemesis13 on 2008-08-29
I used the Ubuntu software off of a full install disk and shrunk the existing XP partition that I was using and then turned off the computer, installed xp pro, and then turned off the computer, and then installed ubuntu, and the grub loader didnt load so i got super boot grub off of the internet and used it to fix the grub loader, and it did, but it couldn't fix the partitions...

---

### Post by metroidnemesis13 on 2008-09-03
Anyone?  I'm probably going to repost if no one responds.

---

### Post by Jonie on 2008-09-03
We still don't know your partition layout. Please post what's the output of fdisk -l.?

```
sudo fdisk -l
```

---

### Post by metroidnemesis13 on 2008-09-03
montag@ubuntu:~$ sudo fdisk -l
[sudo] password for montag: 

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec00ec00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4998    40146403+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0afd0afd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24328   195414628+   7  HPFS/NTFS
/dev/sdb2           24329       36483    97635037+   f  W95 Ext'd (LBA)
/dev/sdb5           24329       31623    58597056    7  HPFS/NTFS
/dev/sdb6           31624       36278    37391256   83  Linux
/dev/sdb7           36279       36483     1646631   82  Linux swap / Sola

---

### Post by Jonie on 2008-09-03
Two more questions:

First, how does your menu.lst look now, after you fixed it?
Second, which drive is configured in the BIOS as your first boot device? The bigger or the smaller one?

Edit:
Isn't it that you had connected the smaller (ATA) disk to your system and things have become messed up since then?

---

### Post by metroidnemesis13 on 2008-09-03
it says 

ubuntu (regular boot)
ubuntu (recovery mode)
memtest
Vista (or professional, whatever you want to call it)
XP Home Edition

---

### Post by metroidnemesis13 on 2008-09-03
it says 

ubuntu (regular boot)
ubuntu (recovery mode)
memtest
Vista (or professional, whatever you want to call it)
XP Home Edition

Umm... by drives I'm assuming you mean partitions, this is all on one drive.  The big one is XP, the second biggest one (60 gb NTFS) is Professional, or what I want to be vista, and then the other few are for ubuntu (40 gb)

---

### Post by Jonie on 2008-09-03
I see from the output of fdisk that there are two physical hard disks (drives). 

And the question remains, which is configured to boot, i.e. from which one BIOS load GRUB.

This may be the only ambiguity, because if you followed bilepo32 advice I see no reason why both Microsoft systems should not boot.

---

### Post by Jonie on 2008-09-03
Of your windows partitions you can only boot (hd0,0) = /dev/sda1 = 40GB NTFS from first hard disk or (hd1,0) = /dev/sdb1 = first partition of the big disk (too lazy to calculate the size), "map" swapping is here required. 

/dev/sdb5 = (hd1,4) is a logical disk within an extended partition and cannot be booted by any version of Windows.

---

### Post by metroidnemesis13 on 2008-09-03
So does that mean I need to change it to a primary?

---

### Post by Jonie on 2008-09-03
Yes. There is room for yet another entry, but this could be tricky:


boot a live cd
start gparted
delete this logical ntfs
shrink the extended partition
note down start and end sectors of created free space
note down start and end sectors of shrunken extended partition
close gparted
start command line parted
delete shrunken extended partition
create new primary partition with the noted start and end sectors of the free space
create new extended partition with the noted start and end sectors of shrunken extended partition
use testdisk to recover logical drives in it

if you don't understand it 100% don't do it
wait for an opinion of another poster that may help better, this is only a draft

If you are going then to install windows to it and want to avoid restoring grub again, backup your mbr code

```
sudo dd if=/dev/sda of=mbr.bak bs=446 count=1
```

To restore GRUB after installing windows swap the if and of arguments.

```
sudo dd if=mbr.bak of=/dev/sda bs=446 count=1
```

This installation will probably carry the letter E: and will share it's boot files /dev/sda1:.

---

### Post by caljohnsmith on 2008-09-03
> **Jonie said:**
> Of your windows partitions you can only boot (hd0,0) = /dev/sda1 = 40GB NTFS from first hard disk or (hd1,0) = /dev/sdb1 = first partition of the big disk (too lazy to calculate the size), "map" swapping is here required. 

/dev/sdb5 = (hd1,4) is a logical disk within an extended partition and cannot be booted by any version of Windows.
Jonie, it is possible to boot Windows XP in a logical partition without too much trouble. He doesn't have to make it a primary partition to be bootable. Please see [Meierfra's guide]("http://ubuntuforums.org/showthread.php?t=813628") of how to do it. Probably it's too late now since he's most likely repartitioning as we speak, but anyway, it's not a big deal to boot Windows from a logical partition.

---

### Post by Jonie on 2008-09-04
We meet again on the sideways of multiboot :)

> Jonie, it is possible to boot Windows XP in a logical partition without too much trouble.

Yes, but AFAIK, you have to place it there with the help of cloning software. You still can't install Windows on that volume.

>  He doesn't have to make it a primary partition to be bootable. Please see Meierfra's guide of how to do it.

There has to be a FAT/NTFS primary active partition with XP boot files on it. And the best method is to boot from it, then pointing from boot.ini to the logical disk. Following this above method may raise some stability issues in certain situations (BSODs) as it is totally unsupported.

The most interesting issue (off topic) happens when you reformat primary active NTFS volume with ext3 or another Linux/UNIX FS, still being of type 0x7 (NTFS). A Windows XP CD does not start anymore! Neither PE, however the latter could run from USB. In such scenario having XP installation on logical drive means to a certain extent an unreparable installation.

---

### Post by caljohnsmith on 2008-09-04
> **Jonie said:**
> We meet again on the sideways of multiboot :)
I want my knowledge of multibooting to be as accurate as possible, so I enjoy discussing these topics with you as you obviously have a lot of experience with them. I hope you don't mind. :)
> **Jonie said:**
> 
[COLOR="Blue"]There has to be a FAT/NTFS primary active partition with XP boot files on it[/COLOR]. And the best method is to boot from it, then pointing from boot.ini to the logical disk. Following this above method may raise some stability issues in certain situations (BSODs) as it is totally unsupported.

That has been the conventional thought for a long time, but it is actually not true; I would agree with you that putting the bootable files on a primary partition has been a workaround that some people have successfully used to get Windows XP to boot off a logical partition,* but it is not necessary* if you use the method meierfra gives in that guide I linked to. Using his method, Windows stays entirely self-contained within its logical partition (no files elsewhere). His method to boot Windows from a logical partition is really quite simple and can be summarized as:
[LIST=1]
[*]For the Windows entry in Grub, make sure to omit the "makeactive" option, because Grub can not make a logical partition active (i.e. set the boot flag on), and it is not necessary for the Windows partition to be active to boot.
[*]Then modify the Windows boot.ini file (which still resides on the logical partition, as all the other boot files), so that it uses the correct partition number. To figure that out, all primary and logical partitions are counted, but the extended partition itself is not.
[/LIST]
That's all it takes, and it really does work. :)
> **Jonie said:**
> 
The most interesting issue (off topic) happens when you reformat primary active NTFS volume with ext3 or another Linux/UNIX FS, still being of type 0x7 (NTFS). A Windows XP CD does not start anymore! Neither PE, however the latter could run from USB. In such scenario having XP installation on logical drive means to a certain extent an unreparable installation.
I don't think I understand what you are saying: if you format the NTFS partition to be ext3 or some other Linux FS, why wouldn't the FS ID obviously be changed to 83 or something other than the original 0x7 for NTFS?

---

### Post by metroidnemesis13 on 2008-09-06
Hey, guess what guys, I figured it out.  I used a Vista install disk and basically erased the 60 GB spot (where XP Professional was) and installed Vista.  When I tried booting XP, it brought me to a kind of Windows boot loader that said boot Vista or earlier versions of windows, and it works just like I thought it would.  Thanks for your help, guys.

---

