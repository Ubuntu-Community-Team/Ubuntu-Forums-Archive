---
title: "Power off USB ports on system shutdown?"
date: 2014-02-20
forum: Hardware
---

### Post by Olav on 2014-02-20
Hello, I just built a new desktop computer using an Asus M5A78L-M/USB3 motherboard with an AMD FX6300 CPU. I am running Xubuntu 13.10 on it. Everything is working really nicely. Except I noticed that the USB ports keep supplying a voltage even after I shutdown the system. This seems undesirable to me and it was not the case with my previous computer. I would prefer it if no USB devices were leeching power while the computer is off, while still being able to turn on the computer (and everything attached) remotely through Wake-on-LAN.

I also have a power strip that I like to use, which works with a USB controlled relais. In the present state it obviously does not power off my other peripherals (monitor, amplifier, desk lamp...) without manually flipping the switch. Which makes it sort of useless, unfortunately.

Shouldn't it be possible to cut power to all the USB ports on shutdown? Or even, to determine for each port individually whether it should remain powered or not? There is no option that I can find in the BIOS system settings to accomplish this. Does anyone know how I can do this from within the operating system?

I am not afraid of the command line or of scripting or changing configuration files. However I am quite unsure where to even start at this point.

Any pointers will be appreciated.

---

### Post by tgalati4 on 2014-02-20
Newer computers leave one or more USB ports powered so you can charge your phone.  It's a convenience.  Normally there would be a BIOS switch to turn that feature on or off.  There is a tool to do that called *acpitool*.  If you are not afraid of the terminal:

```
sudo apt-get install acpitool
acpitool -w
```

Anything "enabled" will have power to it during S3 or S4 sleep.  You can shut off parts of the bus with the -W switch and the number of the device from the above command.

This is especially helpful for Wake-on-Lan, because you need to leave power to the PCI bus that is connected to the ethernet card, otherwise the card won't wake up the system.  If you turn too many things off, your system won't wake at all, so take notes and only change one item at a time and note the behavior.

My USB ports stay powered during sleep:

tgalati4@Mint14-Extensa ~/Desktop $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID0	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. HDEF	  S3	*disabled  pci:0000:00:1b.0
  4. PXSX	  S5	*enabled   pci:0000:02:00.0
**  5. USB1	  S3	*enabled   pci:0000:00:1d.0**
  6. USB2	  S3	*enabled   pci:0000:00:1d.1
  7. USB3	  S3	*enabled   pci:0000:00:1d.2
  8. EHC1	  S3	*enabled   pci:0000:00:1d.7

If I want to shut off USB1:

```
sudo acpitool -W 5
```

To learn more about acpitool:

```
man acpitool
```

Spacebar to page forward, "q" to quit.

Proceed carefully.

---

### Post by Olav on 2014-02-21
Thank you for your reply. I tried the acpitool as you described, unfortunately it does not do what I am after. The USB ports remain powered on after shutdown regardless of the settings I did with the tool. It makes sense I guess, because the -w option of the tool manages the capability to wake the system up through the ports, not (necessarily) their power status.

Since yesterday I have googled some more and discovered that it is something that more people are struggling with, but there appears to be no real solution in the current kernels.

I will investigate further, meanwhile if you or someone else has another idea that would be great of course.

---

