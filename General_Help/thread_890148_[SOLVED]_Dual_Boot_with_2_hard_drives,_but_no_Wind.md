---
title: "[SOLVED] Dual Boot with 2 hard drives, but no Windows"
date: 2008-08-14
forum: General Help
---

### Post by Sef on 2008-08-14
To help out a group, I installed Ubuntu on their computer.  It had two hard drives, so I installed Ubuntu on the one without XP.  Ubuntu boots fine, but there is no option for XP.

I know that the problem is that Ubuntu is on sda1 and XP is on sdb1.  I tried [Herman's tutorial]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot") a few times.  At first, I got a message that stated GRUB error 23; however, eventually, it said that NTLDR was missing.  

What can I do to get both as an option?

---

### Post by LowSky on 2008-08-14
heres what my Grub list looks like it should be very simular to what you need i modified in **BOLD** what I think you may need to be careful about

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
# kopt=root=UUID=128cb256-452d-4803-b436-543076441748 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root		(hd0,6)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=128cb256-452d-4803-b436-543076441748 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
**root		(hd0,6)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=128cb256-452d-4803-b436-543076441748 ro single
initrd		/boot/initrd.img-2.6.24-19-generic


title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
[B]root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)[/B]
chainloader	+1

```

---

### Post by Sef on 2008-08-14
How do I get into the GRUB list?

And thanks, I will try it when I go there again.  The place is about 3 hours from me, so it is not a quick jog over.

If anyone else has any other ideas, I would appreciate them too as you can see it is not easy for me to go there often.

---

### Post by Mgiacchetti on 2008-08-14
I'm wondering that since you have ubuntu on sda1 and windows on sdb1, was windows always on sdb1?  

If Windows was c: and now its d: (even though the ubuntu drive wont be seen by windows, the bios still attributes it a letter) You may have a lot of registry paths to change...

I may be wrong though... Just throwing this in to make sure...

---

### Post by Mgiacchetti on 2008-08-14
First, create a backup in case things get muffled up.
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp #copy verbatim

```
then
```

gksudo gedit /boot/grub/menu.lst #

```

---

### Post by Sef on 2008-08-18
I still can't get into Windows.  It does not show as an option except when I go into GRUB.  When I go into Windows, it says NTLDR is missing.

What can be done to fix this problem?

---

### Post by caljohnsmith on 2008-08-18
Can you post your /boot/grub/menu.lst? Also please post:
```
sudo fdisk -lu
```
And when you are in Ubuntu, can you mount the Windows partition? If so, check to see if it has the following three files in its root directory:
```
ntldr
boot.ini
NTDETECT.COM
```
Of course the "ntldr" file is the most crucial file at this point, since the error you got said Windows couldn't find that file. And do you have the Windows Install CD? That can be used to repair the boot sector of the Windows partition, but you probably don't need to do that just yet.

---

### Post by Sef on 2008-08-18
```
sudo fdisk -lu
```

> /dev/sdb1   *          63   312576704   156288321    7  HPFS/NTFS


```
/boot/grub/menu.lst
```

> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6599c3d0-e5f3-409e-96ee-c112d44ecfff ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6599c3d0-e5f3-409e-96ee-c112d44ecfff ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


> And when you are in Ubuntu, can you [mount the Windows partition]("http://ubuntuforums.org/showthread.php?p=5617969#post5617969")?

This is what I get

> gic09@gic09-desktop:~$ sudo mount -t ntfs /dev/sdb1 /media/windows -o umask=0000 
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/windows ntfs-3g force 0 0


What is the relevant row?

---

### Post by Sef on 2008-08-19
Resolved.  I reinstalled Windows on sda and Ubuntu on sdb.  I did this due to time constraints.

---

### Post by hkhalsa on 2008-08-20
I have a similar but slightly different issue.  I installed Ununtu on a USB disk connected to a laptop.  The laptop which does not sufficient space to install Ubuntu on its HD.  The installtion worked OK except that I must have the USB drive connected even if I intent to use Windows.  Is is possible for the boot screen to come up and default to run Windows if the USB drive is not connected.

Thanks.

---

### Post by bitninja on 2008-08-20
Which version of Windows do you have?

---

### Post by bitninja on 2008-08-20
Actually whether it's XP or Vista (I believe this tool works for both) and should write a standard MBR to your drive that can boot Ubuntu or Windows:

