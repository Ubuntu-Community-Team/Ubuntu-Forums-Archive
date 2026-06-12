---
title: "trouble dule booting/loading windows xp."
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by cactusfrog on 2009-07-02
I have recently installed ubuntu-9.04-desktop addition on to one of my harddives. I want it so when i boot up my computer i have an option of which OS to  boot off of, windows XP or Ubuntu. My harddives are SATA. when i have my ubuntu harddive plugged into the main port of my motherbord and the XP harrdive plugged into the second port and i boot it up i get the grub menu. This gives me the option to boot up into Ubuntu or windows. IF i choose Ubuntu, ubuntu runs fine. If i choose windows i get an error
```
Error 13 invalid or unsupported executable format
```
If i plug in my windows harddive so that its connected to the main port and boot up my machine i also get an error:
```
Grub loading stage 1.5
grub loading please wait
error 21
```
I don't know what i have to do so that i can boot up into windows again but i really need some help.

---

### Post by wojox on 2009-07-02
Keep your hard drive as your main port.
Go find a Windows install CD and boot that. 
Get into recovery console and run fixmbr.

---

### Post by papenpj on 2009-07-02
by running fixmbr, your going to loss the ability to access windows and will need to reinstall grub.


When you installed ubuntu did you move the windows drive to a different port? show me a copy of your

/boot/grub/menu.lst

---

### Post by cactusfrog on 2009-07-02
yes i did move my windows harddive to a different port originally it was connected to the first port but when it was like that i got the second error i listed so i changed its location to the secondary port so i could access the grub menu. 
here is my menu.lst
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
# kopt=root=UUID=d9245193-c6d2-4db2-98b6-87f53ac7036b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d9245193-c6d2-4db2-98b6-87f53ac7036b

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
uuid		d9245193-c6d2-4db2-98b6-87f53ac7036b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d9245193-c6d2-4db2-98b6-87f53ac7036b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d9245193-c6d2-4db2-98b6-87f53ac7036b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=d9245193-c6d2-4db2-98b6-87f53ac7036b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d9245193-c6d2-4db2-98b6-87f53ac7036b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by papenpj on 2009-07-02
ok you will need to use "sudo gedit /boot/grub/menu.lst"

under XPs option change "rootnoverify	(hd0,0)"

to "rootnoverify	(hd1,0)"


That way it will point to the first partition on the second drive, and hopefully locate your system.

Alternatively, to test if this method would work restart your computer. at the grub menu scroll down to the XP option

Press "E"
go to the root line and again press "E"
Now you can do a one-time change of that 0 to a 1.  Then press "ENTER" or "ESC" to apply the change I honestly forget which it is. then "B" to BOOT.
If windows loads you can hardcode the change using gedit.

---

### Post by cactusfrog on 2009-07-02
unfortunately that doesn't work changing that number to 1 just causes me to get this error when booting up.
```
error 21 selected disk does not exis
```t

---

### Post by papenpj on 2009-07-02
ok. how about trying.

"sudo fdisk -l"
to see what your partitions are like.

Or you could try to reinstall grub. I quickly googled this site. looks like it has that covered.
[http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/](http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/)

------
There might be an option 3. which would consist of putting the Windows drive back in slot 1 so it boots windows and chaging the MBR of that drive so when it boots it points to ubuntu. then ubuntu can point back to it.
I have no personal experience dual booting from separate drives. I might be able to test some theories on my USB drive that boots linux to point it back to my main drive.

However I do think a reinstall of grub might do the trick if not like I said try to change the mbr of the windows drive, which you can always do a fixmbr if that doesn't work. At least your able to boot one system or the other.

---

### Post by presence1960 on 2009-07-02
first, if your windows and Ubuntu are on separate drives you must have map lines in your windows entry in menu.lst, like this:
```

title          Microsoft Windows 7 RC
rootnoverify   (hd1,1)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1
```

Secondly post the output of ```
sudo fsdisk -l
``` That is a lowercase L. So we can get your windows booting from GRUB. Do not run fixmbr yet. If you needed to run that you most likely would get a message that NTLDR is missing. You are not able to boot windows because your (hdx,y) may be wrong and you have no map lines.

---

### Post by papenpj on 2009-07-03
good call with the map command, ill have to try that on my flashdrive as when i forget to remove it i would like it to go to my windows.

---

### Post by makinglife on 2009-07-03
Stop making it so hard their is a great thing called wubi im using it as we speak 
Windows is my default system but i have ubuntu 9.0.4 on here to with a 20g space limit on it, ( you can choose how much space you want on it). Oh and make sure your running windows Vista and down.

Heres your link.
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by papenpj on 2009-07-03
makinglife,
while wubi is nice to try ubuntu, you can't get the real benefits until you actually install it, plus when windows dies, I think then you can't easily get your ubuntu that uses wubi to run. just my 2 cents

---

### Post by QIII on 2009-07-03
My two cents -

Wubi is not the same as running Ubuntu natively.  It is a kludge.  (Sorry to those who use it.  If it works for you, go ahead and use it.)

