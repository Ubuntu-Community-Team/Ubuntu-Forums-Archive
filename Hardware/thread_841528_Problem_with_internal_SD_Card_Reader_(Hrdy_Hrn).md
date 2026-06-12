---
title: "Problem with internal SD Card Reader (Hrdy Hrn)"
date: 2008-06-26
forum: Hardware
---

### Post by Chillax on 2008-06-26
Alright, here's the lowdown:

I've got a Toshiba Satellite M35-S359 and am running an Hardy Heron/XP dual boot (Ubuntu is what I mostly use, though. XP is for games).

Everything works great (minus all the partitioning I had to do, when I upgraded my HD), the only problem I've got is that my SD card reader doesn't work on my Ubuntu partition. 

**It works fine on my XP partition.**

It's really frustrating and I cannot, for the life of me, figure out what's wrong. I'm sure that if I knew more about Shell and whatnot, I could fix the problem myself but I haven't had the time to learn the needed commands/procedures to even begin to know what's going on.

Any help would be greatly appreciated.

---

### Post by jualin on 2008-06-26
Welcome to the forums and welcome to Linux in general. Post the results of > lspci on the terminal and then you will get the exact model of your SD Card Reader and maybe we can figure something out. Greetings from Miami, FL

---

### Post by Chillax on 2008-06-26
Thank you, so much, for deciding to help me out! Here's the readout from the lspci command:

```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0a.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)

```

---

### Post by jualin on 2008-06-26
**Toshiba America Info Systems SD TypA Controller** is your SD Card reader.
Apparently this is a bug which has been [reported]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/88863") on launchpad. From what I have read Linux doesn't support that SD Card Reader. Sorry pal

---

### Post by stchman on 2008-06-26
Just get a USB xD/SD adapter.  They are like $6 shipped off ebay and they work great.

My Toshiba laptop has a Ti 5 in 1 reader and SD cards work but xD cards do not.

---

