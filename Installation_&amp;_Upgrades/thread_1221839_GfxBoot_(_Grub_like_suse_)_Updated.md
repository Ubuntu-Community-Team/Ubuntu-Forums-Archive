---
title: "GfxBoot ( Grub like suse ) Updated"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by lookinggoodson on 2009-07-24
Please follow this guide to get the SUSE boot screen in ubuntu 9.04:


This works for an i386 PC running ubuntu 9.04

(you will need your user password, enter it when asked)


**1. **

Goto http:[//www.sidux.com/debian/pool/main/g/grub-gfxboot/]("//www.sidux.com/debian/pool/main/g/grub-gfxboot/")

Download the latest version for your architecture

In my case "grub-gfxboot_0.97-43_i386.deb"

Find out where it was saved (probably your desktop)


**2.**

Open a terminal and copy and paste the below and hit return

*sudo apt-get remove grub*


**3.**

Install grub-gfxboot_0.97-43_i386.deb either by double clicking it or pasting the below command in the terminal and hitting enter

*sudo dpkg -i grub-gfxboot_0.97-35_i386.deb *

(Note you need to be in the same directory as the install file in the terminal)


**4.**

Now in the terminal paste the below

*sudo grub*

grub> *find /boot/grub/stage1* (note dont paste the grub>)
(hdx,y) (dont paste this line, its an output)

grub> *root (hdx,y)* (enter the x,y from the output about)

grub> *setup (hdx)*

*quit* (type quit to exit grub)


**5.**

Now paste the below in the terminal and hit enter

*sudo grub-install /dev/sda*


**6.**

Now you need to get the SUSE boot screen (this is where most issues happen and it took me a long time to figure it out)

Goto System -> Administration -> Synaptic Package Manager (on the ubuntu menu)

Enter password

Paste the follwing in the search box and mark for installation "gfxboot-theme-suse" and hit Apply

Install all dependencies and finish the install


**7.**

Open a terminal and paste the below and hit enter after each line

*cd /usr/share/gfxboot-theme-suse/*

*sudo make*

*sudo make install*

(ignore all errors)


**8.**

Now open a terminal and paste the following and hit enter

*sudo nautilus*

The file manager will open.

Navigate to /usr/share/gfxboot-theme-suse/boot

There should be a file called "message" in the folder

You now need copy this file to the below folder

/boot/grub/

And rename it to message.suse


**9.**

Now open a terminal and paste the below

*sudo gedit /boot/grub/menu.lst*

Add the below line to the begining of the file 

gfxmenu /boot/grub/message.suse

Click save and close




This worked for me hopefully it will work for you:

---

### Post by Intrepid Ibex on 2009-08-13
Niiiiccceeeeee..

Thanks man.

**Edit:** just a little nitpicking O:):

> **3.**

Install grub-gfxboot_0.97-**43**_i386.deb either by double clicking it or pasting the below command in the terminal and hitting enter

*sudo dpkg -i grub-gfxboot_0.97-**35**_i386.deb *See the difference :wink:?


> **5.**

Now paste the below in the terminal and hit enter

*sudo grub-install /dev/sda*Not everyone has their [COLOR=Black]grub[/COLOR] on their first hd.


> **8.**

Navigate to /usr/share/gfxboot-theme-suse/boot

There should be a file called "message" in the folder

You now need copy this file to the below folder

/boot/grub/This would be easier with: 
```
sudo cp /usr/share/gfxboot-theme-suse/boot/message /boot/grub/message.suse
```Of course the file can be renamed to anything if you change the name in menu.lst too. Also I prefer having folder 'messages' on /boot/grub so that I can have all my messages in a separate place (you can get more themes on [http://www.gnome-look.org/](http://www.gnome-look.org/) and [http://www.kde-look.org/](http://www.kde-look.org/)). So if you also want to have separate place for your messages, then you could e.g. do this:
```
sudo mkdir /boot/grub/messages && mv /boot/grub/message.suse /boot/grub/messages/message.suse
```> **9.**

Add the below line to the begining of the file 

gfxmenu /boot/grub/message.suseIf you just put the gfxmenu line before the kernel/os options, it will be fine. E.g my menu.lst (**OBS.** don't replace your kernel lines with mine!):
```
default        0

timeout        10

# Pretty colours

color white/black yellow/red

# Gfxboot

**gfxmenu /boot/grub/messages/message-8**

#List

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
# kopt=root=UUID=e6dee6d0-03ad-42b0-bef2-c22f3438d324 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e6dee6d0-03ad-42b0-bef2-c22f3438d324

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
# defoptions=quiet splash vga=795

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
##      altoptions=(single-user) single
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

[COLOR=Red]# (0)                                     <- Don't copy these
title         Arch Linux
rootnoverify (hd0,2)
kernel         /boot/vmlinuz26 root=/dev/sda3 ro logo.nologo quiet console=tty1 vga=794 splash=silent,theme:gentoo-blue,fadein,fadeout
initrd         /boot/kernel26.img

# (1)
title           Arch Linux Fallback
rootnoverify (hd0,2)
kernel          /boot/vmlinuz26 root=/dev/sda3 ro
initrd          /boot/kernel26-fallback.img

# (2)
title           Arch Linux (root terminal)
rootnoverify (hd0,2)
kernel          /boot/vmlinuz26 root=/dev/sda3 ro 1
initrd          /boot/kernel26-fallback.img

# (3)
title         Windows Vista Ultimate piece of ****
rootnoverify (hd0,3)
savedefault
makeactive
chainloader  +1

# (4)
title         Xubuntu 9.04, kernel 2.6.28-14-generic
rootnoverify (hd0,5)
kernel         /vmlinuz root=/dev/sda6 ro splash vga=794
initrd         /initrd.img
quiet

# (5)
title         Xubuntu 9.04, kernel 2.6.28-14-generic (recovery)
rootnoverify (hd0,5)
kernel         /vmlinuz root=/dev/sda6 ro single
initrd         /initrd.img
quiet[/COLOR][COLOR=Red]                                     <- Don't copy these[/COLOR]

### END DEBIAN AUTOMAGIC KERNELS LIST
```You could even have: 
```
default        0

timeout        10

# Pretty colours

color white/black yellow/red

# Gfxboot

#List

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
# kopt=root=UUID=e6dee6d0-03ad-42b0-bef2-c22f3438d324 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e6dee6d0-03ad-42b0-bef2-c22f3438d324

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
# defoptions=quiet splash vga=795

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
##      altoptions=(single-user) single
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

[COLOR=Red]# (0)                                     <- Don't copy these either[/COLOR]
**gfxmenu /boot/grub/messages/message-8**
[COLOR=Red]title         Arch Linux
rootnoverify (hd0,2)
kernel         /boot/vmlinuz26 root=/dev/sda3 ro logo.nologo quiet console=tty1 vga=794 splash=silent,theme:gentoo-blue,fadein,fadeout
initrd         /boot/kernel26.img

# (1)
title           Arch Linux Fallback
rootnoverify (hd0,2)
kernel          /boot/vmlinuz26 root=/dev/sda3 ro
initrd          /boot/kernel26-fallback.img

# (2)
title           Arch Linux (root terminal)
rootnoverify (hd0,2)
kernel          /boot/vmlinuz26 root=/dev/sda3 ro 1
initrd          /boot/kernel26-fallback.img

# (3)
title         Windows Vista Ultimate piece of ****
rootnoverify (hd0,3)
savedefault
makeactive
chainloader  +1

# (4)
title         Xubuntu 9.04, kernel 2.6.28-14-generic
rootnoverify (hd0,5)
kernel         /vmlinuz root=/dev/sda6 ro splash vga=794
initrd         /initrd.img
quiet

# (5)
title         Xubuntu 9.04, kernel 2.6.28-14-generic (recovery)
rootnoverify (hd0,5)
kernel         /vmlinuz root=/dev/sda6 ro single
initrd         /initrd.img
quiet[/COLOR][COLOR=Red]                                     <- Don't copy these[/COLOR] either

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by 600WPMPO on 2009-08-22
Ok, i finally installed the suse theme as described above..!!

However, i am unable to use any other theme i have downloaded e.g. ububrown, ubugray, ubured etc.

When i boot, the message says "invalid file format"

When i replace the file like message.new with the original message.suse, it again works fine.

Help please...

--------------------------------------

EDIT: No replies, so I found out by myself (courtsey msch @ [http://ubuntuforums.org/showthread.php?t=208855&page=41](http://ubuntuforums.org/showthread.php?t=208855&page=41))

> A lot of the themes on gnomelook.org are old format so will have config files missing or bad install files. The message file format has changed. The older formats work with versions upto 0.97-11 you probably will need to re-compile themes if you are running the latest 0.97-40 grub-gfxboot.

This can be done for the themes in synaptic as follows:
Extract the theme to &#8220;/usr/share/gfxboot-theme-xxxx&#8221; then:

Code:
cd /usr/share/gfxboot-theme-xxxx/
sudo make
sudo make install
cd install
sudo -s
ls . |cpio -o > /boot/grub/message.xxxx #### theme file name

-------------------------------------

EDIT: However, even this doesn't work.

Tried the themes gfxboot-theme-blueAqua-ubuntu & gfxboot-theme-ubuntumsk-1280x1024 with the above method, but get the same error at boot : invalid file format

Is anybody here who can help me...??

---

### Post by Intrepid Ibex on 2009-09-04
[http://ubuntuforums.org/showpost.php?p=7325554&postcount=733](http://ubuntuforums.org/showpost.php?p=7325554&postcount=733)

Read before posting :).

Also this howto is probably better: [http://ubuntuforums.org/showthread.php?t=481957&highlight=gfxboot](http://ubuntuforums.org/showthread.php?t=481957&highlight=gfxboot)

---

### Post by BobtheBlueBerry on 2009-09-19
There is also a amd64 deb for 64-bit machines in the repository link in the topic post.

---

