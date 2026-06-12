---
title: "HELP!!! Sony Vaio doesn't want to read SONY memory stick PRO duo."
date: 2009-05-30
forum: Hardware
---

### Post by peterkim04 on 2009-05-30
Hello guys, I seriously need some help.
I have a VGN-NR10E, wiped vista that came with completely and got myself a 8.10 II. I am having trouble with the memory stick slot on the laptop. I have two slots, one for SD and another one for Memory Stick pro duo. when i was using the vista, they both worked so i know it's not the hardware trouble. since i got the ubuntu the SD slot work perfectly but the stick pro duo doesn't want to work, no error or warning, no recognition at all.
i have read a few advices but none of them work, any help will be much appreciated. thanks in advance

---

### Post by DVANDERM on 2009-05-30
I don't have a fix for this as I am looking for one myself. I know that it has to be something with Ubuntu not recognizing the slot on the Sony Vaio's. I have an HP desktop that has the slot also and recognizes and reads from it just fine. 

I'm going to watch this thread in the hopes that someone has an answer because I've been searching for awhile now.

EDIT: 

I have a NR260E some I'm wondering if it's all Sony's or just the NR series.

---

### Post by DVANDERM on 2009-05-30
Oh and it might help to open a terminal and use this command and post the readout for the memory card slots.

lspci -v

Then look for something that looks like this and post it:

```

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fc204000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 90000000-93fff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fc206000 (32-bit, non-prefetchable) [size=2K]
	Memory at fc200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fc205000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

```

Sorry for hijacking just trying to help. We may both have the same hardware.

---

### Post by peterkim04 on 2009-05-31
> **DVANDERM said:**
> Oh and it might help to open a terminal and use this command and post the readout for the memory card slots.

lspci -v

Then look for something that looks like this and post it:

```

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fc204000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 90000000-93fff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fc206000 (32-bit, non-prefetchable) [size=2K]
	Memory at fc200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fc205000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

```

Sorry for hijacking just trying to help. We may both have the same hardware.

No problem at all, more people having the same/similar trouble must be easier to find the solution. I have run on the terminal what you seggested and here it is,

08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fc204000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 90000000-93fff000
	I/O window 0: 00005000-000050ff
	I/O window 1: 00005400-000054ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fc206000 (32-bit, non-prefetchable) [size=2K]
	Memory at fc200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Sony Corporation Device 902d
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fc205000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: tifm_7xx1
	Kernel modules: tifm_7xx1

it looks pretty similar if not identical, i haven't gone through both of them thoroughly. I keep trying to find something so i will let you know if i find anything, if you come across anything maybe do the same thing?
ta

---

### Post by DVANDERM on 2009-05-31
I'm still trying to find something. If I do I will chime in and post a link or the instructions here.

Thanks

---

### Post by baucha_linux on 2009-06-09
Hi guys,

I also have been trying to search the solution for the same problem. I got NR160E and my memory stick is also not recognized. 

After a couple of hours of searching i found this site but it's in German.

[http://www.sw83.de/2008/04/memorystick-support-unter-ubuntu-hardy.html](http://www.sw83.de/2008/04/memorystick-support-unter-ubuntu-hardy.html)

may be u can use google translate then can understand some things written over there. I haven't tried it so far cos i dunno wot i am doing. It seems he is trying to patch the tifm driver but not sure.

May be someone who has tried can give us feedback so that we can know whether it really works and how can it be done.

Waiting for some useful input.

---

### Post by baucha_linux on 2009-06-09
Hi again.

I just found this post here in the forum. This seems to solve the problem even for jaunty. Good luck..

[http://ubuntuforums.org/showthread.php?t=797031&page=2](http://ubuntuforums.org/showthread.php?t=797031&page=2)

havnt tried it yet ;)

---

### Post by baucha_linux on 2009-06-09
there is a nice shell script in the page 4 of that post. Now I'm trying that. 148 MB to download and still it's gonna take time to compile. Dunno how long it's gonna take.... 

lets hope this wont break my system ;)

will post the result...

---

### Post by baucha_linux on 2009-06-10
VOILA!!! my memory stick is now detected after following the instructions posted here [http://ubuntuforums.org/showthread.php?t=797031&page=2](http://ubuntuforums.org/showthread.php?t=797031&page=2)

:D

---

### Post by peterkim04 on 2009-06-12
baucha, thanks for the help.
i actually tried that method, downloaded and installed and updated the kernel and everything was going well, until the step 2. i think this is more general 'ubuntu knowledge lacking for me' issue but i couldn't add the 'config_memstick=m' to my i386/config. any help/suggestion on that? the error message was that i didn't have enough access control or something on those lines? i am the administrator(or whatever is equivalent on ubuntu) and the only user so i don't know why it says i don't have permission to change my i386/config. 
any help will be mucho appreciated.
regards

---

