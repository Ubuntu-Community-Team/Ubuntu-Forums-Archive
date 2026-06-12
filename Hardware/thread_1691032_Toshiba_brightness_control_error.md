---
title: "Toshiba brightness control error"
date: 2011-02-19
forum: Hardware
---

### Post by aditosh on 2011-02-19
Hi, I have a Toshiba C650 - I5011 model with Ubuntu 10.3 . I have a problem that even after pressing the Fn + F6 key, the brightness of my LCD does'nt change. 
It remains at maximum.

I have installed both Toshutils and hotkey daemon. My volume control key (on numeric alternate) works perfectly fine but none of the Function keys (on which brightness control is located) work. Pls help.
Also, I had errors during installation of Ubuntu on my laptop because of which I had to permanently disable ACPI, else it won't boot. Following is the lspci output :


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by jerrrys on 2011-02-20
i do not own a Toshiba C650, but found this interesting, has to do with acpi

[http://art.ubuntuforums.org/showthread.php?p=10225707](http://art.ubuntuforums.org/showthread.php?p=10225707)

found that here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+C650+brightness+control&as_qdr=all&sa=Google+Search&lang=en#971](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+C650+brightness+control&as_qdr=all&sa=Google+Search&lang=en#971)

a wider search yields this

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+C650&as_qdr=all&sa=Google+Search&lang=en#855](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+C650&as_qdr=all&sa=Google+Search&lang=en#855)

---

