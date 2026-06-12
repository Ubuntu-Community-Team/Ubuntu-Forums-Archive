---
title: "Hi Folks, need some help, I'm trying, and trying, and . . ."
date: 2009-08-19
forum: Hardware
---

### Post by larry19l on 2009-08-19
Hi Folks,
Need a little help . . . :(
Hware is an HPcompaq R4000 AMD 64x1 w/2gigRAM, 60gigHD ATI Radion 200 with current drivers for, yes, EVERYthing.
Used FreeDOS Fdisk to partition as follows:
Partition 0: 19456 - ntfs
Partition 1: 18432 - fat32
Partition 2: remainder (18.9g) unformatted (fat32)
---
Original system discs with custom HP labeling install like retail winXPpro32. Installed to partition 0; successful install and boot.
Retail win98se disc from an older system (gone now) install ok, but when I booted from the CD, partition 0 was not recognized so the CD booted and it asked to be installed to drive "C" which, from the space it said was available, was clearly partition 1. Which under winXPpro's shell (explorer) shows up as "D" drive.
Anyway, I ran the win98se install to "C" drive to normal completion. I used GAG410 to multi-boot and added winXPpro and win98se then installed GAG to the boot sectors and did a cold boot to GAG and booted up winXPpro with no problem. Installed all the drivers and then downloaded the latest drivers from HP and installed them. Then a restart to winXPpro and all is ok. Partition 1 shows as "D" and is formatted as fat32. Partition 2 shows as "E" and fat32. Another restart and try to boot to win98se. Boots to DOS runs config.sys and autoexec.bat but win.com chokes: insufficient memory and says to dump stuff from config.sys which only has the following:
Device=himem.sys
DOS=high,umb
Device=EMM386.sys NOEMS
Files=30
Buffers=20
Stacks=0,0
Device=setver.exe
;;;

the above auto loads DBLBUFF.sys and IFSHLP.sys

then . . .

Autoexec.bat:
echo off
Set path=C:\;C:\windows;c:\windows\command;c:\windows\system;
prompt $P$G
;;;

ok so I haven't figured out how to get win98se running . . . 
 . . . yet ? :confused: Is there a better version of Himem or Emm386 ?

Popped in the Ubuntu cd and booted, picked install and got as far as the partition mgr which gave me 2 choices:
1...use entire disc (not gonna happen)
2...manual install
(no "Guided ...")

So now how do I install Ubuntu to partition 2: /dev/sda3/
When I "edit" the partition I get a list that does NOT include "root partition". I tried fat32 & fat16 but the rest don't seem right ? Like ext2,3,4 journaling whatever and other stuff !

And mount point offers either /dos or /windows... choices... choices...:(

I'm gonna try deleting the win98se partition and I expect that I will be able to do a guided install to partition 1, but then I don't know if the win98se will install to partition 2 ! we'll see.
In the meantime, maybe somebody knows how to get win98se up and running ? I want it for some Dreamcatcher Interactive games.

I was able to get win98se up on my desktop using Sun's VirtualBox in Ubuntu but not in winVista and I haven't tested the games on it so I don't know if they will run.

My ideal situation would be:
HPcompaq notebook: AMD 64x1 2gig RAM, 60gigHD, 80gig USBHD (for data ONLY)
Use GAG or Grub
 (I'd prefer Grub but I'd wanna be able to edit it's menu.lst from any OS)
partition 0: winXPpro32 (from original system discs)
partition 1: win98se (from original retail disc)
partition 2: Ubuntu 9.04 64bit

HP pavilion media center: AMD 64x4 5gig RAM, 640gigHD, 400gigHD, 1,000gigHD (this 1TbHD is for data ONLY)
Use GAG or Grub
 (I'd prefer Grub but I'd wanna be able to edit it's menu.lst from any OS) 
640gigHD partition 0: winVista home premium (install from restore segment)
640gigHD partition 1: win7rc (ultimate / download as iso)
----
400gigHD partition 0: install win98se (100gig partition)
400gigHD partition 1: Ubuntu 9.04 (300gig partition)

In other words, to make it simple (IOW2MIS) 3 os'es on each of 2 machines.
To make it easy, the HD's for partitioning and OS install have ABSOLUTELY NO DATA. Data is all on the 1Tb SATA, 80gb USB and a 8gig Sandisk cruzer (U3)

It's a BFmess,  NE1 wanna help me clean it up ? . . .:lolflag:

And one last item: I still need to install the Wacom stuff on the desktop. . .;)

---

### Post by Favux on 2009-08-19
Hi larry19l,

I can help you with the Wacom stuff.

As for the other stuff, not so much.

Win98SE does not run well on more that 512 MB of RAM.  And you have 2 GB!  That's what the "Insufficient memory to initialize windows.  Etc." is trying to tell you.  See article ID:  253912 in the Microsoft Knowledge Base.  One work a round is to use the MaxFileCache setting in System.ini.  Go to [vcache] and:
```
MaxFileCache=524,288
```
524,288 KB is 512 MB.  That's the max.  A little less might be better, say 522,240 KB or 510 MB.  And that's right, it won't use the other 1.5 GB.

For Jaunty and lower the native file system is ext 3.  That's what you want the Ubuntu partition formatted as.  ext 4 is the new one which I think will be default in Kharmic.  It's faster but since it's new there have been some reports of data corruption.  I think that's why it's "test" for Jaunty.

Hope this helps.

---

### Post by larry19l on 2009-08-20
Thanks Favux,

Here's where I am so far...
XP back up and running on the 64x1 notebook, Vista home premium back up on the 64x4 desktop via a complete system restore (35 hrs non-stop, yuck!), to the entire 640gHD and Jaunty to the entire 400gHD. I'm not yet gonna bother with win7rcU anywhere for now. When I go for win7u as a full retail, I hope I won't have to de-crapify it, that took 3 hours with the vista desktop.

anyway...

I'm still not sure how to partition the 400gHD to put win98se past the Jaunty partition. I think I will poke around here to see how to do the partition and formating under Jaunty. After all the entire 400g stays fat32. Right ? Then all I need to do is identify the partition for Grub and edit "menu.lst" to add another item to the list.

This is what's in menu.lst so far...
--[[[[[[
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		2b0b3461-1d19-40f9-8a29-ece61a0817fe
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2b0b3461-1d19-40f9-8a29-ece61a0817fe ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		2b0b3461-1d19-40f9-8a29-ece61a0817fe
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=2b0b3461-1d19-40f9-8a29-ece61a0817fe ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		2b0b3461-1d19-40f9-8a29-ece61a0817fe
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista boot
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista boot to System Restore
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
]]--

So how to identify where Jaunty is now ?
and assume it is in (hd0,0) and win98se is in the second partition of the 400gHD that being (hd0,1), but what device ? If sda2 is the "first" drive, the 640gHD, then what is the 400gHD which is connected to the second sata port ? !
So I could add:

# This entry manually added for a non-linux OS
# on /dev/???
title		Windows 98se boot
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

BTW, yup, 1k is 2e10 NOT 1,000 and 1meg = 2e20 so yes half a meg is 2e19.
I did enough assembler programming, back in the day to watch the bit count.
The other stuff is for the sales and marketing folkk.

meanwhile, what can you tell me about installing Wacom ? I've got an Intuous 3 - 6x11 that I'd like to get working.

Also what is your experience with the mouse ? This is the second one that's dying on me in a year ! The left button starts becoming unreliable for about 2 months till it dies altogether !

---
L8r
me

---

### Post by Favux on 2009-08-20
Hi larry19l,

There's some gurus on the Installation & Upgrade forum who can help.  Do this stuff in their sleep.  Doesn't Win98 want to be C?  You should check on gparted:  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)  I don't know if it works with Vista yet.  So be careful.

Some good links.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[https://help.ubuntu.com/8.04/installation-guide/powerpc/partitioning.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/partitioning.html)

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)


To install the Intuos3 in Jaunty see post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Then to set up wacomcpl see "Section 3:  Calibrating your Tablet" at:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I've never used the Wacom mouse.  Is there a replaceable spring in there?

---

