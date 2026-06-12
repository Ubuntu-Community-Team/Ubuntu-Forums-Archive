---
title: "Dual boot(Windowsxp+Ubuntu) make...."
date: 2008-09-11
forum: General Help
---

### Post by ManyBeers on 2008-09-11
.....Windows the default boot . How do I do this editing Grub's /menu/list.
I just Installed Ubuntu last night and now am happily dual-booting. However 
after putting my Windows system into hibernation last night which I always
do......  on system wake-up this morning (which occurs via a Scheduled-Task) 
I wqs greeted with Ubuntu's log-in screen. I no why this happened-When the harddrive spun up it loaded Grub and since I wasn't there to select which operating
sysrem to boot it loaded Grub's default entry...Ubuntu. No good, I need Windows
as my default entry. How?

---

### Post by cdtech on 2008-09-11
Find the line within your "/boot/grub/menu.lst" file that looks like this:
```
**default		0**
```
and change it to the device order of the system you want as your default OS.

---

### Post by Sycron on 2008-09-11
Post the output of the following command.```
cat /boot/grub/menu.lst
```

---

### Post by Idefix82 on 2008-09-11
Either type
```
sudo grub-set-default ?
```
where  ? is the number of the entry in the boot list that you want to be the default (eg. 0 for the top entry, 1 for next one and so on)
or type
```
cd /boot/grub
sudo gedit menu.lst
```

and change the line "default  0" accordingly.

---

### Post by ManyBeers on 2008-09-11
> **Idefix82 said:**
> Either type
```
sudo grub-set-default ?
```
where  ? is the number of the entry in the boot list that you want to be the default (eg. 0 for the top entry, 1 for next one and so on)
or type
```
cd /boot/grub
sudo gedit menu.lst
```

and change the line "default  0" accordingly.

I'm a beginner with Ubuntu here so I will need explicit guidance. I an currently 
in Windows but I will reboot into Ubuntu and return to this forum in 5 minutes.
I will be logged into Ubuntu in my regular user acct. Please bear with me as getting this right is very important as I am sure you know.

---

### Post by pastalavista on 2008-09-11
if you want an easy graphical way to do it, install QGrubEditor
```
sudo apt-get install qgrubeditor
```

---

### Post by Idefix82 on 2008-09-11
OK, here is a more detailed explanation:
Go to the menu in the top left corner, Applications->Accessoires->Terminal
now type in
```

cd /boot/grub
sudo gedit menu.lst

```
and provide your login password.
You can now view and change the configuration file for grub.
Find the line which says
```

default   0

```
(line 14 for me) and replace 0 by the number of the Windows entry. If you don't remember the number, you can actually count the entries in the file you are currently viewing. They will all be at the bottom of the file after all the comments (lines starting with #).

---

### Post by ManyBeers on 2008-09-11
> **pastalavista said:**
> if you want an easy graphical way to do it, install QGrubEditor
```
sudo apt-get install qgrubeditor
```

I'm not ready to install anything yet. I am now in Ubuntu and if one of you can hold my hand on this I am ready to follow instructios.

---

### Post by ManyBeers on 2008-09-11
> **Idefix82 said:**
> OK, here is a more detailed explanation:
Go to the menu in the top left corner, Applications->Accessoires->Terminal
now type in
```

cd /boot/grub
sudo gedit menu.lst

```
and provide your login password.
You can now view and change the configuration file for grub.
Find the line which says
```

default   0

```
(line 14 for me) and replace 0 by the number of the Windows entry. If you don't remember the number, you can actually count the entries in the file you are currently viewing. They will all be at the bottom of the file after all the comments (lines starting with #).

Ok here in my list:# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=5e3c91a1-6ddc-4e8b-8eb7-766e7e18aaf0 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5e3c91a1-6ddc-4e8b-8eb7-766e7e18aaf0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5e3c91a1-6ddc-4e8b-8eb7-766e7e18aaf0 ro single
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
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1
 Would you show me how? What number should I change default too.

---

### Post by pastalavista on 2008-09-11
post the contents of /boot/grub/menu.lst

edit:ok.. I see you have

now in the terminal, type
```
sudo gedit /boot/grub/menu.lst
```
then, in Gedit, change the line (the first uncommented '#' line) that says 'default 0' to 'default 3'
save the changes and reboot

(the first 'title' is number 0... Windows is the fourth so it will be 3)

re-edit: oops, I keep forgetting the line "Other Operating Systems" is a 'title' too so Windows will be 4... not 3

and, you're "ready to install" whenever you have internet access.. it's easier than pie... it's a piece of cake haha
the apt-get will do all the work

---

### Post by ManyBeers on 2008-09-11
> **pastalavista said:**
> post the contents of /boot/grub/menu.lst

I have.

---

### Post by Idefix82 on 2008-09-11
You can see after the second block of lines starting with # is the line default 0. Replace 0 by 3 and save.
I hope somebody will correct me, if the divider is also counted as an entry so that it should be 4 and not 3, but I am pretty sure this isn't the case.
You can just try 3 and reboot, but stay in front of the computer and see which line is selected in grub.

---

### Post by ManyBeers on 2008-09-11
> **Idefix82 said:**
> You can see after the second block of lines starting with # is the line default 0. Replace 0 by 3 and save.
I hope somebody will correct me, if the divider is also counted as an entry so that it should be 4 and not 3, but I am pretty sure this isn't the case.
You can just try 3 and reboot, but stay in front of the computer and see which line is selected in grub.

I am going with #3. Hope you guys right.

---

### Post by ManyBeers on 2008-09-11
> **ManyBeers said:**
> I am going with #3. Hope you guys right.

Well I made it a 3 and when I rebooted the "Other Operating Systems" was highlighted so I am assuming that line counts and I need to change 3 to a 4 is that correct?

---

### Post by Idefix82 on 2008-09-11
Yes, so it's 4 then, sorry. There was no risk involved though since you don't actually let grub execute the default option.
By the way, as you could see in the file, you can also set the amount of time it waits for before booting the default option. All you have to do is to change the line "timeout 10" to something that suits you.

---

### Post by ManyBeers on 2008-09-11
> **Idefix82 said:**
> Yes, so it's 4 then, sorry. There was no risk involved though since you don't actually let grub execute the default option.
By the way, as you could see in the file, you can also set the amount of time it waits for before booting the default option. All you have to do is to change the line "timeout 10" to something that suits you.

Yeah I quickly selected Ubuntu. Yeah I will leave the time where it is for now. Thanks a lot for your help.

---

