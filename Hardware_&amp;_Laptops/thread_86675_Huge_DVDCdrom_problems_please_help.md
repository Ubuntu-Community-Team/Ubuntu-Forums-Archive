---
title: "Huge DVD/Cdrom problems please help"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by kittcankitt on 2005-11-06
I'll try to make this straight and to the point.  Up until a few hours ago my dvd-burner was working flawlessly.  It's an AOPEN duw1616/arr that is only a month or so old.  I was burning a dvd iso image and for some reason my computer completely froze (which rarely if ever happens, surprisingly as it's an old clunker...amd500 300and change ram, etc...) anyhow I was only able to get moving again by shutting it down the hard way.  NOW, the drive doesn't seem to work at all.  If I put a disk in it will show an icon on the desktop and I can use the eject to eject it (as well as from the command line) but the light keeps blinking and nothing appears on the disks.  I can't boot from it either.  I have shut down/restarted several times.  Unplugged the drive, rebooted, plugged it back in, etc...same thing. 

Dmesg gives me this as the drive initiates reading the disk:

[23960.460051] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[23960.460150] hdb: packet command error: error=0x40 { LastFailedSense=0x04 }
[23960.460164] ide: failed opcode was: unknown
[23960.460916] ATAPI device hdb:
[23960.460927]   Error: Hardware error -- (Sense key=0x04)
[23960.460943]   Focus servo failure -- (asc=0x09, ascq=0x02)
[23960.460961]   The failed "Read Cd/Dvd Capacity" packet command was:
[23960.460967]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[23962.359842] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[23962.359878] hdb: packet command error: error=0x40 { LastFailedSense=0x04 }
[23962.359893] ide: failed opcode was: unknown
[23962.360663] ATAPI device hdb:
[23962.360676]   Error: Hardware error -- (Sense key=0x04)
[23962.360695]   Focus servo failure -- (asc=0x09, ascq=0x02)
[23962.360712]   The failed "Read Cd/Dvd Capacity" packet command was:
[23962.360719]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[23962.465149] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[23962.465176] hdb: packet command error: error=0x40 { LastFailedSense=0x04 }
[23962.465190] ide: failed opcode was: unknown
[23962.465940] ATAPI device hdb:
[23962.465949]   Error: Hardware error -- (Sense key=0x04)
[23962.465965]   Focus servo failure -- (asc=0x09, ascq=0x02)
[23962.465990]   The failed "Read Cd/Dvd Capacity" packet command was:
[23962.465996]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[23962.581478] cdrom: This disc doesn't have any tracks I recognize!
[23962.841815] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[23962.841844] hdb: packet command error: error=0x40 { LastFailedSense=0x04 }
[23962.841858] ide: failed opcode was: unknown
[23962.842585] ATAPI device hdb:
[23962.842593]   Error: Hardware error -- (Sense key=0x04)
[23962.842609]   Focus servo failure -- (asc=0x09, ascq=0x02)
[23962.842626]   The failed "Read Cd/Dvd Capacity" packet command was:
[23962.842633]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[23962.855279] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[23962.855305] hdb: packet command error: error=0x40 { LastFailedSense=0x04 }
[23962.855319] ide: failed opcode was: unknown
[23962.856054] ATAPI device hdb:
[23962.856063]   Error: Hardware error -- (Sense key=0x04)
[23962.856078]   Focus servo failure -- (asc=0x09, ascq=0x02)
[23962.856093]   The failed "Read Cd/Dvd Capacity" packet command was:
[23962.856100]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[23962.939874] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[23962.939898] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.


To me this looks bad with a capital B!  Actually the last two lines repeat several times as well and that's new since the freeze up.  I really haven't had time to look into that yet.  Right now my main concern is the drive as I said it is brand new and was functioning perfectly.  

If any hardware guru out the could help me decipher what the dmesg is about or give me an idea of where I should start looking to get it going again, I'd be forever  grateful!

Thanks and sorry about the long post, I guess it was so "straight and to the point" as I'd hoped...KCK

---

### Post by jvictor on 2005-11-06
Can u hear some spinning noise when u insert a disc? I feel that ur drive is jammed. .there can b a variety of reasons..ranging from a simple alignment prob to the most fearful -: that ur drive's servo motor has just given u a TATA-BUH-BYE. But since the drive is 1 month old u maybe in warranty period..i'd suggest to give it back , and avoid self repair :)

---

### Post by kittcankitt on 2005-11-06
It sounds like it wants to engage, I'm not sure if it's spinning.  Unfortunately it was an ebay purchase and the returning it option doesn't look so good.  I might end up having to take it apart and get a better look inside.  It was quite warm just before all this happened.

Going through the logs I see I have an error that Xserver isn't started up (i think that has to do with the keycodes error?) and somewhere else there is mention of swsusp: wrong signature 

I really don't know what's going on...any other ideas?

---

### Post by Teroedni on 2005-11-06
here is for the last part
[http://ubuntuforums.org/showthread.php?t=76271](http://ubuntuforums.org/showthread.php?t=76271)

as for the other i will see what i find out

---

### Post by Teroedni on 2005-11-06
Can you try ubuntu live cd 
or even windows cd if you got
disable the hardrive in bios  and see if you can get the dvd drive to boot a bootable cd like windowsxp or ubuntu live cd

---

### Post by kittcankitt on 2005-11-07
Thanks, I found out about the keycodes bug searching around too.  No, I can't even seem to boot off the drive.  It starts, sounds like its spinning at first then stops.  I can't seem to figure out what's going on.  I started some of the burning programs I have and they all still see the drive and nerolinux even sees that dma is turned on (and off, as I tried that too)  

A hdparm -i /dev/hdb gives this:

/dev/hdb:

 Model=AOPEN DUW1616/ARR, FwRev=1020, SerialNo=&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;&#65535;
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 *mdma2
 UDMA modes: udma0 udma1 udma2
 AdvancedPM=no
 Drive conforms to: device does not report version:

 * signifies the current active mode

Any other ideas folks?

---

### Post by Teroedni on 2005-11-07
To make sure: 
You can see the drive in Bios??
you set it to boot cd first in bios, and it wouldn't boot?
so neither live cd or perhaps windows cd would boot even though you disable harddrive and set cd to first boot in bios????

---

### Post by kittcankitt on 2005-11-07
That is absolutely correct.  It shows up in both the bios and in all the  device managers in ubuntu but it won't boot a live cd.

For that matter like I posted earlier, if I put a cd/dvd in the drive it'll actually put an icon on the desktop and I am able to open it in a file browser but no files on the cd/dvd show. ???

---

### Post by Teroedni on 2005-11-07
If you set bios to boot cd first and it cant boot then i am afraid your cd/dvd drive is malfunction:(.

---

### Post by jvictor on 2005-11-07
U see the drive on ur desktop becuase the firmware and the chips in ur drive are still functional , but the mechanical part of it is goofy goofy.. since its new it maybe just a jam, y dont u take it to soem drive repairing guys, they will b able to give u a better picture..

---

