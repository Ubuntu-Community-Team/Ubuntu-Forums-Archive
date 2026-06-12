---
title: "Ubuntu on Toshiba Satellite L650-BT2N23"
date: 2010-11-10
forum: Hardware
---

### Post by harris.sw on 2010-11-10
I am new to Ubuntu and was given a Toshiba Satellite L650-BT2N23 that I was hoping to use Ubuntu on.  I installed 10.10 but wifi, the integrated intel graphics, and the SD card reader don't seem to work.  

First I need to get wifi working; from looking around the forums I tried booting from a livecd, but no wifi card seen.  I tried proprietary drivers but none were found. I did an lspci -nn and got the following:

:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

How do I find the right driver?  
Thanks for any help!

---

### Post by irv on 2010-11-10
OK Lets start with the wife. If you can't see the Network icon at the top right of your screen, you might not have a driver loaded.
First, you will need to plug in a Network cable to get on the Internet. Next go to System> Administration> Additional Drivers. It will search for your hardware and list the driver(s) to select from. Pick the right driver. After it installs you should be able to disconnect the cable and it should find your wifi.
You might even see the other drivers you need for the other hardware when you do this. I am not sure on this one. But if you can find them in the list of drivers go ahead and select them for install.

---

### Post by harris.sw on 2010-11-10
Thanks for the quick reply!  I tried that, it searched for a bit, but did not find any additional drivers to install for any of the missing devices.

---

### Post by irv on 2010-11-10
> **harris.sw said:**
> Thanks for the quick reply!  I tried that, it searched for a bit, but did not find any additional drivers to install for any of the missing devices.

Sorry this didn't help, It worked on my Dell Inspiron 1521 and thought It was worth trying on you Toshiba. I am not sure about your hardware so I can't help at this point but maybe someone else can jump in here. Good luck in getting it going.

---

