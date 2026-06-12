---
title: "Virtual Consoles (Ctrl-Alt-F(1-6)) broken in Intrepid Ibex"
date: 2008-11-18
forum: General Help
---

### Post by Altay_H on 2008-11-18
After installing Intrepid Ibex I no longer can use the six virtual consoles. To clarify, I can switch to them and I think they're working correctly, but I cannot actually *see* any text on the screen. The screen is black, and about once every ten seconds (inconsistently) displays what it should in a single flash. This makes it difficult to use them, because commands like ls are completely useless, and I can't see if I make a mistake. Any ideas?


Here's my lspci:
```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I'm not sure, but my only thought is that my graphics card driver could be the problem. I'm using an ATI Radeon XPRESS 200M with the FGLRX driver, which I know isn't flawless in Linux.

---

### Post by Altay_H on 2008-11-24
Bump.

I'm still having this problem.

---

### Post by MorphWVUtuba on 2008-12-02
I'm having this problem too.

Any luck finding a solution?

---

### Post by Altay_H on 2008-12-11
Unfortunately not. What I find strange is that I installed Intrepid Ibex on a separate partition of my hard drive, but I recently noticed that my Hardy Heron partition has the same problem. My only guess is that it's graphics card related.

What graphics card and driver are you using?

---

### Post by Altay_H on 2008-12-20
Bump.

Still having this problem.

---

### Post by zman58 on 2008-12-20
Could it be a problem of your monitor not supporting the mode that the tty* console requires? Try using an older multi-syncing CRT monitor if you have one lying around.

---

### Post by Altay_H on 2008-12-20
> **zman58 said:**
> Could it be a problem of your monitor not supporting the mode that the tty* console requires? Try using an older multi-syncing CRT monitor if you have one lying around.
This problem exists on a laptop, so I'd be surprised if it's the monitor. Especially because it worked before upgrading to Intrepid. I do happen to have an old CRT monitor, so I'll give it a try. Could you explain how I can tell whether or not it's multi-syncing? Are all CRT monitors multi-syncing, or must the monitor be both CRT and multi-syncing?

A small update: I tried disabling my graphics card driver (FGLRX) to see whether or not that would solve my problem. It did not.

---

### Post by zman58 on 2008-12-22
CRT monitors, particularly higher end units, tend to be very flexible in supporting many different modes of operation (text and/or graphic). They can automatically sync to any of the modes they support (multisyncing). I have noticed that some of the LCD monitors I have worked with tend to be more limited as to what specific text or graphic modes they support--they typically do not handle the wide range that the CRT does. But since you are running on laptop, you are probably not using analog VGA port, so syncing is probably not your problem.

One other thought that came to mind is to try disabling any desktop acceleration. That is "Preferences - Appearance - Visual Effects" set to "none". Sometimes the desktop acceleration interferes with switching between screen sessions. --I have seen this in the past.

---

### Post by Altay_H on 2008-12-22
> **zman58 said:**
> One other thought that came to mind is to try disabling any desktop acceleration. That is "Preferences - Appearance - Visual Effects" set to "none". Sometimes the desktop acceleration interferes with switching between screen sessions. --I have seen this in the past.
I'd try this, except that I already keep visual effects on none.

I just tried hitting Ctrl+Alt+F1 again, and it worked. I think it's because I recently rebooted after disabling my graphics card driver. I'm going to try enabling it again and see if the problem returns.


Update:
Yes, the problem is with my graphics card driver (FGLRX). Disabling it causes my Virtual Consoles to work perfectly, and enabling it causes them to mess up again. Should I submit a bug report?

---

### Post by lowtolerance on 2008-12-22
I'm having the same problem with the nonfree nvidia driver.

---

### Post by Altay_H on 2008-12-23
> **lowtolerance said:**
> I'm having the same problem with the nonfree nvidia driver.
Which version are you using? I have a laptop using the nonfree nvidia driver version 177 and it doesn't have this problem.

---

### Post by lowtolerance on 2008-12-26
> **Altay_H said:**
> Which version are you using? I have a laptop using the nonfree nvidia driver version 177 and it doesn't have this problem.

That's the same version I'm using. It's broken for me in 32-bit and 64-bit Intrepid. It doesn't really bother me, as I'd just as soon use a windowed terminal, but it has always worked in the past.

*EDIT:* Recently upgraded to the beta NVidia driver(180.xx), and I can confirm that the problem still persists.

---

### Post by nour214 on 2009-03-16
on my pc i have intell drivers and i'm having the same problem with my virtual consoles on ubuntu 8.10

here is a copy of my lspci
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:01.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

```

---

### Post by Altay_H on 2009-03-16
I can confirm that a similar problem exists with Arch Linux, so this problem might not be exclusive to Ubuntu. I'm not sure if it's related, but sometimes when I switch to the virtual console in Arch Linux the screen will simply black out. Switching between virtual consoles repeatedly sometimes solves the problem, but other times I'm required to either type "sudo reboot" followed by my password and hope it works or press and hold the power button.

---

### Post by nour214 on 2009-03-27
my problem has been fixed, all i did was update my linux kernel and my virtual consoles work fine.

---

### Post by Altay_H on 2009-03-29
I just upgraded and it seems to be fixed for me as well. Looks like kernel 2.6.27-11 solved this problem. :)

---

