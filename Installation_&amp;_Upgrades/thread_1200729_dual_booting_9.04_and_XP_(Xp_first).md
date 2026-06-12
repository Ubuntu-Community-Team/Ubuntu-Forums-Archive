---
title: "dual booting 9.04 and XP (Xp first)"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by madzach200 on 2009-06-30
what steps should i take to insure an easy harmless install of Ubuntu and the Grub loader?
i have a 40gig pata(Xp system drive) and a 160gig SATA (the HD that i want Ubuntu on) i use the 160gig for games and media ,if i try to partition 10gigs will i loose the stuff i have on it (note: the stuff i have on it only takes up 17.7gigs)
i dual booted ubuntu a long time ago but i can remeber exactly what i did.
i have upgraded to a ATI Video card (AGP 8X) since then.
i am new to this forum and hope to have this figured out.

Thanks A lot:p

Zach

---

### Post by raymondh on 2009-06-30
This thread may give you clues/hints/tips.

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

His (OP) links are of value .... albeit old.

If this thread does not suit your needs nor preferences, post back and the forum can make a plan of action depending on your comfort level and requirements.

Back up first.

Good luck.

---

### Post by Bucky Ball on 2009-06-30
This might be handy too:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by madzach200 on 2009-07-01
ok i have read through most of them.
the way i see it i need to backup everything on the sata.
unplug the pata and boot from the livecd.
then install Ubuntu normally.
giving it 25gb.
after i install Ubuntu let it run all the updates.
then restart and do this.


n Ubuntu go to Applications/System Tools/Terminal. open a text editor and change the grub menu file:
$cd /boot/grub
$sudo gedit menu.lst
 look for an entry (near the end) that reads like something like this:

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
chainloader +1

and change it to this:

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
chainloader +1

7. save the file
8. reboot and test boot into XP
...............................................................

after i have done this xp will boot normally and i will be using mbr instead of GRUB.
everything will work.
am i wrong on anything did i forget about anything.

Zach:KS

---

### Post by madzach200 on 2009-07-02
sorry for double posting but do i have a go for takeoff
i really want Ubuntu but i want to know if i am doing the right thing

thank all of you for directing me to these wonderful links

regards,
  Zach

---

