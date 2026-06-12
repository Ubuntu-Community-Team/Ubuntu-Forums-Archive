---
title: "AC'97 Audio Controller no driver"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by linbie on 2006-10-31
Dear all,

When i installed my ubuntu (6.06) fresh from the cd, my sound card is working. However, now it doesn't work anymore as i have upgraded the system to the latest packages (it popped up from the panel as a red asterisk asking to update). 

I do not know where to start or how to troubleshoot, please help. 
Anyway i found this link [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound).

I followed until step3 and went to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)  to find a compatible driver. My chipset is ICH4, but i cannot click on it (as it is not a hyperlink), does that mean the driver does not exists?

lspci -v, gives me this:
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/IC H4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM: Unknown device 0554
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at d0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at d0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

If anyone could be so kind to guide me where/how to start.
Thanks !!

---

