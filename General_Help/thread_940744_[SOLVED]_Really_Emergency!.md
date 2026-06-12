---
title: "[SOLVED] Really Emergency!"
date: 2008-10-07
forum: General Help
---

### Post by hackboy on 2008-10-07
Hi..i realy got to solve the problem..ok i had instaled winxp pro and then instaled ubuntu 8.04..now yesterday i formated the partition where ubuntu was instaled from winxp..then turned off my pc..today when i started my pc,i got some errors grub erors..i got so scared..i took the ubuntu cd and reinstaled it..now when i start my pc,winxp does not load..and in the file browser in ubuntu does not show up my winxp partition..i need an emergency help on this

---

### Post by overdrank on 2008-10-07
> **hackboy said:**
> Hi..i realy got to solve the problem..ok i had instaled winxp pro and then instaled ubuntu 8.04..now yesterday i formated the partition where ubuntu was instaled from winxp..then turned off my pc..today when i started my pc,i got some errors grub erors..i got so scared..i took the ubuntu cd and reinstaled it..now when i start my pc,winxp does not load..and in the file browser in ubuntu does not show up my winxp partition..i need an emergency help on this

Hi and could you post the output of this command in the terminal
```
sudo fdisk -l
``` that is a lower case L. then we can tell if you have installed and deleted the windows partition.

---

### Post by hackboy on 2008-10-07
The Output i got is 
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf222f222

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9729    62790052+   5  Extended
/dev/sda5            1913        8585    53600841    7  HPFS/NTFS
/dev/sda6            8586        9215     5060443+  83  Linux
/dev/sda7            9216        9729     4128673+  83  Linux


```

---

### Post by caljohnsmith on 2008-10-07
If you can boot into Ubuntu, open a terminal (applications > accessories > terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom of the file add:
```
title Windows XP Professional
root (hd0,0)
chainloader +1
```
Reboot, and let us know what happens when you select Windows from the Grub menu.

---

### Post by hackboy on 2008-10-07
Nothing loads. Just did what u instructed..is my xp gone:( ?..

---

### Post by LowSky on 2008-10-07
XP isn't gone, or I sould really say the NTFS partition that XP should be isn't gone, which means you didn't delete it.

do us a favor and post the entire contents of the
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2008-10-07
It doesn't look like your Win XP is gone, but we need more info; while you are in Ubuntu, post the output of the following:
```
sudo mkdir /mount/sda1 /mount/sda5
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda5 /media/sda5
ls -l /media/sda1
ls -l /media/sda5
```
Note that "-l" is a lowercase L, not a one.

---

### Post by hackboy on 2008-10-08
I Got this output from terminal ```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sda5 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sda5 ntfs-3g force 0 0
burhanuddin@burhanuddin-desktop:~$ ls -l /media/sda1
ls: cannot access /media/sda1: No such file or directory
burhanuddin@burhanuddin-desktop:~$ ls -l /media/sda5
ls: cannot access /media/sda5: No such file or directory

```

---

### Post by caljohnsmith on 2008-10-08
OK, while you are in Ubuntu, open a terminal again and do:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo ntfsfix /dev/sda5
```
And if ntfsfix says it was successful on either of those partitions, use the directions from post #7 to list their contents.

---

