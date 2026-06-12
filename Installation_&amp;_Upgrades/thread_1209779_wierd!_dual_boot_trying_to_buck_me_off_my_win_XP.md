---
title: "wierd! dual boot trying to buck me off my win XP"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by justjuss on 2009-07-10
&#65279;[COLOR=#204a87][SIZE=2](01:42:23 PM) [/SIZE]**[SIZE=3]jussy:[/SIZE]**[/COLOR][SIZE=3] Hi, I just installed ubuntu8.04 on a partition next to my Win XPPro OS. How do I uninstall? My trouble is that When the 1st screen comes up and gives me the choice of which syst I want to load I cannot choose XP. It's there but it keeps switching my curser back to Ubuntu. I've never had this happen in all my dual boot installs.
justjuss
[/SIZE]

---

### Post by philcamlin on 2009-07-10
are you using wubi or partitioned?

---

### Post by lindsay7 on 2009-07-10
type these commands in the terminal and post the results here

sudo cat /etc/fstab

sudo cat /boot/grub/menu.lst

sudo fdisk -l

---

### Post by justjuss on 2009-07-10
DOn't know what wubi is and I have partitioned my hd to have win xp pro and ubuntu 8.04 (used the wrong disk - thought I was putting my kubuntu 8.1 on.)


> **philcamlin said:**
> are you using wubi or partitioned?

---

### Post by justjuss on 2009-07-10
Here's what I got...
sudo cat /etc/fstab

sudo cat /boot/grub/menu.lst

sudo fdisk -l

actually, that's not what showed up in my terminal window. it kept asking me for my password and wouldn't accept it so I just keps typing the commands you gave me and hit enter after each line and it would say command not found.
justJuss



> **lindsay7 said:**
> type these commands in the terminal and post the results here

sudo cat /etc/fstab

sudo cat /boot/grub/menu.lst

sudo fdisk -l

---

### Post by lindsay7 on 2009-07-10
Type one command at a time. You will be asked for your password, enter it (you will not see what you type) and hit enter.  The password is what you used for password when you installed Ubuntu.

---

### Post by merlinus on 2009-07-10
Try this:

```
cat /boot/grub/menu.lst
cat /etc/fstab
```

Also, when you type in your password, nothing will show up on the screen.  Press enter after typing it in.

---

### Post by justjuss on 2009-07-10
Whoa!!!!!!!!!
Do you want me to post what happened? I tried to copy it and it wouldn't copy. but it says a bunch of stuff.
what now? I can't read and understand all this.
just Juss



> **merlinus said:**
> Try this:

```
cat /boot/grub/menu.lst
cat /etc/fstab
```Also, when you type in your password, nothing will show up on the screen.  Press enter after typing it in.

---

### Post by merlinus on 2009-07-10
Highlight the text with your mouse, and from the menu at the top of the window select Edit/Copy.

---

### Post by lindsay7 on 2009-07-10
Highlight the results of each command go to edit in the menu bar hit copy, Go to the reply screen in your post and go back to the edit menu and hit paste.

---

### Post by lindsay7 on 2009-07-10
Excuse me, I just reread your post,

> (01:42:23 PM) jussy: Hi, I just installed ubuntu8.04 on a partition next to my Win XPPro OS. How do I uninstall? 

Open windows, control panel, you should find something like administration, disk management, or something to that effect, format the partition or delete the partition where Ubuntu is installed.

If you want help getting Ubuntu installed, please provide the information that was requested.[COLOR="black"][/COLOR]

---

### Post by justjuss on 2009-07-10
OK see all it told me below:aaaghhhhh!!!!!!!!!!!!!!
What does it mean?


juss@jussyJustice:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,4)
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
root        (hd0,0)
savedefault
chainloader    +1

juss@jussyJustice:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=c1e69a24-b3d2-4f10-9cdf-5fe3b24743f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
juss@jussyJustice:~$ 
juss@jussyJustice:~$ 



> **lindsay7 said:**
> Highlight the results of each command go to edit in the menu bar hit copy, Go to the reply screen in your post and go back to the edit menu and hit paste.

---

### Post by merlinus on 2009-07-10
```
gksudo gedit /boot/grub/menu.lst
```and change this:

