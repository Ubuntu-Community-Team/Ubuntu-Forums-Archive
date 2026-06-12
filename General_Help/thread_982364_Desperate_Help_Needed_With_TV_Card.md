---
title: "Desperate Help Needed With TV Card"
date: 2008-11-14
forum: General Help
---

### Post by jlacroix on 2008-11-14
I have an MSI Tuner TV@nywhere Plus card on a machine that dual boots Windows XP and Ubuntu 8.10.

More info on the card I have is here:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127988](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127988)

Under Windows everything works fine (even though the bundled TV software sucks). Under Ubuntu 8.10 using TVTime I get picture, but no sound. I've checked all the sliders especially the one for line-in, which is what the card uses.

This TV card even comes with a remote, but of course that doesn't work in Ubuntu either.

I need to figure out why I don't get sound out of it and why the bundled remote doesn't work.

Here is the output from lspci that may give some information:
```
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
01:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)

```

---

### Post by jimmy the saint on 2008-11-14
A quick google search seems to indicate that a lot of people are having issues with this card, and a bug has been filed about the remote.  It may be that the card is either too new, or that the hardware is obscure.  Either way, it does not seem that linux drivers have made it into the kernel yet.

---

### Post by jlacroix on 2008-11-14
> **jimmy the saint said:**
> A quick google search seems to indicate that a lot of people are having issues with this card, and a bug has been filed about the remote.  It may be that the card is either too new, or that the hardware is obscure.  Either way, it does not seem that linux drivers have made it into the kernel yet.

I don't understand, if the drivers haven't made it in Linux, than why does the video work perfect? One of the reviews for this card mention that everything works out of the box in Ubuntu so it can't be a global issue.

---