### Post by geirha on 2008-10-08
Install the [ntfsprogs](apt://ntfsprogs) package, then run ```
sudo ntfsfix /dev/sda1
sudo ntfsfix /dev/sda5
```

Then try booting into windows. It should boot and run chkdsk on your windows drives, and after that it should work as normal again.

EDIT: Beaten to it by caljohnsmith :)

---

### Post by hackboy on 2008-10-08
The main prob is that i dont have internet.am posting from opera mini. But i can download the package file of ntfsprogs and then instal..may you please post the download link.

---

### Post by geirha on 2008-10-08
[http://packages.ubuntu.com/hardy/ntfsprogs](http://packages.ubuntu.com/hardy/ntfsprogs)

You'll probably need to download some of the dependancies too ... at least libntfs10

---

### Post by Bibek on 2008-10-08
If you have your windows xp cd, you can boot with it and when the installer shows the "Windows XP Professional Setup" Welcome to setup and all that stuff menu, select "R" for Recovery Console 
after providing the password and chosing which windows installation to repair , you get a dos prompt. in that prompt, type ```
 fixmbr 
``` . this should get you to your xp installation.

check this link for more info 
[http://www.windowsnetworking.com/articles_tutorials/wxprcons.html](http://www.windowsnetworking.com/articles_tutorials/wxprcons.html)

---

### Post by hackboy on 2008-10-08
Ntfsprogs worked like a charm..but stil my first win partition got an error - /dev/sda1 ..it told me to run chkdsk..pls tel me how to do it..my second partition is working great - /dev/sda5

---

### Post by geirha on 2008-10-08
Did you try to reboot into windows? ntfsfix will put a mark on the filesystem, saying it needs to be checked. If you boot windows, it should run chkdsk automatically. That is, if you got an windows entry in your grub menu. Paste the content of /boot/grub/menu.lst.

---

### Post by hackboy on 2008-10-08
Hi..again xp does not load from grub..heres my menu.lst
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
defaultçç0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeoutçç10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password Ä'--md5'Ñ passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 ¤1¤gLhU0/¤aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# titleççWindows 95/98/NT/2000
# rootçç(hd0,0)
# makeactive
# chainloaderç+1
#
# titleççLinux
# rootçç(hd0,1)
# kernelç/vmlinuz root=/dev/hda2 ro
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
## If you want special options for specific kernels use kopt§x§y§z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt§2§6§8=root=/dev/hdc1 ro
##      kopt§2§6§8§2§686=root=/dev/hdc2 ro
# kopt=root=UUID=19b89145-a32d-4a53-8083-05e48e32f550 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

titleççUbuntu 8.04.1, kernel 2.6.24-19-generic
rootçç(hd0,5)
kernelçç/boot/vmlinuz-2.6.24-19-generic root=UUID=19b89145-a32d-4a53-8083-05e48e32f550 ro quiet splash
initrdçç/boot/initrd.img-2.6.24-19-generic
quiet

titleççUbuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
rootçç(hd0,5)
kernelçç/boot/vmlinuz-2.6.24-19-generic root=UUID=19b89145-a32d-4a53-8083-05e48e32f550 ro single
initrdçç/boot/initrd.img-2.6.24-19-generic

titleççUbuntu 8.04.1, memtest86+
rootçç(hd0,5)
kernelçç/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
titleççOther operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
titleççWindows XP Professional
rootçç(hd0,0)
chainloaderç+1


```

---

### Post by Thelasko on 2008-10-08
In emergency situations like this, I've heard good things about the [super grub disk.]("http://www.supergrubdisk.org/")

Download it, burn it, boot it, and you should be able to get back into Windows.

---

### Post by unutbu on 2008-10-08
For some reason your menu.lst has some funny characters in it. Below are instructions for correcting the funny characters. 

Boot from the LiveCD
```

sudo mount /dev/sda6 /mnt
sudo mv /mnt/boot/grub/menu.lst /mnt/boot/grub/menu.lst-20081008
gksu gedit /mnt/boot/grub/menu.lst
```

Put this in /mnt/boot/grub/menu.lst:
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
default  0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  10

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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
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
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=19b89145-a32d-4a53-8083-05e48e32f550 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title  Ubuntu 8.04.1, kernel 2.6.24-19-generic
root  (hd0,5)
kernel  /boot/vmlinuz-2.6.24-19-generic root=UUID=19b89145-a32d-4a53-8083-05e48e32f550 ro quiet splash
initrd  /boot/initrd.img-2.6.24-19-generic
quiet

title  Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root  (hd0,5)
kernel  /boot/vmlinuz-2.6.24-19-generic root=UUID=19b89145-a32d-4a53-8083-05e48e32f550 ro single
initrd  /boot/initrd.img-2.6.24-19-generic

title  Ubuntu 8.04.1, memtest86+
root  (hd0,5)
kernel  /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title  Windows XP Professional
root  (hd0,0)
chainloader +1

```
Save, exit, reboot.

---

### Post by hackboy on 2008-10-08
Hi..i dnt get you, why do u want me to boot from the live cd..nd even if i loaded from the cd,the code u gave me won't work..specialy /mnt/...

---

### Post by hackboy on 2008-10-09
Is there any ******* way to solve this problem..i wil ban this ubuntu os..2 days have pased stil am ******* stuck..i just hate this ubuntu,i wana loginto windows which no1 is abled solve my prob.

---

### Post by sceo on 2008-10-09
You've pretty much, with the post above, burned all your bridges.  We all know you're frustrated, but taking it out on people who are trying to take time out of their day to try and help you, FOR NOTHING IN RETURN BUT YOUR THANKS, will pretty much get everyone to stop helping REAL FAST.

So, I would say that if you don't care about your Ubuntu partition at all, and just want Windows back, that you follow the directions above to put your Windows XP disc in, and press R to recover Windows.  Running "fixmbr" takes Ubuntu completely out of the equation and puts windows back in charge of booting your computer, so that there will be no more grub at all, no menu.lst to mess with, no booting into ubuntu, nothing.  Just put the Windows disc in, and tell it to repair the existing windows installation, or go into the Recovery Console and fixmbr.

There are a number of Windows resources to help you with the XP recovery process, but ubuntuforums.org isn't one of them.

---

### Post by hackboy on 2008-10-09
Thank you all for your wonderful help! I really appreciate for helping me and taking out your time for helping me.but anyways i got my solution.

---