Besides, it reminds me too much of the word "woobie", which I learned while I lived in Massachusetts.  It's definition is somewhat similar to "blankie" or even "binkie".

It can be a nice, warm Microshaft blanket wrapped around Ubuntu.

---

### Post by cactusfrog on 2009-07-03
here is my output when i type sudo fdisk -l
i added the map to my menu.lst still get the same errors. the grub on my windows drive is broken and i am not sure how to fix it because i need to boot up in windows
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19452     6032407+   5  Extended
/dev/sda5           18702       19452     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf812f812

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS
```

---

### Post by merlinus on 2009-07-03
What is the windows entry in menu.lst?  Also, you can remove the boot flag from sda1.

And what is the boot order of your hdds in bios?

---

### Post by cactusfrog on 2009-07-03
> **merlinus said:**
> What is the windows entry in menu.lst?  
i really don't know though i know its connected because i can assess it. 
> **merlinus said:**
> Also, you can remove the boot flag from sda1.
what do i do? 
> **merlinus said:**
> And what is the boot order of your hdds in bios? 
my bios just gives me the option to "Boot up on my onbord SATA hard dive and thats it can't pick the harddive port. heres a pic of my BIOS
[http://www.flickr.com/photos/35633310@N07/3683150651/sizes/l/](http://www.flickr.com/photos/35633310@N07/3683150651/sizes/l/)

---

### Post by merlinus on 2009-07-03
Change your windows entry at the end of /boot/grub/menu.lst to this (or add it if there is no windows entry):

title windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

You can edit the file by entering this command in a terminal:

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by cactusfrog on 2009-07-03
i did what you said but when i try to boot up i get  this error
```
error selected disk does not exist
```
even though it does
i also tryed messing with the settings like this but i always got that error.
```
title          Microsoft Windows xp hd1,1
rootnoverify   (hd1,1)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

