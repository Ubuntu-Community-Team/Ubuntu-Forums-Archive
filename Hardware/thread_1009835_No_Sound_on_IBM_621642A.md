---
title: "No Sound on IBM 6216/42A"
date: 2008-12-13
forum: Hardware
---

### Post by swudee on 2008-12-13
Hi 

I am having trouble getting the sound to work on this machine.Ubuntu 8.10.
I have also tried the live CD of 8.04 with the same problem.
The onboard sound is enabled in the bios.
Double clicking the volume control icon shows the device as an Intel 82801DB-ICH4 (Alsa mixer)
All looks normal there. But when I run alsamixer in terminal.
It shows only one (master) volume control.

It lists the card as PulseAudio and the chip as PulseAudio.

lspci -v | less  list this as the relevant part.

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM Device 1f00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 6000 [size=256]
        I/O ports at 6400 [size=64]
        Memory at 80200000 (32-bit, non-prefetchable) [size=512]

I have been looking through the forums without much luck so far.
Any help before I go to give this to my niece, 1200 miles away, tommorow would be apreciated.

---