title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1

to this:

title        Microsoft Windows XP Professional
[COLOR=Red]rootnoverify        (hd0,0)[/COLOR]
[COLOR=Red]makeactive[/COLOR]
savedefault
chainloader    +1

(text to edit is in red)

then restart.

---

### Post by lindsay7 on 2009-07-10
We are trying to find our where windows and Ubuntu are installed on the disk partitions and compare that to what the boot loader is telling the system to do.

We need to see the result of 

sudo fdisk -l    (this is the letter l in the small case)

---

### Post by justjuss on 2009-07-10
There is the info I was finally able to get but I still don't know how to get my windows to load. If I can get the windows xp to load instead of unbuntu then I know how to delete the two partitions. 
Did you see what all it said when I put those commands in? WOW

> **lindsay7 said:**
> Excuse me, I just reread your post,



Open windows, control panel, you should find something like administration, disk management, or something to that effect, format the partition or delete the partition where Ubuntu is installed.

If you want help getting Ubuntu installed, please provide the information that was requested.

---

### Post by justjuss on 2009-07-10
ok. just a sec...


> **merlinus said:**
> ```
gksudo gedit /boot/grub/menu.lst
```and change this:

title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1

to this:

title        Microsoft Windows XP Professional
[COLOR=Red]rootnoverify        (hd0,0)[/COLOR]
[COLOR=Red]makeactive[/COLOR]
savedefault
chainloader    +1

(text to edit is in red)

then restart.

---

