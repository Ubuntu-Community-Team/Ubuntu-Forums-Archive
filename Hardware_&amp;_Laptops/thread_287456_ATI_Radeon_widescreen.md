---
title: "ATI Radeon widescreen"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by don_kostone on 2006-10-28
Hi,

I'm trying to set up my compaq laptop ( compaq presario x1000) running with Ubuntu 6.06 to use dual head desktop. My LCD works on 1280x800 and when I install the driver provided by ATI the LCD doesn't works properly. The whole display is blinking and there is no clear picture at all. With the generic drivers it work's fine, but I can not set up my TVout and CRT output correctly. Please give me any information about running ATI RADEON with ATI drivers with widescreen resolution. Is it also possible to configure my LCD with 1280x800 and the CRT at 1024x768 at the same time with the generic drivers. 

Here is information about my hardware:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation: Unknown device 0860
        Flags: bus master, stepping, 66MHz, medium devsel, latency 128, IRQ 10
        Memory at 98000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at 90400000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at 90420000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
        Capabilities: [50] Power Management version 2

root@compaq:~# atitvout -r vbe
Forcing Radeon/Rage 128 mode
VBE Version: 2.0
VBE OEM Identification: ATI MOBILITY RADEON 9200
root@compaq:~#

root@compaq:~# uname -a
Linux compaq 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux
root@compaq:~#


Excuse me if this is discussed already, but I'm new to the forum.

Thanks

Ivan****

---

### Post by pmaxv on 2006-11-05
This guide would do:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

