---
title: "Hauppauge HVR-1260 drivers"
date: 2015-03-03
forum: Hardware
---

### Post by r 1 on 2015-03-03
Hi! I'm trying to get my Hauppauge working. I've googled all over the place and the only thing I've found is a post on these forums about it with no replies from a year ago. When I run [FONT=Courier New]lspci -vv[/FONT], I see the following:
```
03:00.0 Multimedia controller: Philips Semiconductors SAA7231 (rev aa)
    Subsystem: Hauppauge computer works Inc. Device 0810
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 5
    Region 0: Memory at fa800000 (64-bit, non-prefetchable) [disabled] [size=4M]
    Region 2: Memory at fa400000 (64-bit, non-prefetchable) [disabled] [size=4M]
    Capabilities: <access denied>
```

I've tried the following:
[LIST]
[*][FONT=courier new]modprobe bttv[/FONT][INDENT]doesn't seem to do anything for the card[/INDENT]
 
[*][FONT=courier new]tvtime[/FONT][INDENT]doesn't recognize the card[/INDENT]
 
[*][FONT=courier new]ls /dev | grep video[/FONT][INDENT]doesn't show anything at all[/INDENT]
 
[/LIST]

---

### Post by houstonbofh on 2015-03-04
I am finding nothing on your card, and you may be out of luck.  TV card support is poor at the best of times, and it looks like no one wrote a driver for this card.  It is not listed here.
[http://www.hauppauge.com/pages/faq/support_faq_linux.html](http://www.hauppauge.com/pages/faq/support_faq_linux.html)

And it is not on [http://linuxtv.org](http://linuxtv.org) either.  Closest is [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250)

---

