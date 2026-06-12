---
title: "Wireless No Worky On Asus G73"
date: 2010-10-04
forum: Hardware
---

### Post by giddyup306 on 2010-10-04
Hello, 

I just bought said laptop, and as I anticipated, I'm having wireless problems.  I'm running 10.04 on this one.  I didn't find a single thing by searching on this forum, but I did find a little bit on a Gentoo forum (which didn't work).  The wireless light is on, but it just shows the wireless as being disabled.

If this is going to be hard to do, can you suggest a USB adapter?

I found this one on ebay...

[http://cgi.ebay.com/500mw-USB-Wireless-300M-802-11N-WIFI-adapter-OSX-Linux-/320588282863?pt=LH_DefaultDomain_0&hash=item4aa48cfbef](http://cgi.ebay.com/500mw-USB-Wireless-300M-802-11N-WIFI-adapter-OSX-Linux-/320588282863?pt=LH_DefaultDomain_0&hash=item4aa48cfbef)

I already have to use a USB mouse since the touch pad is way too sensitive.

OT I'm pretty disappointed in this computer.  The first one wouldn't load Win 7, or even boot off the DVD drive...

Thanks!

---

### Post by giddyup306 on 2010-10-05
ttt

---

### Post by Dark_Stang on 2010-10-05
What kind of wireless card is in your machine? Post the output of "lspci" if you don't know.

---

### Post by giddyup306 on 2010-10-06
Intel Corporation WiMAX/WiFi Link 6050 < - I'd assume this is the one?

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68a0
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
03:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 57)
04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

---

### Post by giddyup306 on 2010-10-06
I think I found a firmware update!

[http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)

Which one do I want, and how do I install it?

---

### Post by Dark_Stang on 2010-10-06
You probably just need to update your drivers. You can download and install the latest wireless drivers from here.
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by giddyup306 on 2010-10-06
So which one do I need, and how do I install/update it?

---

### Post by Dark_Stang on 2010-10-08
I would just download the bleeding edge ones. There are instructions further down the page for installing it.

---

### Post by giddyup306 on 2010-10-11
I upgraded to Manic Monkey 10.10, and now it works!!! :guitar:

---

