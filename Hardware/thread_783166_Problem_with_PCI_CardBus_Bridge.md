---
title: "Problem with PCI CardBus Bridge"
date: 2008-05-05
forum: Hardware
---

### Post by m2pc on 2008-05-05
Hey all,

I just installed 7.10 Gutsy on a Dell server.  I'm trying to get my GSM modem to work.  I've installed a PCI PCMCIA carrier board with the ENE chipset in it.  I get this info for it when I run the "lspci -vv" command:

```
01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: ENE Technology Inc CB1410 Cardbus Controller
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 255
        **[COLOR="Blue"]Region 0: Memory at 40020000 (32-bit, non-prefetchable) [disabled] [size=4K][/COLOR]**
        Bus: primary=00, secondary=00, subordinate=00, sec-latency=0
        [B][COLOR="blue"]I/O window 0: 00000000-00000003 [disabled]
        I/O window 1: 00000000-00000003 [disabled][/COLOR][/B]
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt- PostWrite-
        16-bit legacy interface ports at 0001
```

But no lights come on when I insert the GSM modem card into this carrier and the "/dev/ttyUSB0" device for the modem does not exist.

Does the [disabled] (BOLD lines above) mean the card is inoperable? If so, how do I fix it?

I'm setting this up for a friend and it's weeks overdue -- any help would be greatly appreciated!

Thanks in advance.

---

### Post by m2pc on 2008-05-05
Replying to myself, I found this article which seems to address the very same issue under "Cardbus":

[http://www.emmanuelebassi.net/documentation/ubuntu-e6300/#hw-pccard](http://www.emmanuelebassi.net/documentation/ubuntu-e6300/#hw-pccard)

---

### Post by m2pc on 2008-05-06
Ok I tried everything I can think of aside from downloading and installing the sierra.c wireless driver.

Will that help if "modinfo sierra" lists the current driver is the latest?

It seems the main issue is the PCI CardBus adapter card not initializing properly due to a resource allocation issue.  Is there anything else I can try? I'm getting desparate and am ready to format the box and install WinXP on it, which I really _don't_ want to do.

Help!

---

### Post by m2pc on 2008-05-06
Update: I was able to get an IRQ assigned to the card, but the memory is still shown as [disabled]:

```

01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: ENE Technology Inc CB1410 Cardbus Controller
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 19
        [COLOR="Blue"]Region 0: Memory at 40025000 (32-bit, non-prefetchable) [disabled] [size=4K][/COLOR]
        Bus: primary=00, secondary=00, subordinate=00, sec-latency=0
        I/O window 0: 00000000-00000003 [disabled]
        I/O window 1: 00000000-00000003 [disabled]
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt- PostWrite-
        16-bit legacy interface ports at 0001

```

Even after I added this kernel option to my GRUB boot config:

```

title           Ubuntu 7.10, kernel 2.6.22-14-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=737c93c8-9953-43b1-a891-04c07ca4e17f ro quiet splash pci=routeirq [COLOR="blue"]reserve=0x40020000,0x5000[/COLOR]
initrd          /boot/initrd.img-2.6.22-14-server
quiet

```

Anyone? I need a cardbus expert!

---

### Post by m2pc on 2008-05-08
Ok, giving up; I'm going to try installing 8.04 desktop and see if it has better driver support.

---

