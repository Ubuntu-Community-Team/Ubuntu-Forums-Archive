---
title: "HOWTO: FIX touchpad issues on karmic upgrade"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by balak on 2009-10-31
I am just starting this thread to let y'all know of the fix I used. 

**Problem: touchpad working fine in jaunty, not working at all after karmic upgrade.** My laptop is a sony vaio, but the problem could be in all laptops.

**Symptoms:** 
1. Check what kernel you are booting into
```
$uname -a: 
Linux xxxx 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```
If this is not your output, then you are using an older version (most probably from jaunty). You'll need to change the kernel you are booting into. This can be done by editing the default value in /boot/grub/menu.lst file.
2. Search your 'dmesg' output for this:
```
$dmesg | grep mouse
[ 13.603905] psmouse: Unknown parameter `synaptics_resume_reset'
```
3. Check if the 'psmouse' module is loaded at all:
```
$lsmod | grep psmouse

```
If there is no output of the above command, that means the touchpad module (psmouse) is not loaded.
4. Look if there is a file called /etc/modprobe.d/psmouse.conf
If this line exists in the file, you have the same problem as me.
```
options psmouse synaptics_resume_reset=N

```

**Solution:**
1. Comment out the line in (step 3) /etc/modprobe.d/psmouse.conf, i.e. add "#" at the start of the line.
2. Reboot. 

The 'psmouse' module should be loaded successfully, and you should see a 'touchpad' tab in System->Preferences->Mouse

Please let me know if this fixes your problems. I'll try to help as much as I can.

---

### Post by samasat on 2009-11-01
Thanks Balak.

I got output for :
dmes | grep psmouse          and          
lsmod | grep psmouse

However, there is no psmouse.conf file in /etc/modprobe.d/ to modify.

---

### Post by MiloszK on 2009-11-01
> **samasat said:**
> Thanks Balak.

I got output for :
dmes | grep psmouse          and          
lsmod | grep psmouse

However, there is no psmouse.conf file in /etc/modprobe.d/ to modify.

Second.

```
milosz@milosz-laptop:~$ dmesg | grep psmouse
milosz@milosz-laptop:~$ dmesg | grep mouse
[    2.111311] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    4.456053] mice: PS/2 mouse device common for all mice
milosz@milosz-laptop:~$ dmesg | grep synaptics
[   16.497483] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
milosz@milosz-laptop:~$ lsmod | grep psmouse
psmouse                64028  0 
```Not sure what to do here. _[This guy]("http://ubuntuforums.org/showthread.php?t=1306012")_ solved the problem by reverting to the previous kernel. I don't want to do that, but that solution identifies modules as a culprit. I'm using a USB mouse for now (works fine).

---

### Post by MiloszK on 2009-11-01
Edit: the other thread has a proper solution. I misread the kernel version numbers. He was not reverting, but rather updating the configuration file.

---

### Post by balak on 2009-11-01
Yeah, it looks like the 'default' kernel version was the older kernel in /boot/grub/menu.lst. Changing it to new kernels has helped some people; thanks for letting me know about this. I have updated the first post with this information.

> **MiloszK said:**
> Edit: the other thread has a proper solution. I misread the kernel version numbers. He was not reverting, but rather updating the configuration file.

---

### Post by samasat on 2009-11-02
Thanks Balak !!

After following the instruction 1 in your edited post I got it straight ... 

just for information...some detailed info about it for other NewB's like me looking for help :
1) cd /boot/grub/menu.lst                 (change directory)

2) sudo cp menu.lst  ~/menu_bkup.lst    (create bkup)

3) sudo vim menu.lst         (it will open file for edit ... i) goto to the last portion of it using arrow key or mouse ...you will find all OS listed there if you have dual boot set .... ii) each block of about 4 lines for each boot option. Copy -paste the previous kernel lines block and change all kernel number (e.g. 2.6.28.11) to 2.6.31-14.   iii) save file by Esc >> press ":wq" >> ENTER

4) reboot by typing Cmd  sudo reboot

5) Select newly added boot option.

NOTE : This worked for me. I have UPGRADED from Ubuntu 9.04 to 9.10 and all upgrade (download , install) process was successful in one go.

---

### Post by bjaz on 2009-11-08
thanks for all this

in my install, there is also no

no psmouse.conf file in /etc/modprobe.d/ to modify.

and when doing this 

$lsmod | grep psmouse
I get no output. Does this mean I need to load it, and how do I do this ?

thanks in advance

ben

---

### Post by balak on 2009-11-10
> **bjaz said:**
> thanks for all this

in my install, there is also no

no psmouse.conf file in /etc/modprobe.d/ to modify.

and when doing this 

$lsmod | grep psmouse
I get no output. Does this mean I need to load it, and how do I do this ?

thanks in advance

ben

Can you report what kernel you are using ? (see the first post for 'uname -a').

---

### Post by bjaz on 2009-11-11
> **balak said:**
> Can you report what kernel you are using ? (see the first post for 'uname -a').


yes sorry 

Linux kayogoro 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux


it's apparently the old kernel.
i've also tried to modify it using thunar to have root access to the menu.lst, but it seems to stay the same.

thanks

b

the is what my current menu.lst looks like in the grub folder


-------------------------------------------------------

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
# kopt=root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professionnel
rootnoverify    (hd0,1)
savedefault
makeactive
chainload

---

### Post by balak on 2009-11-11
Is this after you modified the /boot/grub/menu.lst file ?
The first and third entries look the same and the 2nd & 4th entry look the same. I would think the 3rd & 4th entry would have the old kernel (2.6.28-16).

Anyways after this modification, you should boot into the new kernel if you reboot.

Bala

> **bjaz said:**
> 
title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=579a4449-4de6-4ccb-a7a0-0b9c2090c7a3 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        579a4449-4de6-4ccb-a7a0-0b9c2090c7a3
kernel        /boot/memtest86+.bin
quiet


---

### Post by raboofje on 2009-11-19
Instead of editing menu.lst by hand, shouldn't running 'update-grub' as root fix it automatically?

---

### Post by cutout33 on 2009-12-18
Hi, 
I have a fresh install and :
```
uname -a
Linux fadi-laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
```

```
dmesg | grep mouse
[    0.904667] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.962579] mice: PS/2 mouse device common for all mice
[   12.831634] psmouse: Unknown parameter `elantech'
[   12.850815] psmouse: Unknown parameter `elantech'
[   12.866655] psmouse: Unknown parameter `elantech'
[   12.882194] psmouse: Unknown parameter `elantech'

```

```
lsmod | grep psmouse ==> gives no output
```

and the file does not exist!

can anyone help me please my laptop is a fujitsu siemens and it is a clean install, no windows just ubuntu!

---

### Post by nmvictor on 2010-12-07
Their is a package, synaptic-dkms which i found [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191"). Install the package and you are good to go. The provided link is quite a long discussion but don't give up looking through till you get a link to synaptic-dksm Debian package. The package depend on dkms, dynamic kernel module service i guess. You might wanna install that first!

---

