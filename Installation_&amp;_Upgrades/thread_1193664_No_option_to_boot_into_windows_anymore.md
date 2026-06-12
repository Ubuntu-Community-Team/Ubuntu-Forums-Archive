---
title: "No option to boot into windows anymore"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by I-Imaging on 2009-06-21
Hi guys,

I updated to the newest version of Ubuntu a few days ago but when I did my loading menu stopped recognizing windows as an option to boot into. I still have all my files accessible just can't log in.

After reading a bunch of stuff I think that this information would help. It's the info in the menu.lst file.

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, kernel 2.6.24-17-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-17-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro  single
initrd        /boot/initrd.img-2.6.24-17-generic

title        Ubuntu 9.04, kernel 2.6.22-14-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-386 root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-386
quiet

title        Ubuntu 9.04, kernel 2.6.22-14-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.22-14-386 root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro  single
initrd        /boot/initrd.img-2.6.22-14-386

title        Ubuntu 9.04, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I know very little about what I am doing so if you could reply with very basic instructions that would be appreciated. (it took me 2.5 days to figure out how to get my wireless working). :(

Thanks

---

### Post by merlinus on 2009-06-21
You probably noticed that there is no option at the end of menu.lst for booting windows.

Post results of:

```

sudo fdisk -l

```

---

### Post by I-Imaging on 2009-06-21
I did notice, but I don't know what to do about it. ;)

Here is the results:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  de  Dell Utility
/dev/sda2               7       15295   122808892+   7  HPFS/NTFS
/dev/sda3           15296       19457    33431265   83  Linux
jeremy@jeremy-laptop:~$ 
jeremy@jeremy-laptop:~$ 

Thanks for the help.

---

### Post by merlinus on 2009-06-21
Try adding this to the end of menu.lst:

title windows
rootnoverify (hd0,1)
makeactive
chainload +1

Then restart.

You may also have to delete the boot flag from sda1 and activate it on sda2.  You can do this with gparted, either from the live ubuntu cd or by installing it from Applications/Add/Remove.

But try the first before doing this.

---

### Post by I-Imaging on 2009-06-21
I do that by pressing Alt+F2 and running gksu gedit /boot/grub/menu.lst right? Then once in there add your code at the end?

That's what I'll try then I'll get back to you on if it worked. Thanks.

---

### Post by I-Imaging on 2009-06-21
"windows" comes up in the options to load but it's last and I can't select it. 

The other operating system is Vista Business 32 bit... if that makes a difference?

---

### Post by merlinus on 2009-06-21
The down arrow key does not work at the grub menu?  Do other keys work, such as Enter?

If so, press e when the menu appears, and see if you can arrow down to the line that boots windows.  Then press b.

---

### Post by presence1960 on 2009-06-21
when you post a lot of text, please highlight the text then click the # key on the toolbar to place code tags around the text. example my menu.lst :
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
timeout		4

## hiddenmenu
 Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c94e2af2-c9a2-49b5-ba8f-357853bf3e23

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

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 7 RC
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

title           Hardy 8.04
rootnoverify    (hd0,2)
chainloader     +1
```

Thanks, I know you probably didn't know to do that, but it makes reading threads easier for everyone

---

### Post by merlinus on 2009-06-21
Hey presence, I didn't know that either!  I manually enter the code tags. This is much easier.  Thanks!

---

### Post by I-Imaging on 2009-06-21
> **merlinus said:**
> The down arrow key does not work at the grub menu?  Do other keys work, such as Enter?

If so, press e when the menu appears, and see if you can arrow down to the line that boots windows.  Then press b.

Sorry, I can move the arrows but when I hit enter nothing happens.

> **presence1960 said:**
> when you post a lot of text, please highlight the text then click the # key on the toolbar to place code tags around the text. example my menu.lst :

Thanks, I know you probably didn't know to do that, but it makes reading threads easier for everyone

I didn't know that, thanks! It looks way better that way. I updated the post. :)

---

### Post by presence1960 on 2009-06-21
> **I-Imaging said:**
> Sorry, I can move the arrows but when I hit enter nothing happens. I will try again and press b to see if it makes a difference.

Do you have a USB keyboard? Some people have trouble with those. The solution is to go into BIOS and enable Legacy USB

---

### Post by I-Imaging on 2009-06-21
> **presence1960 said:**
> Do you have a USB keyboard? Some people have trouble with those. The solution is to go into BIOS and enable Legacy USB

No I don't have a usb keyboard. I'm using a laptop for this without anything fancy like that.



Ok I figured out a way to get into vista but it's a pain.

Once in the boot menu I go to my "windows" option and edit it. In there I press o to add something new and type in chainload +1. Then I can press enter and it will proceed to the login screen. I have to do that manually each time I want to run vista though. I really don't understand what I'm doing in the menu.lst

I tried gparted too. I have clicked on "manage flags" and changed it to the proper partition but every time I reboot it's back to the original.

---

### Post by presence1960 on 2009-06-22
> **I-Imaging said:**
> No I don't have a usb keyboard. I'm using a laptop for this without anything fancy like that.



Ok I figured out a way to get into vista but it's a pain.

Once in the boot menu I go to my "windows" option and edit it. In there I press o to add something new and type in chainload +1. Then I can press enter and it will proceed to the login screen. I have to do that manually each time I want to run vista though. I really don't understand what I'm doing in the menu.lst

I tried gparted too. I have clicked on "manage flags" and changed it to the proper partition but every time I reboot it's back to the original.

you probably need to add chainload +1 to your windows entry in menu.lst
open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```

try this for windows Vista entry:

> title windows vista
rootnoverify (hd0,1)
chainload +1

P.S. look at my menu.lst in post #8 to see where you need to add the windows entry. You don't need the map lines in the windows entry. I have them because windows is on a different hard disk than Ubuntu.

---

### Post by I-Imaging on 2009-06-22
Awesome! That worked. 

How do I make it at the top as the first option so it will default into there? (I'm trying to get away from windows but don't have the skills to leave it yet).

Also why are there so many Ubuntu options when I log in? Can I remove some of those options?

Thanks.

---

### Post by presence1960 on 2009-06-22
> **I-Imaging said:**
> Awesome! That worked. 

How do I make it at the top as the first option so it will default into there? (I'm trying to get away from windows but don't have the skills to leave it yet).

Also why are there so many Ubuntu options when I log in? Can I remove some of those options?

Thanks.

Those Ubuntu options are different kernels. I would keep the two latest kernels, in case one has a problem you can boot into the other. There should also be a recovery mode option for each kernel. Keep the memtest option also.

Here is a peek at mine so you can see what I am saying.
```

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-12-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
initrd		/boot/initrd.img-2.6.28-12-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=c94e2af2-c9a2-49b5-ba8f-357853bf3e23 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		c94e2af2-c9a2-49b5-ba8f-357853bf3e23
```

You can open a terminal and run ```
sudo apt-get install startupmanager
```
This will install a GUI program which will let you choose the default startup choice and much more.
you can run startupmanager by going System > Administration > StartupManager or in terminal > gksu startupmanager

BTW when you run graphical programs in terminal use gksu- examples startupmanager, nautilus, gedit. Non-graphical use sudo.

---

### Post by presence1960 on 2009-06-22
> **I-Imaging said:**
> Also why are there so many Ubuntu options when I log in? Can I remove some of those options?
Thanks.

you can comment them out by prefacing them with # (see how I commmented out the Ubuntu 9.04, kernel 2.6.28-11-generic)
 or ```
 gksu gedit /boot/grub/menu.lst
``` and remove the older ones. I would leave the two newest kernels in there just in case something happens to the newest kernel and it can't boot. Leave the corresponding recovery mode entries for the kernels you keep.

---

### Post by I-Imaging on 2009-06-22
Presence thanks for all the help. So far things seem to be progressing but the options I change in the Start-Up manager don't seem to make any effect. 

Can I just change it in the menu.lst file? I found this [page]("http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/") and though it may work if I just changed the number. Is that accurate? If it is how do I know which number to put in? Do I count the ones that I changed to comments? 

```
## ## End Default Options ##


title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

#title        Ubuntu 9.04, kernel 2.6.24-17-generic
#root        (hd0,2)
#kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro quiet splash 
#initrd        /boot/initrd.img-2.6.24-17-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.24-17-generic (recovery mode)
#root        (hd0,2)
#kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro  single
#initrd        /boot/initrd.img-2.6.24-17-generic

#title        Ubuntu 9.04, kernel 2.6.22-14-386
#root        (hd0,2)
#kernel        /boot/vmlinuz-2.6.22-14-386 root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro quiet splash 
#initrd        /boot/initrd.img-2.6.22-14-386
#quiet

#title        Ubuntu 9.04, kernel 2.6.22-14-386 (recovery mode)
#root        (hd0,2)
#kernel        /boot/vmlinuz-2.6.22-14-386 root=UUID=b07abcda-a6ee-48a5-bced-d8542f09a489 ro  single
#initrd        /boot/initrd.img-2.6.22-14-386

#title        Ubuntu 9.04, memtest86+
#root        (hd0,2)
#kernel        /boot/memtest86+.bin
#quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Windows Operating Systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Vista Business
rootnoverify    (hd0,1)
chainloader    +1
```And just to make it clear for me... making just two options "Ubuntu" and "Vista" isn't a good option? It's better to have a couple versions in case I mess something up? I'm just looking to have the boot menu as clean and sleek as possible (and simple).

Thanks again.

---

### Post by presence1960 on 2009-06-22
I just thought of this. You can comment everything out except the most recent kernel and windows. If something happens and you can't boot into another kernel you can always boot off the Ubuntu Live CD and uncomment a kernel in menu.lst. Then reboot into that kernel. I would keep the recovery mode option available. So there you can have Ubuntu, Ubuntu recovery mode & Vista.

---

### Post by I-Imaging on 2009-06-22
Thanks for all your suggestions, it's been really helpful.

---

### Post by presence1960 on 2009-06-22
> **I-Imaging said:**
> Thanks for all your suggestions, it's been really helpful.

we are all here for each other. BTW welcome to the best online community of which I have been a member. The opportunities are here to learn not only Linux, but computers in general.

---

### Post by I-Imaging on 2009-06-23
Thanks I will be back often I'm sure. :)

---

