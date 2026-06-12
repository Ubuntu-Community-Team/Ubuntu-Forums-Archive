---
title: "dual boot question"
date: 2009-05-08
forum: Hardware
---

### Post by biosnake on 2009-05-08
so i just installed ubuntu on my pc and now when i turn on my pc it wont show my dual boot menu so i can select windows 7 

what do i do

---

### Post by Trigsu on 2009-05-08
Umm.. but if you installed Ubuntu from Live-CD/DVD, wouldn't GRUB show you the Windows option?

Or did you install Ubuntu with wubi from Windows?

---

### Post by biosnake on 2009-05-08
i installed ubuntu with the dvd

---

### Post by Trigsu on 2009-05-08
And it detected Windows on C: while installing? If I remember right, it did for me..

---

### Post by biosnake on 2009-05-08
yea i installed it on a new partition but it wont show me the windows partition when i boot up

---

### Post by DJYoshaBYD on 2009-05-08
go into ubuntu, and then go to a terminal

type or paste the following..

```

sudo gedit /boot/grub/menu.lst

```

that will bring up the boot menu config tool file thing.. lol

edit down where it says timeout, and set the seconds longer..

really, when your pc is booting, it should say something like "press escape to enter grub menu"... that is where you choose your OS to boot with..

be careful editing the menu.lst file

---

### Post by logos34 on 2009-05-08
run this in a terminal

sudo fdisk -l

and post the output.

then manually add windows boot entry to grub menu

---

### Post by biosnake on 2009-05-08
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
dood@dood-laptop:~$

---

### Post by logos34 on 2009-05-08
it's sudo fdisk **-l** (letter l)

just copy and paste

I misread your initial post..check your menu.lst like DYoshaBYd--if the menu isn't appearing at all it's likely set for "hiddenmenu"

---

### Post by DJYoshaBYD on 2009-05-08
I know that.. but it should still tell him to press escape to go into it...

---

### Post by Trigsu on 2009-05-08
Mine went always to GRUB without esc, after installing Ubuntu (on 2nd hard drive while Windows was on 1st).

---

### Post by DJYoshaBYD on 2009-05-08
yes.. it should be like that by default.. but you never know if something got changed.. lol

---

### Post by biosnake on 2009-05-08
what do i do after i type in sudo fdisk [B]-l and see what it says
[/B]

---

### Post by logos34 on 2009-05-08
yeah, ubuntu has a mind of it's own. That's what makes it so exciting--you never know what's going to go wrong next!

---

### Post by biosnake on 2009-05-08
when i press escape to go into the dual boot thing it doesnt show windows in there.

 i want to know how to manually add the option to boot windows in

---

### Post by Trigsu on 2009-05-08
You know..I'm getting withdrawal symptoms from Ubuntu, because my 2nd hard drive is getting replaced by the warranty...
Waiting it urgently so I can install 9.04 and get some problems of my own :D

---

### Post by logos34 on 2009-05-08
> **biosnake said:**
> what do i do after i type in sudo fdisk [B]-l and see what it says
[/B]

copy and post it

but your really need to post menu.lst

---

### Post by biosnake on 2009-05-08
> **logos34 said:**
> copy and post it

but your really need to post menu.lst


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2481    19928601    5  Extended
/dev/sda2            4204        7296    24839164    7  HPFS/NTFS
/dev/sda5               1        2481    19928569+  83  Linux

---

### Post by logos34 on 2009-05-08
if no windows boot entry at bottom of /boot/grub/menu.lst, you'll need to add something like this:

for windows on sda2:

> title Windows 7
root (hd0,1)
makeactive
savedefault
chainloader +1

---

### Post by biosnake on 2009-05-08
that didnt work

---

### Post by DJYoshaBYD on 2009-05-08
post your menu.lst so we can see what it looks like

/boot/grub/menu.lst

---

### Post by biosnake on 2009-05-08
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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
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
# kopt=root=UUID=3983557b-e413-4f9c-869b-e20d3ca6cbcd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3983557b-e413-4f9c-869b-e20d3ca6cbcd

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
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3983557b-e413-4f9c-869b-e20d3ca6cbcd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3983557b-e413-4f9c-869b-e20d3ca6cbcd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by DJYoshaBYD on 2009-05-08
where is the code that the last guy told you to past? if you didnt put the code in as instructed, it wont work.. but it right above
where is says

### END DEBAIN AUTOMAGIC KERNELS LIST

follow the last post again, and lets see if we can get this shi+ to flush down.. lol

---

### Post by DJYoshaBYD on 2009-05-08
oh yeah.... and to be able to edit the menu.lst file, do the following to open the file, instead of just opening it

```

sudo gedit /boot/grub/menu.lst

```

---

### Post by DJYoshaBYD on 2009-05-08
Copy and paste this into you file, replacing everything in your menu.lst file.. i added the appropriate code for you.. :)

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
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
# kopt=root=UUID=3983557b-e413-4f9c-869b-e20d3ca6cbcd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3983557b-e413-4f9c-869b-e20d3ca6cbcd

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
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3983557b-e413-4f9c-869b-e20d3ca6cbcd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3983557b-e413-4f9c-869b-e20d3ca6cbcd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/memtest86+.bin
quiet

title Windows 7
root (hd0,1)
makeactive
savedefault
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by logos34 on 2009-05-08
> **DJYoshaBYD said:**
> 
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3983557b-e413-4f9c-869b-e20d3ca6cbcd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3983557b-e413-4f9c-869b-e20d3ca6cbcd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3983557b-e413-4f9c-869b-e20d3ca6cbcd
kernel        /boot/memtest86+.bin
quiet
[COLOR="Red"]
title Windows 7
root (hd0,1)
makeactive
savedefault
chainloader +1 [/COLOR]

### END DEBIAN AUTOMAGIC KERNELS LIST


Technically, that will work...The only problem is that update-grub will remove any foreign OS entries inside the 'automagic' section at the next kernel upgrade.  So either put it just above or below (but outside) the automagic section.

> What NOT to do-  don't paste your Windows entry anywhere inside the automagic kernels list because it will be deleted when you have a kernel update in Ubuntu.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by DJYoshaBYD on 2009-05-08
AHHH.. thats why that happens.. lol... excellent... you learn something new every day.. thanks.. now if I can just get someone to chime in on my post about my suspend on my laptop, id be happy..

---

### Post by logos34 on 2009-05-08
don't even mention suspend issues...I had trouble with that and hibernation for as long as I can remember...One or the other never worked properly, no matter what tweaks I tried...Luckily, Hardy has fixed that for me...I have no idea what happened!

---

### Post by DJYoshaBYD on 2009-05-08
hardy didnt work for me.. intrepid did, untill it updated, then it broke it.. lol.. and i have NO idea which one did it.. lol.. pretty screwed up..

---

