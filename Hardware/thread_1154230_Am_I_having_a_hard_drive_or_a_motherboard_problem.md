---
title: "Am I having a hard drive or a motherboard problem???"
date: 2009-05-09
forum: Hardware
---

### Post by Sambie on 2009-05-09
I'm having some problems lately and it seems like it's persistent. When I'm surfing thru the net... my browser automatically closes and when I try to re open it... it doesn't let me. Sometimes when I open a folder (My mp3's/pics/etc)... I see on an icon of a Master Lock on the upper right hand corner of my file icons. When I try opening them... they do not open as well. When I do a restart... here's what I get (I've took a screenshot of it on my camera phone)

My CPU
id:	
cpu:0
description: 	CPU
product: 	Intel(R) Core(TM)2 CPU 6400 @ 2.13GHz
vendor: 	Intel Corp.
physical id: 	
4
bus info: 	
cpu@0
version: 	6.15.6
serial: 	0000-06F6-0000-0000-0000-0000
slot: 	CPUSocket
size: 	1596MHz
capacity: 	2133MHz
width: 	64 bits
clock: 	266MHz
----------------

My motherboard
id:	
core
description: 	Motherboard
product: 	775Dual-VSTA
physical id: 	
0
----------------
My hard drive

id:	
disk
description: 	ATA Disk
product: 	WDC WD2500JS-00N
vendor: 	Western Digital
physical id: 	
0.0.0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	10.0
serial: 	WD-WMANK5975496
size: 	232GiB (250GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	0000e0e3
----------------

I hope this information helps.

The last time I've scanned my hard drive with a Western Digital diagnostic tool test.. the results came back with nothing. Is there a way to scan for a motherboard problem?

oops... My computer is not a laptop.

---

### Post by Sambie on 2009-05-09
bump

---

### Post by dsmithhfx on 2009-05-09
As is apparent in your attachment, you are getting ext3 format errors, which might not show up on a WD diagnostic. Hopefully you have a backup of critical data. If not, you could try to boot a cd and recover it to an external usb or network drive.

Then you will probably have to reformat the drive and do a clean install. There might be an underlying hw issue, so all you can do is wait and see if the problems come back.

---

### Post by Sambie on 2009-05-11
I keep having to reformat my hard drive but eventually it comes back with the same problem. sometimes it gives me the "Unable to boot" error. Do you think my hard drive is failing?

---

