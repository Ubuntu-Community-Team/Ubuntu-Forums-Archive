---
title: "Help! Vista not booting in GRUB!"
date: 2008-08-26
forum: General Help
---

### Post by Vistux on 2008-08-26
Hey there, I only just got Ubuntu yesterday after installing it on my vista machine on another partition. Here's a rundown of my exact situation.

I have 1 500GB hard drive, the first partition (0,0) [I think this is sda2] is the Vista 'recovery partition, i believe. The second is my Vista os Itself (0,1) which i believe is sda3. the third is the ubuntu partition (0,3) on sda4. If i've got this wrong, i would really appreciate if you could give me some pointers of what to type into terminal so i can help you to help me further :)

I have vista installed first with all my files and programs etc, And i needed to boot it into safe mode to create a partition. I created a 40gb partition for Ubuntu, and thats when i restarted and installed ubuntu from cd. Heres something i may have done wrong. The partition bit in the ubuntu installation, i selected Manual and selected the 40b shrinked partition, didnt change the partition size, just clicked it and press create partition, or something like that. Another thing is for the bootloader i selected vista/longhorn bootloader, was that wrong too?

Anyway, I finished up the installation, restarted the pc, selected Ubuntu, installed updates, e.t.c. and Ubuntu worked fine. Then I restarted after having a play around, and on the grub menu I selected: Windows Vista/Longhorn Loader. Nothing happens.

So i booted back into ubuntu, researched a bit and found out i had to use sudo in terminal and open grub's menu.lst and i had to add:

title         "Windows Vista"
root         (hd0,1)
chainloader      +1

I thought I had a sata hard drive (well it says serial ATA... and I know for sata its meant to be sd(0,1) but all the others in menu.lst are hd(0,whatever) so i went with hd.

Then I saved menu.lst, rebooted, selected Windows Vista from GRUB, and i get:

BOOTMGR is missing, press ctrl + alt + del to restart.

Ok, so I'm officialy stumped. Any help? Great thanks to anyone who can offer any help :)

PS: Im a complete absolute noob to linux so please don't BLAM me for making a stupid mistake, i can comprehend how to work terminal but i don't know the necessary commands i need to type so i can get the info for you guys to help me. Please help me, and hopefully one day, when someone needs help, maybe i'll be in your position... If you need any more info for me to amke it clearer, just tell me what to do...

---

### Post by caljohnsmith on 2008-08-26
Don't worry, you've come to the most newbie-friendly forums in the world--we aren't going to flame you. So, welcome to the forums. :)

To make sure I understand your setup correctly, please boot into Ubuntu and post the output of the following commands:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
So to clarify, on startup, you get the Grub menu that allows you to select between Ubuntu and Vista, correct? And it's just Vista that's not working right now, is that right?

---

### Post by Vistux on 2008-08-26
Output of fdisk lu:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      128519       64228+   6  FAT16
/dev/sda2          129024    21100543    10485760    7  HPFS/NTFS
/dev/sda3   *    21100544   889931767   434415612    7  HPFS/NTFS
/dev/sda4       889936740   976768064    43415662+  83  Linux








Output of cat:

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
# kopt=root=UUID=78a0b2eb-be4a-4387-892a-aceb019d61a4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=78a0b2eb-be4a-4387-892a-aceb019d61a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=78a0b2eb-be4a-4387-892a-aceb019d61a4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1

title         "Windows Vista"
root         (hd0,1)
makeactive
chainloader      +1


Thanks for replying so quickly, i guess its only microsofters that flame :P And yes, you are correct

---

### Post by caljohnsmith on 2008-08-26
You've got two entries for Vista:
```
title Windows Vista/Longhorn (loader)
root (hd0,2)
savedefault
chainloader +1

title "Windows Vista"
root (hd0,1)
makeactive
chainloader +1
```
And according to your fdisk output, since the boot flag is set on sda3, that is probably your bootable Vista partition. That would mean your first entry above that uses (hd0,2) would be correct. I'm not sure exactly what you did in your Ubuntu installation process that made Vista unbootable, but you can most likely easily fix it by downloading the [Vista Recovery CD]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") (if you don't all ready have one), and running the following command from its CLI:
```
bootrec /fixboot
```
That fixes the boot sector of the Vista partition without harming the master boot record (MBR), which has Grub. But if that doesn't completely solve the problem, you might have to rebuild Vista's partition table with the following:
```
bootrec /rebuildbcd
```
Let me know how it goes.

