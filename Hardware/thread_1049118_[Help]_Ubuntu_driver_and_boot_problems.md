---
title: "[Help] Ubuntu driver and boot problems"
date: 2009-01-24
forum: Hardware
---

### Post by ren_mot on 2009-01-24
Ok so i have a few problems im hopping someone can help me with

The Problem -
My touch pad isn't working on ubuntu and i cant connect to the internet but everything worked on the live CD
I also have BackTrack 3 installed and the touch pad works but it won&#8217;t connect to the internet.
There might be other hardware problems since whenever i try to open the Restricted Drivers manager it says 
you need to install the package linux-restricted-modules-2.6.21.5
for this program to work
and the device manager has a lot of unknow devices on it


Overview - 
I have a Sony Vaio PCG-Z1VA notebook
i recently formatted my pc
(i wanted to have windows and linux installed on it)
First i installed 
Windows XP (everything worked)
Then i installed 
Ubuntu 7.10
and then i installed 
BackTrack 3 Final

The thing is that when i installed BackTrack 3
it changed the MBR to lilo
(i think i don&#8217;t know much about this)
and i could only boot backtrack
windows and ubuntu disappeared from the boot screen
so i had to configure the lilo.conf file to boot the other os

My lilo.conf file looks like this :


```

append = &#8220;resume =dev/hda5 splash=silent&#8221;
boot = dev/hda
prompt
timeout = 60
#bitmap=/boot/splash.bmp
change-rules
reset
#vga = 769,771/773/792
vga = 769
image = /boot/vmlinuz
	root = current
	label = BackTrack
	read-only

#Windows Boot
other = /dev/hda1
label = WindowsXP
table = /dev/hda

#Ubuntu Boot
image = /boot/vmlinuz
root = /dev/hda3
label = Ubuntu
read-only 

```

and my disk drive is partitioned like this

```

Name    Flags    Part Type  FS Type        [Label]    Size(MB)
------------------------------------------------------------
hda1    Boot     Primary    NTFS           [     ]    80023.75
hda2             Primary    Linux ReiserFS            20003.89
hda3             Primary    Linux ext3                58465.30
hda5             Logical    Linux swap                 1546.36

```

after i wrote that on the lilo.conf i was able to boot to windows, ubuntu and backtrack but with this problem

im using a 
Linksys WRT300N Wireless-N Broadband Router
and it doesnt connect even if i conect it with a cable.
Its also taking much longer to boot Ubuntu and backtrack

can anyone tell me what i did wrong 
Ubuntu and backrack worked just fine on this computer before

---

