---
title: "No boot menu, xp has disappeared"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by Mariane on 2009-07-18
I tried installing ubuntu 9.04 from a burned CD on an old computer with 
windows xp. It had about 15 GB of free space and I ran the defragmenter 
several times. At the end it looked as though the largest continuous 
space was about 10 GB. 

Then I booted from the ubuntu CD and partitioned. It told me it could 
only find about 2.7 GB of continuous free space. I thought I would give 
it a try anyway. I have used ubuntu before but it is the first time 
I try to install it. 

Now Ubuntu is installed in a tiny space (it recommended updates but could 
not install them) so I guess it did partition only 2.7 GB for itself. But 
I have no boot menu. When I reboot it just starts ubuntu. 

I tried, from /  
```

find ./ -name WINDOWS

```

To see where the directory was. It was not found. Either it has been deleted 
or for some reason ubuntu cannot see it. I would like to have this dual 
system set up so that ubuntu can "see" windows files and windows cannot "see" 
ubuntu files. 

What should I do, please? 

Mariane

---

### Post by merlinus on 2009-07-18
Open a terminal, enter these commands and post results:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by Mariane on 2009-07-18
```


sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa16aa16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4539    36459486    7  HPFS/NTFS
/dev/sda2            4540        4865     2618595    5  Extended
/dev/sda5            4540        4843     2441848+  83  Linux
/dev/sda6            4844        4865      176683+  82  Linux swap / Solaris



cat /boot/grub/menu.lst
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
# kopt=root=UUID=59ea4443-7e43-4d7d-8107-f9bf415b496b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=59ea4443-7e43-4d7d-8107-f9bf415b496b

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		59ea4443-7e43-4d7d-8107-f9bf415b496b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=59ea4443-7e43-4d7d-8107-f9bf415b496b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		59ea4443-7e43-4d7d-8107-f9bf415b496b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=59ea4443-7e43-4d7d-8107-f9bf415b496b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		59ea4443-7e43-4d7d-8107-f9bf415b496b
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by merlinus on 2009-07-18
This all seems correct.  So you do not see the grub menu when you start your computer?  Just checking to be sure...

And the windows partition does not appear in Places/Computer?  It may be called disk something or other, or 20G disk, or something like that.

---

### Post by Mariane on 2009-07-18
Yes. It boots straight into ubuntu. 

Mariane

---

### Post by merlinus on 2009-07-18
You might try to mount the xp partition manually:

```
sudo mkdir /media/disk
sudo mount -t ntfs /dev/sda1 /media/disk
```Then use nautilus and navigate to that directory.

---

### Post by Mariane on 2009-07-18
Thanks! That's my windows xp stuff. Now what should I do to get the dual 
boot, please? 

Mariane

---

### Post by James58321 on 2009-07-18
try holding F8 on startup
-J

---

### Post by merlinus on 2009-07-18
Let's try reinstalling grub

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,4)
root (hd0,4) #use the numbers from the previous command
setup (hd0)
quit 
```

---

### Post by Mariane on 2009-07-18
```


grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


```

This looks promissing :) Rebooting now, and if I still don't see xp 
I will try holding F8. 

Mariane

---

### Post by p0cky84 on 2009-07-18
You could use the windows' boot loader also, just edit the boot.ini in you %HOMEDRIVE% (usually C:\)

[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)
[]("http://support.microsoft.com/kb/289022")

---

### Post by Mariane on 2009-07-18
The menu displayed but the keyboard was inactive, so I couldn't choose another operating system. 

When holding F8 there as no time limit but it was the same. This gave me time to experiment wit many keys and combinations but nothing worked. 

BTW my keyboard is Icelandic. 

Mariane

---

### Post by merlinus on 2009-07-18
Did you select that keyboard layout whilst installing?  You might also check in System/Preferences/Keyboard.

Strange, though, that the up-and-down arrow keys and Enter would not work at the grub menu...

---

### Post by Mariane on 2009-07-18
Yes, I selected it. Most keys, including arrows, are the same, there are just a few extra letters.
System/Preferences/Keyboard tells me it is as it should. And once ubuntu is runing it works fine. 

Mariane

---

### Post by merlinus on 2009-07-18
Just checking -- did you shut down completely, or simply restart?  Can you unplug the keyboard whilst the computer is shut down, and then try reinserting it?

Also, you might look in bios to see if there are any keyboard settings.

---

### Post by Mariane on 2009-07-18
Tried typing 
```

sudo shutdown now

```
This got me to a recovery menu in which the arrowkeys were fully functional. 

Then shut down throught the "Switch user" option, unplugged and replugged (usb keyboard). No luck. 

I just tested with the text editor, typed a few lines and navigated through them with the arrow keys. No problem there. 

Mariane

---

### Post by livigagl on 2009-07-18
If the keyboard is USB I think that you should enable in the BIOS the Legacy USB support.

---

### Post by Mariane on 2009-07-18
Found it! Yes, in the setup menu it said usb keyboard disabled. 
Thank you. 

Mariane

---

### Post by livigagl on 2009-07-18
You have to enter in the BIOS clicking either F2 or F10 or Del (it depends from your PC) during the POST (Power On Self Test) and then you have to search the USB Legacy support.
If it is not enable, switch it, save and exit from the BIOS.
There are many different BIOS so I can't tell you more information, just try, it's not so difficult! ;-)

Wow you are much faster than my writing! :-)

Did it work?

---

### Post by Mariane on 2009-07-18
And it actually worked (I was half expecting windows to say "the security has been compromised and the system will shut down" or something). 

Mariane

---

### Post by livigagl on 2009-07-18
Excellent!

You did a great job! :D

---

### Post by |{urse on 2009-07-19
^^
[]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7638006")

---

