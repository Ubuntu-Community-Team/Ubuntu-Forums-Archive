---
title: "No output from internal speakers - headphone jack works ok"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by willy6743 on 2007-09-16
Ok, I just installed Ubuntu, and most everything seems to be working great except I don't have any audio from my internal speakers.  

I tried removing the alsa drivers and using apt-get to install new, but no luck... I even grabbed the latest source for ALSA and compiled that but the same result.  Here is a link to the instructions I followed:

[Comprehensive_sound_problems_guide]("http://72.14.253.104/search?q=cache:IVWQIK5lIeUJ:doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide+Comprehensive_Sound_+Problems_Solutions_Guide&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a")

I am running Ubuntu on a Dell 700m laptop.  Thanks for any help!

lspci output:
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Unknown device 018d
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

---

### Post by staceyofthelamp on 2007-12-20
does your headphone/jack give any sound?

---

### Post by tdeboeser on 2007-12-20
I heard, on a completly different laptop and vid card, that turning off acpi at the kernel helped some people.  

But also what do you see in 'alsamixer' ( open terminal and type alsamixer )?  In 'alsamixer' you'll see a representation of your sound devs.  If you see a "MM" at the bottom of any of the devs, then those devs are muted.  Un-mute them with the "m" key.  

Tom de

---

