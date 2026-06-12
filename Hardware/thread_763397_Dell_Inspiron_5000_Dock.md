---
title: "Dell Inspiron 5000 Dock"
date: 2008-04-23
forum: Hardware
---

### Post by Gumby1234 on 2008-04-23
Sorry but I am a total newb to linux so sorry if this is in the wrong place or whatever....anyway I have a Dell Inspiron 5000 and it has no ethernet port, I also have the dock for the laptop which does have an ethernet port but when i dock it, Ubuntu doesn't realize it so i can't get a network connection with it at all. Any thing helps, Thanks.

---

### Post by overdrank on 2008-04-23
> **Gumby1234 said:**
> Sorry but I am a total newb to linux so sorry if this is in the wrong place or whatever....anyway I have a Dell Inspiron 5000 and it has no ethernet port, I also have the dock for the laptop which does have an ethernet port but when i dock it, Ubuntu doesn't realize it so i can't get a network connection with it at all. Any thing helps, Thanks.

Hi and welcome, I am by no means a network expert but you may start with the command in the terminal ```
lspci
``` the terminal is located under applications, accessories. You can post the out put here and we can help locate your hardware.

---

### Post by Gumby1234 on 2008-04-23
> **overdrank said:**
> Hi and welcome, I am by no means a network expert but you may start with the command in the terminal ```
lspci
``` the terminal is located under applications, accessories. You can post the out put here and we can help locate your hardware.

Ok I did that and got this:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03) 
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) 
00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01) 
00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01) 
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02) 
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) 
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) 
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03) 
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10) 
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 08) 
00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01) 
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) 

Thanks!

---

