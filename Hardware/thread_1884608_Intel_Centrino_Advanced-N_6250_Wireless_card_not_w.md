---
title: "Intel Centrino Advanced-N 6250 Wireless card not working on HP DV74285dx"
date: 2011-11-21
forum: Hardware
---

### Post by toccovender on 2011-11-21
Wireless card won't work, only way to access the internet with it is by using the Belkin wireless USB adapter I have. 
I just installed Ubuntu 11.10 64-bit, was a little bit of a rough install but everything turned out all right.
Thanks in advance for the help!
Here's some terminal information I've seen people asking for in other threads.
```
robert@robert-HP-Pavilion-dv7-Notebook-PC:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Robson CE [AMD Radeon HD 6300 Series] [1002:68e4]
01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0089] (rev 57)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
7f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
7f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
7f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
7f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
7f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
7f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
robert@robert-HP-Pavilion-dv7-Notebook-PC:~$ lsmod | grep intel
intel_ips              18089  0 
robert@robert-HP-Pavilion-dv7-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by trundlenut on 2011-11-21
HP have a habit of restricting the wireless cards that can be used in their laptops.  There is a whitelist within the bios, if the card doesn't match an entry on the list it won't work and either the machine will stop at post with an error message or just not recognise the card at all.

I have an HP laptop I bought from ebay, someone had put a Intel Wireless N card in it and the machine refused to admit is was there, I bought an original acceptable card of ebay and swapped and voila, it worked.

Your best choice is to use a whitelisted card, otherwise you are looking at modifying the card or the bios.

---

### Post by toccovender on 2011-11-21
The card works just fine for Windows 7 though.
I forgot to mention that I dual boot Win7 and Oneiric.

---

### Post by toccovender on 2011-11-23
Also forgot to mention - the wireless card was working during install, but stopped once I rebooted after install.

---

