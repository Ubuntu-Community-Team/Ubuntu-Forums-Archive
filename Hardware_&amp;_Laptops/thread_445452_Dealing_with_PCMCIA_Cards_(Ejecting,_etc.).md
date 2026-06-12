---
title: "Dealing with PCMCIA Cards (Ejecting, etc.)"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by Jamie Jackson on 2007-05-15
I don't know how to work with PCMCIA cards. How do I safely remove them? How do I see their status? Does hotplugging work? Etc., etc..

Thanks,
Jamie

P.S. I'm using Feisty

---

### Post by DarkN00b on 2007-05-16
It may depend on the function of your card. My wireless network card is hotpluggable for example.

---

### Post by Jamie Jackson on 2007-05-16
Thanks. 

Is there some command/GUI that I can run to verify that the machine's aware of the card?

Thanks,
Jamie

---

### Post by DarkN00b on 2007-05-16
> **Jamie Jackson said:**
> Thanks. 

Is there some command/GUI that I can run to verify that the machine's aware of the card?

Thanks,
Jamie

What kind of card is it? Network, memory card reader...? What brand? 

Plug in the card and type ```
lspci
``` into a terminal and look at the output. It helps if you maximize the terminal screen -- makes that mess easier to read. The last line should be your pcmcia card. If you can't find it, post the output here and I'll try to help. It should be readily apparent though.

---

### Post by Jamie Jackson on 2007-05-16
It's a Linksys WPC11 v.3 Wireless card, and here are a few commands I think are interesting:
1. An lspci that doesn't show the card, as far as I can tell
2. An ifconfig, showing the card at eth2
3. An AP scan, which does show APs

```
jamie@satubuntu:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 Ethernet controller: 3Com Corporation 3c555 Laptop Hurricane (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 CardBus bridge: O2 Micro, Inc. OZ6836/6860 CardBus Controller (rev 62)
00:09.1 CardBus bridge: O2 Micro, Inc. OZ6836/6860 CardBus Controller (rev 62)
00:0a.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
06:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)
06:00.1 Serial controller: Xircom Cardbus Ethernet + 56k Modem (rev 03)

jamie@satubuntu:~/Desktop$ ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 00:06:25:11:32:2F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:400 (400.0 b)
          Interrupt:3 Base address:0x100 

jamie@satubuntu:~/Desktop$ iwlist eth2 scan
eth2      Scan completed :
          Cell 01 - Address: 00:18:39:CE:0C:73
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:14/153  Noise level:16/153
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:15:E9:7F:84:04
                    ESSID:"jackson"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:72/153  Noise level:17/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 03 - Address: 00:15:E9:7F:84:04
                    ESSID:"jackson"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:72/153  Noise level:17/153
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

```

---

### Post by Jamie Jackson on 2007-05-16
pccardctl seems to be the command I was looking for.

Thanks,
Jamie

---

