---
title: "Intel integrated cards. Any drivers ?"
date: 2005-09-20
forum: Hardware &amp; Laptops
---

### Post by weasel fierce on 2005-09-20
Are there any drivers I should be looking for, regarding an integrated intel video card ?

---

### Post by er4z0r on 2005-09-20
[QUOTE=weasel fierce]Are there any drivers I should be looking for, regarding an integrated intel video card ?[/QUOTE]

Well, what exactly do you want from the card? Just a working X-Server or Hardware-Acceleration?

What kind of Videocard do you have?
Try running lspci -v and look for VGA.

Hope I could help

---

### Post by weasel fierce on 2005-09-20
Intel Corp. 82845G/GL[Brookdale-G]/GE

Mainly I want to get whatever acceleration out of it, that I may be able to, untill I can afford a proper card :)

---

### Post by copilot on 2005-09-27
I'm using the same chipset..
0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA])
        Subsystem: Intel Corp.: Unknown device 4c59
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 1
and I can't manage to get it to do anything more than 640x480@60hz. I'm using a Samsung Syncmaster 710n as my monitor and it would be really nice to get it to work at a higher resolution. Thanks in advance for any help anyone has to give. =)

---

### Post by John.Michael.Kane on 2005-09-27
It would seem this is going to be the last driver for the video chipset you listed 
[http://support.intel.com/support/graphics/intel845g/](http://support.intel.com/support/graphics/intel845g/)
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

Hope this helps

---

