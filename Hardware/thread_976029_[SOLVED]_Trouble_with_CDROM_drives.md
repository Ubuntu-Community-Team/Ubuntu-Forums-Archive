---
title: "[SOLVED] Trouble with CDROM drives"
date: 2008-11-08
forum: Hardware
---

### Post by shanek on 2008-11-08
I've been having this problem since installing Hardy last spring, and a fresh install of Intrepid hasn't helped one bit. 

When I first boot the computer, I'll sometimes be able to read a data or Audio CD for a little while, but after a few minutes, I can't read it anymore. Using the eject command freezes whatever console I'm in, I never get another prompt after issuing the command. Same thing if I use lshw.

The last time my CDROM drives worked was back in Gutsy. The main difference that I noticed is that the drives are now referred to as /dev/scd0 and /dev/scd1 rather than the old /dev/hda /dev/hdb that they used to be under Gutsy. 

I've tried swapping out drives, changing out cables, changing IDE channels, switching between 40 and 80 wire cables, changing jumper settings. I've also tried a whole raft of kernel parameters. Nothing helps at all.

From kern.log:```
Nov  8 23:17:09 cheetah kernel: [ 2644.312061] ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Nov  8 23:17:09 cheetah kernel: [ 2644.312084] ata3.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
Nov  8 23:17:09 cheetah kernel: [ 2644.312087]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Nov  8 23:17:09 cheetah kernel: [ 2644.312090]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Nov  8 23:17:09 cheetah kernel: [ 2644.312096] ata3.01: status: { DRDY }
Nov  8 23:17:09 cheetah kernel: [ 2644.312129] ata3: soft resetting link
Nov  8 23:17:09 cheetah kernel: [ 2644.500436] ata3.00: configured for PIO0
Nov  8 23:17:09 cheetah kernel: [ 2644.516472] ata3.01: configured for PIO0
Nov  8 23:17:09 cheetah kernel: [ 2644.516508] ata3: EH complete

``` This is repeated a whole bunch of times.

I've got an ASUS a8v motherboard (VIA chipset). 

It looks like that since Hardy, we're using a new kernel module, and it's incompatible with my setup for some reason. Is there any way we can get the old kernel module back? (and does anybody know what this module is?)

---

### Post by shanek on 2008-11-20
Still having trouble with this. 

Here's the message I get when trying to open a DVD in Nautilus:
```
Cannot invoke CheckForMedia on HAL: 
org.freedesktop.DBus.Error.NoReply: Did not receive a reply. 
Possible causes include: the remote application did not send a reply, 
the message bus security policy blocked the reply, the reply timeout expired, 
or the network connection was broken.
```

Often, I will be able to open a disc when I first boot up the computer, but after a few minutes, the drives no longer work. I can't even use the eject command.

I was thinking that it might be a hardware problem, but if that was the case, I certainly wouldn't have been able to install the entire OS from CD.

---

### Post by shanek on 2008-11-20
Booting into the same live CD that I used to install my system ran for about an hour with no problems. lsmod | grep ata gave me the same exact kernel modules.

Booting back into my installed system, the CD/DVD drives are once again not working.

*Something* is different in the way that the live CD runs compared to how an installed system runs.

---

### Post by shanek on 2008-12-05
OK then, I've finally got some progress with my DVD drives.

It's an ugly solution, but compiling my own kernel seems to have done the trick so far. After successfully ripping several CDs and DVDs I'm almost convinced. Haven't tried burning yet. 

Basically, I used apt-get source to retrieve the latest Ubuntu kernel's source code, copied the config from my /boot directory to the newly downloaded source directory and used make menuconfig to tweak the configuration. I removed the pata_via module, and added ATAPI CDROM support and IDE support for via 82xxx chipsets. Removed debugging while I was at it. I also had to remove some Xen related modules, because a makefile was missing somewhere. Ugly process overall, but once I finally got my deb files made, it worked just fine. It's been several hours now, and things still seem to be working.

Anyway, it's good to know that it's not my hardware. Now, if I can just figure out a way to make this process a bit less painful.

---

