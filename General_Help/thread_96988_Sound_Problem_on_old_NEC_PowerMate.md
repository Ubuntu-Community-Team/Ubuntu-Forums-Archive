---
title: "Sound Problem on old NEC PowerMate"
date: 2005-11-30
forum: General Help
---

### Post by itencate on 2005-11-30
Hi all,

I'm having a problem getting sound to work on an old Powermate computer I use for Ubuntu 5.10.

As near as I can tell it's got an OPLSA3 sound card built into the motherboard; at the moment I have the following additions in /etc/modules:

opl3sa2 io=0xe80 irq=5 dma=1,3
snd-cs46xx

In addition, I get the following if I pull dmesg | more

[   36.643222] isapnp: Scanning for PnP cards...
[   36.736177] isapnp: Card 'OPL3-SA3 Snd System'
[   36.736195] isapnp: 1 Plug & Play card detected total


[  176.439030] ad1848/cs4248 codec driver Copyright (C) by Hannu Savolainen 1993-1996
[  176.441781] pnp: Device 01:01.00 activated.
[  176.441803] ad1848: PnP reports 'OPL3-SA3 Snd System' at i/o 0xe80, irq 5, dma 1, 3
[  176.500167] opl3sa2: probe of 01:01.00 failed with error -16
[  176.500194] opl3sa2: No PnP cards found


Note that I put the 0xe80, irq 5, etc. into /etc/modules after it was reported by the kernel load.

Regardless, I don't get any sound, or even the creation of a /dev/dsp on boot.

Any thoughts on what I might be missing?

Ian

---

### Post by kelean on 2005-11-30
Check your /etc/modules to see if your sound card is listed. If it not then add it to the end of the file and save it.  Then reboot and see if that works

---

### Post by itencate on 2005-12-02
OK, found an answer (after about 15 hours of trial and error plus google-searching), so I thought I'd post it in case some other poor soul is trying to get ubuntu 5.10 (breezy badger) to run on an old NEC PowerMate (in my case I believe 8100 ES; might be an 8000 or 9000 series - I bought it second hand so I'm not sure).

Basically, I tried a bunch of diagnostic stuff - one key step was to run pnpdump (not by default in ubuntu - I pulled it down off of another site for a previous install, but still had access to it).

It included a bunch of information, including the following lines:

# Card 1: (serial identifier cb 80 86 00 01 30 00 a8 65)
# Vendor Id YMH0030, Serial Number 2156265473, checksum 0xCB.
# Version 1.0, Vendor version 0.0
# ANSI string -->OPL3-SA3 Snd System<--

which told me that my earlier dmesg listing had got the "correct" sound card (at least insofar as it was a Yamaha OPL3-SA3chipset, not the Crystal chipset the NEC docs seemed to suggest).                                                                               

That done, I played around with isapnp, which produced the following in dmesg:

# Card 1: (serial identifier cb 80 86 00 01 30 00 a8 65)
# Vendor Id YMH0030, Serial Number 2156265473, checksum 0xCB.
# Version 1.0, Vendor version 0.0
# ANSI string -->OPL3-SA3 Snd System<--

This actually comes from a post:

[http://www.mailarchives.org/list/debian-user/msg/2004/29890](http://www.mailarchives.org/list/debian-user/msg/2004/29890)

which brought me to the right track.  If you follow the thread you'll see the other guy had similar problems, and was informed he was trying to load the alsa driver (opl3sa2) but that in general he was using OSS; he needed to load snd-opl3sa2.

I tried the same (using snd-opl3sa2) and it worked.

Hope this saves somebody some time...

Ian

---

