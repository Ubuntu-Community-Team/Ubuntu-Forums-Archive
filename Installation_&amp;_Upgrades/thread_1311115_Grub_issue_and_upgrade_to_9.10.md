---
title: "Grub issue and upgrade to 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Rambar on 2009-11-02
Hello! I am currently a 9.04 user and I've been experiencing a weird problem with Grub. When I start my computer, grub loads and on the list, Ubuntu appears 3 times (I mean, 3 normal ubuntus, 3 recovery/memtests). I want to format my current ubuntu partition and then install Karmic in it (without touching my little windows partition), although Im very unsecure about how should I do it. Does someone mind pointing me the correct way? maybe a link to a detailed tutorial explaining all functions of the liveCD formating tools?


Thanks a lot, and sorry if this exact same thing has been asked many times before.

---

### Post by whoop on 2009-11-02
> **Rambar said:**
> Hello! I am currently a 9.04 user and I've been experiencing a weird problem with Grub. When I start my computer, grub loads and on the list, Ubuntu appears 3 times (I mean, 3 normal ubuntus, 3 recovery/memtests). I want to format my current ubuntu partition and then install Karmic in it (without touching my little windows partition), although Im very unsecure about how should I do it. Does someone mind pointing me the correct way? maybe a link to a detailed tutorial explaining all functions of the liveCD formating tools?


Thanks a lot, and sorry if this exact same thing has been asked many times before.

Why don't you just upgrade 9.04 to 9.10? Do you really want to do a fresh install every six months? I am under the impression that a lot of new people (coming from the windows world) are doing fresh installs all the time, maybe because that is the way for Windows. Upgrading is easier (just push a button and wait), and if you run into problems it's educational (you learn stuff). 

It is not out of the ordinary that ubuntu appears more than one time in grub... It does not mean you have more ubuntu OS's installed, it means, in your case, you have currently 3 kernels installed in your ubuntu setup. In my opinion you should at least have 2 (you are hurting no one, execpt a little disk space, with three. The kernels in your grub all have different versions if you look closely. If your list is getting too big you can remove some kernels with computer-janitor for instance. But I would always keep a couple installed.
The reason people have more than one kernel installed is because a new kernel could technically not work on your machine.. Then it's nice to know you can still boot from an older kernel and see if you can fix the problem...
You get more kernels automatically via updating your system, when new kernels are made available...

---

### Post by Rambar on 2009-11-02
Actually, the 3 versions are the same, and they dont appear in Computer Janitor. Thanks for the help, I was fearing I had severely messed up when I installed 9.04 for the first time.

---

### Post by whoop on 2009-11-02
> **Rambar said:**
> Actually, the 3 versions are the same, and they dont appear in Computer Janitor. Thanks for the help, I was fearing I had severely messed up when I installed 9.04 for the first time.

Ok, then it could be something else...
Could you post the output of:
```

sudo blkid

```

and while your at it give me the contents of menu.lst via:
```

gksudo gedit /boot/grub/menu.lst

```

Then we can get a better idea about the problem. Fixing it is always better, and more educational if you ask me.

---

### Post by Rambar on 2009-11-02
```
santiago@Samorost:~$ sudo blkid
[sudo] password for santiago: 
/dev/sda1: LABEL="RECOVERY" UUID="9417-721B" TYPE="vfat" 
/dev/sda2: UUID="921C1A841C1A638F" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda6: UUID="d2cb334b-d199-43bd-8f5a-06096db71470" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="d0e1380c-8e9d-4409-9ea5-cfaafe017246" 
/dev/sdb1: LABEL="e" UUID="E0DF-96D8" TYPE="vfat" 
santiago@Samorost:~$ 


```
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
# kopt=root=UUID=d2cb334b-d199-43bd-8f5a-06096db71470 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d2cb334b-d199-43bd-8f5a-06096db71470

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

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        d2cb334b-d199-43bd-8f5a-06096db71470
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=d2cb334b-d199-43bd-8f5a-06096db71470 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        d2cb334b-d199-43bd-8f5a-06096db71470
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=d2cb334b-d199-43bd-8f5a-06096db71470 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        d2cb334b-d199-43bd-8f5a-06096db71470
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=d2cb334b-d199-43bd-8f5a-06096db71470 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        d2cb334b-d199-43bd-8f5a-06096db71470
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=d2cb334b-d199-43bd-8f5a-06096db71470 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d2cb334b-d199-43bd-8f5a-06096db71470
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d2cb334b-d199-43bd-8f5a-06096db71470 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d2cb334b-d199-43bd-8f5a-06096db71470
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d2cb334b-d199-43bd-8f5a-06096db71470 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d2cb334b-d199-43bd-8f5a-06096db71470
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

Again, thanks :)

---

### Post by whoop on 2009-11-02
Well I could be wrong but it looks like blkid states you have just one ubuntu install:
This partition contains ubuntu:
/dev/sda6: UUID="d2cb334b-d199-43bd-8f5a-06096db71470" TYPE="ext3" 
This is used for ubuntu swap:
/dev/sda7: TYPE="swap" UUID="d0e1380c-8e9d-4409-9ea5-cfaafe017246" 

This appears the be some recovery partition (maybe from hardware vendor)
/dev/sda1: LABEL="RECOVERY" UUID="9417-721B" TYPE="vfat" 
I don't know what this is (could be a windows partition you made yourself, or some recovery related partition):
/dev/sdb1: LABEL="e" UUID="E0DF-96D8" TYPE="vfat" 
This partition contains windows vista (probably)
/dev/sda2: UUID="921C1A841C1A638F" LABEL="VistaOS" TYPE="ntfs" 

When I look at menu.lst is see three (different) kernels:
Ubuntu 9.04, kernel 2.6.28-16-generic
Ubuntu 9.04, kernel 2.6.28-15-generic
Ubuntu 9.04, kernel 2.6.28-11-generic

The difference here is: -16, -15, -11. So in contrary what you said, the information here leads me to believe they are different. 
It is strange that you don't see them in computer janitor but it could be that the janitor in jaunty doesn't remove kernels (I don't remember).
You could check in synaptic, search for linux-image. To make sure they are indeed installed.

So if I where you I would just make sure what I say is correct (via checking synaptic, looking at the drive with gparted etc.), and then rest assured your system is fine.

Than back-up your precious data (like you always should), and upgrade to 9.10.
As a side note, there's nothing wrong with sticking around with an older version of ubuntu (as long as it's supported). Whenever I install ubuntu for someone, I always give them an LTS, so that they don't have to upgrade every six months.

If you want a machine that just works I would recommend LTS's all the way.

---

### Post by Rambar on 2009-11-02
I am really impressed! Thanks Whoop. I hope havent caused much trouble. I still have a lot to read on Linux, and probably the best thing for me to do now is to get a paperback book instead of the pdfs im using.

Thanks again :), it was very useful.

---

