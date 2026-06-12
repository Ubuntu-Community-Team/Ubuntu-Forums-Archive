---
title: "WinTV PCI not working"
date: 2010-04-12
forum: Hardware
---

### Post by sandrocchio_0.1 on 2010-04-12
I recently wanted to set up a media station based on Ubuntu 9.10
So far I've been only focusing on hardware components, I found two PCI tv cards in my dad's garage and I decided to give a try.
They're both Hauppage cards, one is an Hauppage 9002 which only has the input plug and from the system log seems to be recognized correctly, the other which doesn't work has the output as well and is a WinTV PCI (not sure about the model).

My question is: how and/or where can I find details on this card chipset and possibly evidence about the problem. I assume the driver is missing.

Thanks in advance

---

### Post by coffeecat on 2010-04-12
With the card in a PCI slot, do a 'lspci' in a terminal. This should give you details of the chipset. Even with the same model number, Hauppage have used different chipsets at different times, or for different markets. If you get something like...

```
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```...the fix should be easy (hopefully). (That's the lspci output for my Hauppage WinTV Nova TV-500, by the way.) For that chipset you need to install the package linux-firmware-nonfree for it to work properly. Others have the Dibcom dib7*** chipsets, for which the firmware is free and comes in a default install. So it will be interesting to see if yours is a Philips one.

---

### Post by sandrocchio_0.1 on 2010-04-15
> **coffeecat said:**
> With the card in a PCI slot, do a 'lspci' in a terminal. This should give you details of the chipset. Even with the same model number, Hauppage have used different chipsets at different times, or for different markets. If you get something like...

```
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```...the fix should be easy (hopefully). (That's the lspci output for my Hauppage WinTV Nova TV-500, by the way.) For that chipset you need to install the package linux-firmware-nonfree for it to work properly. Others have the Dibcom dib7*** chipsets, for which the firmware is free and comes in a default install. So it will be interesting to see if yours is a Philips one.

Thanks "coffecat"
this is my out put

```
lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

05:04.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)

05:09.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:09.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
05:09.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
```looks like I have at least a Philips card, I installed the linux-firmware-nonfree package just in case.
Now I am looking at Kaffeine, under television settings, it shows 2 tab, each for tv interface
1. Conexant CX22702 DVB-T
2. ST STV0299 DVB-S
I am able to perform a channel search, but as I do not have a proper antenna plugged I guess I am unable to catch anything. I would like to focus on TV out for the moment which still doesn't work.
I'll try to find something on the Internet, but so far I haven't a clue on why it doesn't work.
Thanks for now.

---