[http://www.vistabootpro.org/](http://www.vistabootpro.org/)

If you set it to boot to Windows by default, it will always boot to it and then when your USB drive is connected you can boot to Ubuntu by choosing it. Unfortunately I don't think there's any way to get it to automatically choose for you depending on whether the USB drive is connected or not.

---

### Post by falcon61102 on 2008-08-20
Sef,

The problem you ran into is a common Windows problem.  Windows was designed by microsoft to only run as the primary drive of the system so it has a hard time any time someone tries to backburner it.  This inflexibilty is a design flaw that makes our lives miserable when trying to dual-boot, especially when we just want a small backup windows system.  Luckily there has been some real talent in finding ways around it with the GRUB and whatnot, but I've found your fix to be the easiest.  Just install Windows first even if it's going to be the secondary system just to appease it.

---

### Post by falcon61102 on 2008-08-20
hkhalsa,

Sounds like when you installed Ubuntu to your USB drive, you installed the GRUB to the MBR (Master Boot Record) with the startup files on the USB drive.  Not a big deal, but it leaves your where your at.  To get back to normal, you simply need your install disk or a restore tool such as the one suggested above.  With the install disk or the restore tool you can restore your Windows MBR which will allow you to boot up as normal.

To be able to automatically boot to your USB drive only when it's plugged in, set your BIOS start up priority to have your USB drive first with the internal HD lower on the list.  This way when the USB drive is plugged in, it will automatically start the GRUB and you can boot to Ubuntu and when it's not plugged in, Windows will start up as normal.  I use the same system at work.  If you need more detailed instructions or have trouble, post up here and we can help.

---

### Post by hkhalsa on 2008-09-04
Thank you Gentlemen for the advise.  I used the Windows XP CD to start up the computer.  Then I used DOS command FIXMBR but there was no change.  Finally I use FIXBOOT.  With this change the computer started with Windows.  I changed the bios setup with priority to USB drive.  However even with the Ubuntu USB drive plugged in before turning on the computer, the computer still starts up on Windows.  Your advise please.
Best Regards.

---

### Post by falcon61102 on 2008-09-04
The computer may still not be booting from the USB drive.  When you start up, often times you can press a function key (F11 for instance) and that will give you a menu to choose the boot device.  Try that method.

If that does not work, you may have to reinstall the GRUB on the USB drive for some reason.

---

### Post by hkhalsa on 2008-09-05
Thank you very much Falcon.

I have tried the function key, F12 on my laptop.  This gives option to start from USB drive.  Selecting this option still starts Windows from the laptop internal HD.  This means I will have to install grub on the USB disk.  How do I install grub on the USB disk?

Best Regards.

---

### Post by falcon61102 on 2008-09-05
If you boot from a LiveCD you can open a terminal and install it from there.
Make sure your USB drive is plugged in and mounted.  Then run:
```
sudo grub
find /boot/grub/stage1
root (hdX,Y)
setup (hdX)
quit
```
When you run the find command, the result is going to look something like (hd1,0).  That is what you are going to use for the root command.  Then for the setup command leave off the last number so it would be (hd1).

---

### Post by hkhalsa on 2008-09-05
Thanks Falcon,

I have done as you advised.  I started Ubuntu with the CD and typed what you advised using Ubuntu Terminal.  I hope this was correct.  With this done, when the USB disk is out Windows starts normally.  When the USB is connected, Grub loads and gives me pagge with options 

Ubuntu 8.04.1, kernal 2.6.24-19-generic
Ubuntu 8.04.1, kernal 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, kernal 2.6.24-16-generic
Ubuntu 8.04.1, kernal 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, metatest86+
Other operating systems:
Microsoft Windows XP Home Edition

Note that at the bottom of the page there is, enter to boot,  'e' can be used to edit the commands before booting, or 'c' for a command line.

If I select any of the Ubuntu options the following message comes up
Error 17: Cannot mount selected partition
Press any key to continue...

If I select MS Windows option, I get the message
Error 12: Invalid device requested
Press any key to continue...

Pressing any key in both cases brings back the options page.

Note that at the bottom of the page, it states that 'e' can be used to edit the commands

Your advise please.
Best Regards.

---

### Post by falcon61102 on 2008-09-06
Could you post the following;

Results of:
```
sudo fdisk -l
```
-l being a lower case L

And the contents fo your menu.lst from the USB drive.

---

### Post by hkhalsa on 2008-09-06
Thanks Falcon,

The list from "sudo fdisk -l" is as follow:

Disk/dev/sda: 40.0 GB, 40007761920 bytes
255, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065*512=8225250 bytes
Disk identifier: 0x9dc96e9e

Device     Boot    Start    End    Blocks    Id    System
/dev/sda1              1      5     40131    de    Dell Utility
/dev/sda2     *        6   4863  39021885     7    HPFS/NTFS

Disk/dev/sda: 120.0 GB, 120034123776 bytes
255, 63 sectors/track, 14593cylinders
Units = cylinders of 16065*512=8225250 bytes
Disk identifier: 0x8f9c798a

Device     Boot  Start    End     Blocks  Id  System
/dev/sda1            1  14216 114189988+  83  Linux
/dev/sda2        14217  14593   3028252+   5  Extended
/dev/sda5        14217  14593   3028221   82  Linux swap/Solaris

Two "menu.lst" files were found using search.  They are "menu.lst" 1.9 kB dated 10 April 2008 and "menu1.lst" (menu.lst renamed menu1.lst) 4.9 kB dated 16 April 2008.  I have zipped the two files as menu.zip.

Thanks and Best Regards.

---

### Post by caljohnsmith on 2008-09-06
Hkhalsa, it looks like fixing your problem will be as simple as modifying your menu.lst. The menu.lst in that zip file named "menu1.lst" is the one you want to modify, and if you change your entries as follows, I think everything should work:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8eb1c7b5-1bc1-4229-a040-0df73f1314c8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Change all the Ubuntu entries in that menu.lst to use (hd0,0) instead of (hd1,0). Also change the Windows entry:
```
title		Microsoft Windows XP Home Edition
[COLOR="Red"]root		(hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
savedefault
makeactive
chainloader	+1
```
Unless there are other issues, that should be all it takes to get Ubuntu and Windows booting OK from your USB drive. Let us know how it goes.

---

### Post by hkhalsa on 2008-09-07
Hi Caljohnsmith,

Thanks for your advise and help.  I tried to modify the menu files but I do not have permission to change and save the file.  When I tried this I was running Ubuntu from a CD.  How do I get permission to modify the "menu.lst" file?  My apologies if this query is very basic.  I am only just starting to use Ubuntu.

Thanks and Best Regards.

---

### Post by caljohnsmith on 2008-09-08
> **hkhalsa said:**
> Hi Caljohnsmith,

Thanks for your advise and help.  I tried to modify the menu files but I do not have permission to change and save the file.  When I tried this I was running Ubuntu from a CD.  How do I get permission to modify the "menu.lst" file?  My apologies if this query is very basic.  I am only just starting to use Ubuntu.

Thanks and Best Regards.
Did you by chance type the output of "sudo fdisk -l" by hand in your post #21? Because both your 40 GB and 120 GB drives are both labeled as "sda", which would be impossible. If it is indeed an error, is your 120 GB drive actually "sdb"?

---

### Post by hkhalsa on 2008-09-09
Hi Caljohnsmith,

Thank you.  You are correct.  It should be "../sdb".  I typed the text myself (since then, I did not know better) and made an error.  Attached please "sudo fdisk -l" in attached text file prepared with Ubuntu Text Editor.

Best Regards.

---

### Post by caljohnsmith on 2008-09-09
Hkhalsa, please boot up your USB drive so that you get the Grub's menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)", press "e" to edit it, then change it to "root (hd0,0)". Press return, then press "b" to boot the Ubuntu entry that you just modified. That should allow you to boot Ubuntu. 

If that works, when you get into Ubuntu, open a terminal and do:
```
gksudo gedit /boot/grub/menu.lst &
```
Find the lines that have your Ubuntu entries, and change all the (hdX,Y) to (hd0,0). Lastly, change your Windows entry to be:
```
title		Microsoft Windows XP Home Edition
root		(hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader	+1
```
Let me know how it goes or if you run into problems.

---

### Post by hkhalsa on 2008-09-10
Hi Caljohnsmith and Falcon,

Thank you very much.  The system works excellent.  I am so pleased.  Grub starts up when USB disk is in.  The options for Ubuntu as well as Windows works fine.  When USB is not connected, Windows starts up normally.  

This is fantastic.  Thank you very very much for all the help.

Best Regards.

---

### Post by falcon61102 on 2008-09-10
Glad it worked out for you.

---

### Post by Dragonbite on 2010-01-04
Are there any changes in doing this with Windows 7 and Ubuntu 9.10?

I think Ubuntu uses Grub2, so is this going to make things different for editing the menu listing?

I think there were issues installing dual-boot with Windows Vista, so I wonder if the entry required for Windows 7 is going to be different than for Windows XP?

I am looking to have 2 hard drives installed, one Windows one Ubuntu.  The Ubuntu one may be getting installed first (hdb) and then later I want to disconnect the Ubuntu hard drive and install Windows 7 on the other hard drive (hda).

I'm suspecting if I set up the BIOS to boot from the Ubuntu (hdb) hard disk and have Windows listed in the GRUB, and then the Windows hard disk (hda) as the next boot device if the Ubuntu (hdb) hard disk is unavailable (e.g. removed).  At the same time, if the Ubuntu (hdb) hard disk is removed, the BIOS goes to the next device (hda) and boots the Windows that is on it.

---