title          Microsoft Windows xp hd1,0
rootnoverify   (hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

title          Microsoft Windows xp hd0,0
rootnoverify   (hd0,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1

title          Microsoft Windows xp hd1,0 but mapped difrently 
rootnoverify   (hd1,0)
map            (hd1) (hd0)
map            (hd0) (hd0)
chainloader    +1
```
does it matter that i CAN'T boot up into windows even if i unplug the harddive.

---

### Post by merlinus on 2009-07-03
At this point I believe the problem is that your bios is not recognizing your second hdd.  So no matter what you do, including changing the entry in menu.lst, you cannot boot into windows.

You might check the connectors, cables, and such.

---

### Post by cactusfrog on 2009-07-03
it does now turns out the correct layout was the only one i didn't try :S
d
```
title          Microsoft Windows xp hd1,0 
rootnoverify   (hd0,1)
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader    +1
```
so this layout allows me to get past all those errors but i have another problem although it says that its starting up... nothing happens ever. How do i fix this?

---

### Post by merlinus on 2009-07-03
According to the results of sudo fdisk -l, windows is on the first partition of your second hdd (sdb1).  So your windows entry is incorrect in menu.lst, and that is why nothing happens.

---

### Post by presence1960 on 2009-07-03
> **makinglife said:**
> Stop making it so hard their is a great thing called wubi im using it as we speak 
Windows is my default system but i have ubuntu 9.0.4 on here to with a 20g space limit on it, ( you can choose how much space you want on it). Oh and make sure your running windows Vista and down.

Heres your link.
[http://wubi-installer.org/](http://wubi-installer.org/)

That is all well and good, if you have installed via wubi. The OP has ubuntu installed to it's own partition. Wubi is basically for those who want to give Ubuntu a try without partitioning so if they don't like it it can be removed through windows add/remove programs. Did you know that over time wubi's perfermance will become degraded from windows fragmentation?  see here: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) scroll down and look under #11

If you really like Ubuntu it would be better to install to a dedicated partition.

---

### Post by papenpj on 2009-07-03
> **cactusfrog said:**
> 
does it matter that i CAN'T boot up into windows even if i unplug the harddive.

Actually it makes complete sense to me, here is why (as far as I understand it).  Grub is a bootloader that has been placed in the MBR, it is setup to point to a boot partition containing the next stage of grub which happens to be on harddrive 2 with ubuntu.  After that you can decide what part of the menu you want to load.


EDIT:
I just googled our problem because I am really itnerested in it for when I run into myself. We might need to try this
```
 
title Windoze
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
savedefault
chainloader +1


```


source:
[http://www.linuxforums.org/forum/mandriva-linux-help/134278-booting-windows-second-hard-drive-grub.html](http://www.linuxforums.org/forum/mandriva-linux-help/134278-booting-windows-second-hard-drive-grub.html)

Then from our own fourms I just found.

```


title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```
source:
[http://ubuntuforums.org/showthread.php?t=430450](http://ubuntuforums.org/showthread.php?t=430450)

SO, hopefully one of those two will work.

---

### Post by cactusfrog on 2009-07-03
for both of those options i get the error
```
selected drive does not exist
```
is their something wrong with my windows harddive? You said their was multiple partions on it but i don't remember  making multiple partions. what does the setting  
```
title Windows XP
root (hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
tell grub to do?

---

### Post by merlinus on 2009-07-03
As I wrote yesterday, yes.  It is not listed in your bios.

You can try supergrub to try and access windows as a last resort:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by Vaitya on 2009-07-03
Hi there, I am having a similar problem with my system. I've been struggling with this on and off for a month or two now, but would like to find a better solution than my current work around - which is that I disconnect my linux drives whenever the GF wants to use windose.

Sudo fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe42fe42f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60051   482359626   83  Linux
/dev/sda2           60052       60801     6024375    5  Extended
/dev/sda5           60052       60801     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18700   150207718+  83  Linux
/dev/sdb2           18701       19457     6080602+   5  Extended
/dev/sdb5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2         832     6282360    5  Extended
/dev/sdc2   *         833       20672   149990400    7  HPFS/NTFS
/dev/sdc5               2         832     6282328+   7  HPFS/NTFS



SDA is my primary linux system. SBA is an older drive with an old copy of ubuntu on it that I don't use, but haven't ever bothered cleaning up. It's basically just storage that I don't really need at this point. SDC is the windose drive, with a "fresh" XP reinstall on either sdc1 or sdc5. SDC2 is the old windose install, but has all of the GF's files on it so I don't want to mess with that partition. Sdc5 _should_ be the partition XP is now installed on, and I have no idea what sdc1 is (what is Extended partition type?) Just to be totally clear, the fresh windows install was done with the other 2 hard drives disconnected.

/boot/grub/menu.lst:   (it's kind of spammy, sorry)

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		2272a45e-50c1-4809-9ea3-013191c65841
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2272a45e-50c1-4809-9ea3-013191c65841 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title           Windows XP Professional
rootnoverify    (hd2,0)
Map		(hd0)(hd2)
Map		(hd2)(hd0)
savedefault
makeactive
chainloader     +1


title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2272a45e-50c1-4809-9ea3-013191c65841
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2272a45e-50c1-4809-9ea3-013191c65841 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		2272a45e-50c1-4809-9ea3-013191c65841
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2272a45e-50c1-4809-9ea3-013191c65841 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		2272a45e-50c1-4809-9ea3-013191c65841
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=2272a45e-50c1-4809-9ea3-013191c65841 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		2272a45e-50c1-4809-9ea3-013191c65841
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



I removed all of the commented out lines and the "Other Operating System" lines to reduce the spam. Also, can I remove from menu.lst some of the options that I don't use and probably never will (eg the "Other Operating Systems" options), and do this without harming the main boot ups?


Currently with this menu.lst config I get the error 13 issue (not a valid executable something or other). Any other (hd2,x) with result in an invalid device/drive. I've also tried various Map configurations, and to the best of my ability to tell, map seems to do nothing at all. Those lines seem to get dropped - when I've edited the grub menu using the 'e' on the windows entry those lines are not there.

Now, in my BIOS SDA is the main boot drive and is listed in the first position, the sdb is listed as the second drive, and sdc is listed as the third. Also of unknown importance is that SDA and SDB are SATA drives, while the SDC is the old IDE type (big wide cable with many many pins). It has Master position o nthe cable that it shares with my dvd r/w drive.

Currently in order to start up windows I have to pull the power off the two SATA drives, but it starts just fine. This is not a situation I would like to continue as sooner or later some sort of beverage will be dumped into my open cpu case :)


Sorry to barge in on this thread, but it seems to be the closest one to my own issue, so there may be no need to start up a duplicate.

Many thanks in advance for those who try to help, or even just those who read this long long post :)

---

### Post by merlinus on 2009-07-03
A few things:

This --
[COLOR=Red]
title           Windows XP Professional
rootnoverify    (hd2,0)
map        (hd0)(hd2)
map        (hd2)(hd0)
savedefault
makeactive
chainloader     +1[/COLOR]

needs to go below this line:

[COLOR=Red]### END DEBIAN AUTOMAGIC KERNELS LIST[/COLOR]

Also, you have two redundant entries for ubuntu, surrounding the windows one that is in the wrong place, so once you move the windows one delete these:

[COLOR=Red]title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2272a45e-50c1-4809-9ea3-013191c65841
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2272a45e-50c1-4809-9ea3-013191c65841 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet[/COLOR]

[COLOR=Red]title           Windows XP Professional
rootnoverify    (hd2,0)
Map        (hd0)(hd2)
Map        (hd2)(hd0)
savedefault
makeactive
chainloader     +1[/COLOR]


[COLOR=Red]title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2272a45e-50c1-4809-9ea3-013191c65841
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2272a45e-50c1-4809-9ea3-013191c65841 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic[/COLOR]

Also, change the windows entry to:

[COLOR=Red]title           Windows XP Professional
rootnoverify    (hd2,1)
map        (hd0) (hd2)
map        (hd2) (hd0)
savedefault
makeactive
chainloader     +1[/COLOR]

Note the spaces in the map lines between (hd0) and (hd2), and (hd2) and (hd0).

---