### Post by Bucky Ball on 2009-07-02
[http://ubuntuforums.org/archive/index.php/t-11359.html](http://ubuntuforums.org/archive/index.php/t-11359.html)

I think you may be looking at syntax:

```
map (hd1) (hd0)
```Not:

```
map (hd1,hd0)
```Why are you mapping the partition? If you install Windows first, then Ubuntu, no need. Grub will take care of itself. You should only need to map the partition if Windows is not on the first one, first drive, and sometimes IDE and SATA in the same machine require this fix also. Perhaps the latter is what you are getting at?

1/ Install Windows on the first, primary partition. Leave the rest of the drive empty.

2/ Install Ubuntu and choose 'Manual Partitioning' when you get to that section of the install. Partition the rest of the drive up there. The partitions:

```
/
/home
/swap
```... are the basics. The rest is up to you.


* BTW: I am not sure that 9.04 has a menu.lst file. I was helping someone the other day and apparently Grub2 is different to Grub and I have a feeling 9.04 uses that. Check your instructions were for 9.04, NOT 8.04. The other alternative is to install 8.04. It is a year older and therefore more stable at this point and does use Grub.

---

### Post by merlinus on 2009-07-02
If I am reading correctly, the OP already has windows installed on his pata 40G drive. Depending upon which boots first in bios, the map statements may be necessary, but IIRC it should be in this order, if ubuntu on the sata drive is first:

map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by madzach200 on 2009-07-05
sorry,
 it has been awhile since my last post.
i was speaking nonsense.
anyway I am writing this post from ubuntu 9.04
yes that's right i am dual booting xp and ubuntu.
the only thing that is wrong is after i run windows i have to boot into the ubuntu live cd and fix grub error 22 by doing [this]("http://ubuntuforums.org/showthread.php?t=224351").
for some reason ,after running windows it messes up my grub loader.
is there a simple solution to fixing this issue?
should i start a new thread with this question?


chears,
   Zach

---

### Post by presence1960 on 2009-07-05
booting into your windows partition should not mess up your GRUB. Did you do anything with your windows disk after installing Ubuntu?
Here is error 22 from the GRUB manual - 22 : > No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.  This means something is incorrect in menu.lst.

why don't you run these two commands in terminal and post the output here: > sudo fdisk -l that is a lowercase L and > gksu gedit /boot/grub/menu.lst that is also a lowercase L

---

### Post by madzach200 on 2009-07-05
i don't think i did anything to the windows disk
i pasted the commands into terminal here is what it spat out

[COLOR=Red]Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2b192b18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5169    39077608+  42  SFS

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x214d214d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5005    40202631    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa694d376

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          88      706828+  83  Linux
/dev/sdc2              89       19457   155581492+   5  Extended
/dev/sdc5              89        2670    20739883+  83  Linux
/dev/sdc6            2671       18799   129556161    7  HPFS/NTFS
/dev/sdc7           18800       19457     5285353+  82  Linux swap / Solaris
zach@zmachine:~$ 



[COLOR=Black]AND.........................................

[/COLOR]
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
# kopt=root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6f82e37b-2b9c-45fb-895a-936e9ebfd238

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
# xenhopt=[/COLOR]



a lot of info i am not sure what it means but hope it helps
sry for the red font ... i thought it might make it easier to tell what's what

BTW The Smilies are not soposed to be there
it replaced the ('s and the :'s with smiles
 
regards,
  Zach

---

### Post by presence1960 on 2009-07-05
Your Grub did not install correctly or you did not paste all the info from your menu.lst. take a look at mine and you will see you aremissing a lot of stuff, most notably your OS list. here is mine, compare the two:
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
timeout		5

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=301270a1-a123-4faf-b14f-508731178ff8

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
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=301270a1-a123-4faf-b14f-508731178ff8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		301270a1-a123-4faf-b14f-508731178ff8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title          Microsoft Windows 7 RC
rootnoverify   (hd1,1)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

title          Sabayon 4.1
rootnoverify   (hd0,4)
chainloader    +1
```

I see some other issues also. You said windows is on the 40 Gb disk, The file system for that in your sudo fdisk -l output is listed as SFS. if that is a windows partition I have never heard of that filesystem for windows. Something is definitely wrong there...unless

Or is windows on the sdb drive (41 GB)? Which partition on sdc is Ubuntu root (/) installed to?

Your description of your setup only vaguely resembles the actual setup. Please answer those questions.

---

### Post by madzach200 on 2009-07-05
ok for some reason t didnt copy the whole menu.1st
here you go
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
# kopt=root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6f82e37b-2b9c-45fb-895a-936e9ebfd238

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by Bucky Ball on 2009-07-06
> **madzach200 said:**
> 
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
**uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238**
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic


```

This is from mine:

```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
**root            (hd0,5)**
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=36bd7710-ca84-48c9-90$
initrd          /boot/initrd.img-2.6.24-19-generic

```It uses 'root' instead of 'uuid'. Shouldn't make any difference but that's not to say it won't!

Check the lines in bold. Notice mine has 'root' and the UUID reflected in the next line down at 'root' also. You can experiment by editing the grub menu at boot by pressing 'e' and changing it. If it works, change it permanently in your menu.lst 


If it doesn't the changes made editing the grub from the menu list do not remain each time you boot so try again. They are only permanent when you change them in menu.lst

Hope this gives some clue. :)

---

### Post by presence1960 on 2009-07-06
Ok you didn't answer my questions, so I am going to assume Windows is on sda1. If that is true you may have a problem. Look at your sudo fdisk -l output. Now look at sda1. Under system it doesn't say HPFS/NTFS which is a windows filesystem. Here is what it says:
Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2b192b18

Device Boot Start End Blocks Id [COLOR="Red"]System[/COLOR]
/dev/sda1 * 1 5169 39077608+ 42 [COLOR="Red"]SFS[/COLOR] 
Well I seriously doubt that is a valid windows filesystem. If that is your windows partition this is what the entry for windows in menu.lst should be:
```
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader    +1

```
If that does not work, make sure you have the correct HDD that windows is installed to. If it is correct I believe your windows is corrupted because of the SFS Filesystem which is not windows.

If windows is on the 41 GB hard drive then make windows entry this:
```
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
map             (hd1) (hd2)
map             (hd2) (hd1)
chainloader    +1
```

Also the GRUB in Jaunty uses UUID instead of root (hdx,y) for Linux installations.
P.S. I found out SFS is an encrypted filesystem for DOS/Windows. I would try changing the windows entry in menu.lst as suggested above. Hopefully you won't have a problem with the SFS filesystem. Your windows entries in menu.lst to date have been far off the mark. Change that and see what happens.

---

### Post by madzach200 on 2009-07-06
ok i did what you guys said now i get error 22:no such partition
i am going to undo all changes made
i had a hd with backup stuff on it plugged in when i sent the fdisk results and the menu.1st.
so here they are again with backup hd unpluged
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2b192b18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5169    39077608+  42  SFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa694d376

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          88      706828+  83  Linux
/dev/sdb2              89       19457   155581492+   5  Extended
/dev/sdb5              89        2670    20739883+  83  Linux
/dev/sdb6            2671       18799   129556161    7  HPFS/NTFS
/dev/sdb7           18800       19457     5285353+  82  Linux swap / Solaris
zach@zmachine:~$ 
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
# kopt=root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6f82e37b-2b9c-45fb-895a-936e9ebfd238

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6f82e37b-2b9c-45fb-895a-936e9ebfd238 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        6f82e37b-2b9c-45fb-895a-936e9ebfd238
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```the problem was still occuring after changes were made so i restored to default
thank you guys a lot for the help
hopefully i will resolve this issue with your help

regards,
  Zach

---

### Post by madzach200 on 2009-07-06
presence1960 after i did what you said i got this message
```
STARTING UP...
A DISK READ ERROR OCCURED
PRESS CTRL+ALT+DEL TO RESTART
```when i try to boot windows
i was really hopping it would fix it:(
sry for double post
anyway i am currently undoing the changes made to menu.1st.
what's next?
btw the error message that i posed in last post said error 22
... the error flashed really quick i think it might have said error 11

p.s. why is it such a nono to double post in forums?

cheers,
   Zach

---

### Post by presence1960 on 2009-07-06
```
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader    +1
```

that should be your windows entry in menu.lst. I know nothing about SFS encryption that you have on your Windows partition.

One other thing to check in your BIOS is the boot order of your hard disks. if the 40 GB boots first use the above for windows. If the disk with Linux boots first change your windows entry to this

```
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader    +1
```

sometimes BIOS and Ubuntu read the order of disks differently. BIOS always gives the correct booting order of hard disks.

P.S. you see the difference in your disks order with the unplugged drive- what was sdc is now sdb!

---

### Post by madzach200 on 2009-07-06
idk why it says that in the menu.1st but when i change it ,it gives me error messages
as stated above.
maybe it is because i have 9.04 and not the earlier version of ubuntu.
idk what  SFS is or where it came from.
i thought i already tried what you said but i will go ahead and try it again.


cheers,
  Zach

---

### Post by presence1960 on 2009-07-06
here is a link for the SFS filesystem(s) it is a long list. Here is my sudo fdisk -l output. Note my windows filesystem in red:

```
raz@sabayon-raz ~ $ sudo fdisk -l
Password: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25064   201326548+  83  Linux
/dev/sda2   *       25065       30401    42869452+   7  [COLOR="Red"]HPFS/NTFS[/COLOR]

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2863    22997016   83  Linux
/dev/sdb2            2864        3361     4000185   82  Linux swap / Solaris
/dev/sdb3            3362        5972    20972857+  83  Linux
/dev/sdb4            5973       19457   108318262+   5  Extended
/dev/sdb5            5973        8583    20972826   83  Linux

```

if you didn't install the SFS on your windows partition I would format that partition and reinstall Windows.

---

### Post by presence1960 on 2009-07-06
oops forgot the link: [http://www.google.com/search?q=sfs+filesystem&ie=utf-8&oe=utf-8&aq=t&rls=Sabayon:en-US:official&client=firefox-a](http://www.google.com/search?q=sfs+filesystem&ie=utf-8&oe=utf-8&aq=t&rls=Sabayon:en-US:official&client=firefox-a)

---

### Post by presence1960 on 2009-07-06
> **madzach200 said:**
> idk why it says that in the menu.1st but when i change it ,it gives me error messages
as stated above.
maybe it is because i have 9.04 and not the earlier version of ubuntu.
idk what  SFS is or where it came from.
i thought i already tried what you said but i will go ahead and try it again.


cheers,
  Zach

Zach, that is menu.lst where the character after the . is a lowercase L. Have you been editing menu.1st? (the # 1?) If that is the case then no changes have been made to your menu.lst file (with a lowercase L). it has nothing to do with what version you have, the file is called the same name in every version.

---

### Post by madzach200 on 2009-07-06
i have been copying and pasteing this into terminal
gksu gedit /boot/grub/menu.lst                      
i just figured that was a one
anyway i did what presence1960
said and changed the windows stuff in menu.lst
to
```
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader    +1
```
it wasn't a success it said starting up... and hangs there
i let it sit for 45 min nothing happened so i assume something is still wrong
i noticed that there is more things that you would like me to do so i will start that now.

cheers,
   Zach

---

### Post by madzach200 on 2009-07-06
i can get into windows to verify that i in fact do have a sfs file-system but i am almost positive that i have the standard NTFS file-system on my windows partition
i got this computer from a business under the table so i wouldn't be surprised if i had sfs.
i want to avoid formatting it as i don't have a xp cd.
do you need one?
remember i can still get to windows but after i restart i have to fix grub error 22 every-time i use windows.
i am going to probably triple post.
everyone's gunna hate me!
NOTE: i have dual booted xp and ubuntu before ,the only difference is i am putting ubuntu on a SATA HD instead of a PATA and i have an ati video card
but it worked great before
no problems what so ever.
so i figured the sata drive is what screwed it up.
     Cheers,
   Zach

---

### Post by presence1960 on 2009-07-06
> **madzach200 said:**
> i can get into windows to verify that i in fact do have a sfs file-system but i am almost positive that i have the standard NTFS file-system on my windows partition
i got this computer from a business under the table so i wouldn't be surprised if i had sfs.
i want to avoid formatting it as i don't have a xp cd.
do you need one?
remember i can still get to windows but after i restart i have to fix grub error 22 every-time i use windows.
i am going to probably triple post.
everyone's gunna hate me!
NOTE: i have dual booted xp and ubuntu before ,the only difference is i am putting ubuntu on a SATA HD instead of a PATA and i have an ati video card
but it worked great before
no problems what so ever.
so i figured the sata drive is what screwed it up.
     Cheers,
   Zach

I have a sata and an IDE (pata) drive and it doesn't mess my triple boot up. That is not the issue. your sudo fdisk -l shows a SFS file system for your windows partition-that I believe is the problem. To buy some time you can download & register a copy of Windows 7 RC. You will be able to use it until June 2010. That will give you time to get a legit version of windows. yes you will need a install disk to reinstall windows. Don't mess with a pirated version of Windows unless you like malware on your system.

I think the Win 7 RC is the best option right now for you because it will give you a legitimate version of windows that you can use until June, 2010. That gives you 11 months to get a legitimate version of windows.

here is the link to get it: [http://www.microsoft.com/windows/windows-7/download.aspx](http://www.microsoft.com/windows/windows-7/download.aspx)

---

### Post by madzach200 on 2009-07-06
nonono
my operating system is not pirated.
i got my whole computer broken from a business, fixed it, and windows was already installed on it
there is a good possibility that they put a secure file system on it.
my computer is completely legit.
i don't want to get win7 b/c i don't like getting betas
i had serious issues with xp sp3 all because i wasn't patient.
i don't plan on getting beta OS's any more
anyway so i for sure have an sfs file system?

---

### Post by presence1960 on 2009-07-06
I didn't mean your current version is pirated. what I meant is that if you can't get this version running, don't mess with pirated software. If you can't buy a legitimate version of windows right now that is why I recommended Win 7 RC.

Maybe you can find out from that business from which you bought the computer about the SFS filesystem. I seem to think that is the problem.

> anyway so i for sure have an sfs file system? that's what sudo fdisk -l output says you have. sudo fdisk -l is just about unfailingly accurate.

---

### Post by Bucky Ball on 2009-07-07
I would agree. SFS file system could be problematic. It seems to be designed for Amiga:

[http://en.wikipedia.org/wiki/Smart_File_System](http://en.wikipedia.org/wiki/Smart_File_System)

One thing; can't remember the size of that partition but the page above suggests SFS can't handle anything over 128Gb.

---

### Post by madzach200 on 2009-07-08
it will probably be a couple of days before i can contact the business unless i find another way.
the thing is, i have dual booted ubuntu and xp on this computer before and i never ran into this problem.
so why would i now?
that just doesn't make any since.
its not like i changed my file system.
could it be that ubuntu is not seeing the disk correctly.
is there anyway i could test this?
if i in fact do have sfs can i change it to ntfs without formating?
i found that you can change FAT32 to NTFS in [this]("http://ubuntuforums.org/archive/index.php/t-280670.html") archive
i wounder if there method can be used to my advantage.
i hope i can fix this without formatting


Cheers,
     Zach

---

### Post by Bucky Ball on 2009-07-08
What version of Ubuntu did you dual boot with in the past? If you haven't already, I would suggest attempting the 8.04 LTS alternate install ISO.

---

### Post by presence1960 on 2009-07-08
> **Bucky Ball said:**
> What version of Ubuntu did you dual boot with in the past? If you haven't already, I would suggest attempting the 8.04 LTS alternate install ISO.
At this point I would give that a shot since you said you have a couple days before you can contact the business to find out about the SFS filesystem. It is a long shot but after all this it can't hurt.

P.S. by dual boot in the past was it wubi or an actual full install of Ubuntu. As much as I hate to say it if all else fails since you can boot windows you can use wubi and make the second drive a total storage drive. You will be able to access it from within wubi and windows if you format it as NTFS (God forgive me for suggesting to format a whole drive as NTFS!). But it still bugs me that you can't get this squared away with a full installation.

---

### Post by pageone on 2009-07-08
I am not sure that the SFS is the problem here.  My computer seems to be acting exactly the same way.

See the following thread...
[http://ubuntuforums.org/showthread.php?t=1206199](http://ubuntuforums.org/showthread.php?t=1206199)

---

### Post by presence1960 on 2009-07-08
> **pageone said:**
> I am not sure that the SFS is the problem here.  My computer seems to be acting exactly the same way.

See the following thread...
[http://ubuntuforums.org/showthread.php?t=1206199](http://ubuntuforums.org/showthread.php?t=1206199)

yours probably is not the same. I looked at your thread and you can't boot windows. The OP here can boot windows but when he does he then can't boot from GRUB- he has to restore GRUB. Your setup is totally different also you have raid even though they are storage drives.

Check the boot order of your hard drives. Your sdc drive should be first first boot since it has Windows and Linux on it. But you also have sda marked as bootable, why? what is on it? Did you install GRUB to MBR of sda?

Let's get an exact look at your setup and boot info. Download to the desktop the Boot Info Script 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)

Once DL'd on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```. This will create a RESULTS.txt file on your desktop. Paste the entire contents of that file back at your original thread. After pasting highlight all text and click the # sign on the toolbar to place Code tags around the text. This will keep your text from taking up the whole page as in your previous post.

Then we'll get a good look at your setup & boot info.
**_Remember to post back to your thread, this is someone else's and it is difficult to give and receive accurate help if we have multiple topics going on._**

---

### Post by madzach200 on 2009-07-08
> **Bucky Ball said:**
> What version of Ubuntu did you dual boot with in the past? If you haven't already, I would suggest attempting the 8.04 LTS alternate install ISO.
i dual booted ubuntu 7.04 and xp sp2 now i am dual booting 9.04 with xp sp3.
i am going to get a hold of the guy that i got it from and ask him if his business uses sfs file system.hopefully he still remembers because he got laid off a couple months back.
he worked with networking or something so he might not know at all.

wish me luck!:KS
[B]Zach
[/B]

---

### Post by pageone on 2009-07-08
Results posted in my original thread.

Good luck, Zach!!

---

### Post by madzach200 on 2009-07-10
ok i haven't been able to talk to the person i got my computer from but
i just remembered that the 160 gig sata came out of a dvr box from a cable company
i just thought that if anyone wanted data secure it would probably be a company that didnt want to get suid for copyright infrengement.
idk if that info helps the cause but i thought i would put it out there.
btw i formatted it to ntfs when i got it, also there was a bunch of hidden partitions on it that was really hard to get around.
but i think i removed them all.
mabey there is a hidden 40 gig partition that xp cant see
that would make it a 200 gig hd.
ha that would be cool.
P.S. today i unplugged the 40 gig just to see what it would do.
it said that no os was found but the wierd thing is the ubuntu hd was plugged in
why didn't my computer know that and boot the grub loader?
anyways still wating on a reply from that company.

also i am using the live cd right now so dont be suprised if theres a bunch of gramatical errors.
no spell check.
gotta love spell check:p
hope its readable

cheers,
   Zach

---

### Post by raymondh on 2009-07-10
> **presence1960 said:**
> (God forgive me for suggesting to format a whole drive as NTFS!).

LOL.

I feel the same way (bugged) when "it can't get squared away with a full, straight-up install".

Good thread.

---

### Post by Shakeysteve on 2009-07-10
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

Apcmag.com has step by step instructions on how to dual boot Ubuntu, XP and Vista in all combinations. I have used this excellent site many times and has always worked.
This site should be the first "port of call" for anyone attempting a dual boot!

---

### Post by presence1960 on 2009-07-11
I am not trying to be a wiseguy, but maybe you should go back to post #1 and reread all 4 pages of this thread. Then try posting something relevant to the OP's issues.

---

### Post by madzach200 on 2009-07-11
> **presence1960 said:**
> I am not trying to be a wiseguy, but maybe you should go back to post #1 and reread all 4 pages of this thread. Then try posting something relevant to the OP's issues.
LOL:popcorn:

---

### Post by Bucky Ball on 2009-07-12
> **presence1960 said:**
> I am not trying to be a wiseguy, but maybe you should go back to post #1 and reread all 4 pages of this thread. Then try posting something relevant to the OP's issues.

+1. It really pays to read a thread rather than scan it. Plopping random, unrelated posts in the mix only confuses the issue. Sorry.

Think about what you are going to post and consider whether it is actually helping or just mixing up the water.

---

### Post by madzach200 on 2009-07-22
ok so it has takin long enough but i finally got a hold of the guy
he said he did networking and never knew anything about sfs
and that the company went bankrupt shortly after he was laid off
so i am still pretty stuck
is there anyway i can use mbr instead of grub?
whats the difference?

---