### Post by justjuss on 2009-07-10
At the bottom of the terminal screen I typed the 1st part then hit enter and tried to go on but got this

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
juss@jussyJustice:~$ 
juss@jussyJustice:~$ rootnoverify (hdO,O)
bash: syntax error near unexpected token `hdO,O'


Are these Capital O's or zeros?


> **justjuss said:**
> ok. just a sec...

---

### Post by justjuss on 2009-07-10
I was putting the # 1 there...Let me try "L" lowercase. RIght?



> **lindsay7 said:**
> We are trying to find our where windows and Ubuntu are installed on the disk partitions and compare that to what the boot loader is telling the system to do.

We need to see the result of 

sudo fdisk -l    (this is the letter l in the small case)

---

### Post by lindsay7 on 2009-07-10
When you get windows and Ubuntu installed, why not try Ubuntu for a while,  If you delete the partitions for Ubuntu you will also need to reinstall your windows mbr.  Search the internet for how to do this for windows xp or go to one of their forums for help.

---

### Post by lindsay7 on 2009-07-10
To fix the grub menu, you need to type the following in the terminal

gksudo gedit /boot/grub/menu.lst


a box will open with the lines of the grub menu, go down towards the end of the file where you will see the lines that Merlinus gave you, go to the end of the last correct line and hit enter then copy and paste the two lines in red that you were given. Do not make any other changes and then save the file and reboot your computer.

---

### Post by justjuss on 2009-07-10
After I typed it in your way this is what I got...after several tries...

[sudo] password for juss: 
sudo: cat/etc/fstab: command not found
juss@jussyJustice:~$ sudo cat/etc/fstab
sudo: cat/etc/fstab: command not found
juss@jussyJustice:~$ sudo cat/boot/grub/menu.lst
sudo: cat/boot/grub/menu.lst: command not found
juss@jussyJustice:~$ sudo fdisk-l
sudo: fdisk-l: command not found
juss@jussyJustice:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e9ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12017    96526521    7  HPFS/NTFS
/dev/sda2           12018       24321    98831880    5  Extended
/dev/sda5           12018       23815    94767403+  83  Linux
/dev/sda6           23816       24321     4064413+  82  Linux swap / Solaris




> **justjuss said:**
> Here's what I got...
sudo cat /etc/fstab

sudo cat /boot/grub/menu.lst

sudo fdisk -l

actually, that's not what showed up in my terminal window. it kept asking me for my password and wouldn't accept it so I just keps typing the commands you gave me and hit enter after each line and it would say command not found.
justJuss

---

### Post by justjuss on 2009-07-10
Lemme try this again...



> **justjuss said:**
> ok. just a sec...

---

### Post by lindsay7 on 2009-07-10
Ok, that confirms that Merlinus was correct in that windows is installed on hd (0,0), and that Ubuntu is on hd (0,4)


Just do what Merlinus said to do and add the two lines to the grub menu.  This should let you boot to either Ubuntu or windows.. Use copy and paste for those two commands so that you will not have a typo.

We have all the info needed and all you need to do the edit the grub menu as shown.


Here is the command again

gksudo gedit /boot/grub/menu.lst


Just copy and paste this. Also copy and paste the two lines to add to the menu.

---

### Post by justjuss on 2009-07-10
ok, I did this once and saved the getdit file and I'll do it again. Do you think that when I boot up and have the screen in front of me that gives me the choices of which os I want to load I should pust 'e' to edit the windows one? It does look different after I did what merlinis said to do. but it still won't allow windows to load. It just keeps switching back to Unbuntu.
I recall that when I was installing ubuntu I did something different than I had ever done before and that was to go to the advanced tab, at one point, and ad the chain??? to a +1 because I thought that this would make it so that I could turn my machine on walk away and it would just load windows instead of ubuntu. Now that I think of it I did something like that. I just wish I could go find those files and get into my windows side.I used to with Kubuntu.


is installed on hd (0,0), and that Ubuntu is on hd (0,4)


Just do what Merlinus said to do and add the two lines to the grub menu.  This should let you boot to either Ubuntu or windows.. Use copy and paste for those two commands so that you will not have a typo.

We have all the info needed and all you need to do the edit the grub menu as shown.


Here is the command again

gksudo gedit /boot/grub/menu.lst


Just copy and paste this. Also copy and paste the two lines to add to the menu.[/quote]

---

### Post by lindsay7 on 2009-07-10
Something is still not right. Please post this command again, it will show what the status of the grub menu file is after you made the change


cat /boot/grub/menu.lst   please note there is a space between cat and /boot

---

### Post by justjuss on 2009-07-10
Here it is again, like you asked: the last part of the cammand is menu.lst (lowercase L - as in "list"? or is it a digit one as in 1 ?)
Here is the terminals code:
juss@jussyJustice:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,4)
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
rootnoverify (hd0,0)
makeactive
savedefault
chainloader    +1



> **merlinus said:**
> ```
gksudo gedit /boot/grub/menu.lst
```and change this:

title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1

to this:

title        Microsoft Windows XP Professional
[COLOR=Red]rootnoverify        (hd0,0)[/COLOR]
[COLOR=Red]makeactive[/COLOR]
savedefault
chainloader    +1

(text to edit is in red)

then restart.

> **lindsay7 said:**
> Something is still not right. Please post this command again, it will show what the status of the grub menu file is after you made the change


cat /boot/grub/menu.lst   please note there is a space between cat and /boot

---

### Post by justjuss on 2009-07-10
> **justjuss said:**
> Here it is again, like you asked: the last part of the cammand is menu.lst (lowercase L - as in "list"? or is it a digit one as in 1 ?)
Here is the terminals code:
juss@jussyJustice:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=fba99385-dfbc-40e6-9583-ccd1ddeb7a84 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,4)
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
rootnoverify (hd0,0)
makeactive
savedefault
chainloader    +1
Oh, yeah and I did put that space.

---

### Post by lindsay7 on 2009-07-10
This looks correct to me, so you could 

1. wait and see if you get some more help on this.

2. reinstall ubuntu and see if you get the dual boot option

3. reinstall window mrb for windows xp  here is the site to see how to do this.  [http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)

---

### Post by merlinus on 2009-07-10
First, though, let's try reinstalling grub.

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```Enter these commands one at a time, and press Enter after each.

0 is a zero.

---

### Post by justjuss on 2009-07-10
OK I wrote all that and now I will restart.... I just don't know how to reinstall Unbuntu over the top of the same partitions so that I don't end up reformatting any of the windows partition. I don't have anything to loose on the unbuntu side.
justjuss
and thanks to both of you.


> **merlinus said:**
> First, though, let's try reinstalling grub.

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```Enter these commands one at a time, and press Enter after each.

0 is a zero.

---