---

### Post by Vistux on 2008-08-26
Ok, what do you mean by from it's CLI. I've burned it to cd, and it comes up with a boot folder, sources folder and a file called bootmgr. DO i have to boot from cd or something? Then what. Thanks for the help so far ;]

---

### Post by Vistux on 2008-08-26
Read the post above i've edited that, sorry for double posting if that's a rule on here.

---

### Post by caljohnsmith on 2008-08-26
Yes, you need to boot the Vista CD you downloaded, and then enter the recovery console or command line, whichever it is called. Here is a step-by-step guide:
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Vistux on 2008-08-26
Thanks, i got vista working, but now i don't see grub, its just takes me straight to vista when i boot. [I used bootrec /fixboot by the way]

---

### Post by caljohnsmith on 2008-08-26
> **Vistux said:**
> Thanks, i got vista working, but now i don't see grub, its just takes me straight to vista when i boot. [I used bootrec /fixboot by the way]
I think the only way you wouldn't see Grub is if you replaced the Grub MBR with the Vista one, and I believe that can only be done with:
```
bootrec /[COLOR="Blue"]fixmbr[/COLOR]

```
So you're sure you didn't do the above command? :-?

Anyway, to fix it, boot your Live CD, open a terminal, and do:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][will return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know if that works OK or if you get any errors.

---

### Post by Vistux on 2008-08-26
Problem: What do you mean by live cd, i put the ubuntu installation cd in and whent on use ubuntu without making any changes, went in terminal, found the x,y code to be 0,3... grub> root (hd0,3) did nothing, and grub> setup (hd0,3) came up with this error:

grub> setup (hd0,3)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd0,3)"...  19 sectors are embedd
ed.
succeeded
 Running "install /boot/grub/stage1 (hd0,3) (hd0,3)1+19 p (hd0,3)/boot/grub/sta
ge2 /boot/grub/menu.lst"... failed

Error 6: Mismatched or corrupt version of stage1/stage2

Again thanks with your help! (we're nearly there, we'll solve this!) :P





Also I had a look at the menu.lst and here's what it says at the bottom in its entirety, if it helps!

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=78a0b2eb-be4a-4387-892a-aceb019d61a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=78a0b2eb-be4a-4387-892a-aceb019d61a4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1

title         "Windows Vista"
root         (hd0,1)
makeactive
chainloader      +1




EDIT: I repeated it again and it said suceeded this time, I am going to reboot the pc now.. Wish me luck!



EDIT 2: Nope, came up with something along the lines of. Windows has not started up correctly, this may be due to a hardware of software change,

then it gave me an option to repair or start windows normally, should i repair? I started windows normally for now so i cold ask you guys.

---

### Post by caljohnsmith on 2008-08-26
> **Vistux said:**
> 
grub> setup (hd0,3)

Please read my instructions carefully, that should be "setup (hd0)" and not "setup (hd0,3)". :)

---

### Post by Vistux on 2008-08-26
Thanks, sorted! I <3 The Ubuntu community :D 

After i did the setup (hd0) I had to go on grub and select vista bootloader and blam, it works fine, along with ubuntu, cheers again cal :)

---

### Post by caljohnsmith on 2008-08-26
You're certainly welcome, I'm glad your system is working now. If you can, it would be good to click on the "thread tools" button near the top of the page and select the "mark as solved" (or whatever it says). :)

---

