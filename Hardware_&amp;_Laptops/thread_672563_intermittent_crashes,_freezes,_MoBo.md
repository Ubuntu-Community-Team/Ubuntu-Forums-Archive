---
title: "intermittent crashes, freezes, MoBo?"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by ewy on 2008-01-19
My HP Compaq nx6130 is over two years old. I'm pretty sure I've overheated it a few times (blocked the vent by leaving it on cloth surfaces, etc). About 8 months ago it started crashing occasionally under WinXP, and would not reboot -- the power would come on but after a few seconds would die again, or just remain suspended on a black screen after the BIOS loaded fine).

I reinstalled WinXP Pro, and took the opportunity to set up a dual boot system with Ubuntu 7.10. Both seemed to work fine (Ubuntu needed a lot of tweaking) and they ran ok.

Recently I installed some new RAM, which checked out fine, and cleaned out the fan -- this helped with system stability and heat IMMENSELY, or so it seemed. In the last few weeks the system has started to freeze up again: 

In XP, it would load up to the Windows XP splash screen (with the blue boxes moving around) but would freeze before the logo was fully lit. This did not happen on every boot, just sometimes.

In Ubuntu, the most common cause of a freeze would be plugging in a network cable to the ethernet jack -- regardless of whether or not the cable's other end was connected to anything.

I got fed up with this inconsistency, wiped the hard drive, and installed Ubuntu 7.10 only. It showed the same freezing problems, and in addition it would freeze sometimes during boot -- an endless loop of ohci1394 fw-host0 transmit failures. I discovered through trial and error that holding the power button on the case down for a few seconds, but not the full 8 required to shut down, would break this endless loop and allow Ubuntu to continue loading.

I have since wiped the hard drive again, reinstalled XP as the sole OS, and tested both the Fujitsu hard drive (no problems) and the memory (memtest86+ ran for 13 hours without finding anything wrong). 

When checking out my system using the PCI program on the Universal Boot CD, I noted the following unexpected output:

ROM PCI IRQ routing table checksum 00h
ROM PCI IRQ routing table appears to be faulty!

I have no idea if this is relevant. After installing all the HP patches I could find from their website, I'm now at a point where XP system doesn't seem to freeze very often. However, I tried running GParted from the Ubuntu 7.10 Desktop CD, and it froze while I was setting options (I can still move the mouse, but Ctl+Alt+F1 and Ctl+Alt+Bksp, etc have no effect).

I still have two remaining problems: 
1. In XP, occasionally when I touch my keyboard after being away from the computer, a static discharge occurs and the system immediately reboots. This did not happen for the first two years I owned the laptop, but now it is predictable and repeatable.
2. I can't really use Ubuntu 7.10 despite what I try, including the Desktop CD. It consistently and inevitably freezes in the first five minutes of use.

I'm currently burning the Ubuntu 7.04 CD so I can try GParted from that, but I'm not holding out any hope. The situation looks dire.

I fear I have a motherboard problem, but I don't know where to start to diagnose this issue. Any help would be greatly appreciated. 

TI OHCI compliant IEE-1394 FireWire Controller
ATI Mobile Radeon X300 64MB
Intel 82801FB(ICH6)AC'97 Audio Controller
Inet Pro/Wireless 2200BG
Broadcom BCM5705MA2 NeXtreme Gigabit Ethernet
Texas Instruments PCIxx21/x515 Cardbus Controller
MoBo: HP Model 0A0C (KBC Version 51.02) Chipset 82915PM/GM/GMS, 82910GML Host Bridge

Cheers.

---

### Post by Yellow Pasque on 2008-01-19
Some things to try:
- Reseating your RAM and only using one stick
- Disabling components (audio, LAN, Firewire, USB, etc.) in the BIOS and seeing if that helps.

---

### Post by ewy on 2008-01-20
My BIOS doesn't allow me disable anything but Bluetooth and wireless capabilities.... is there any other way to disable these so they don't trip up the system?

I will try the RAM swapping, thanks.

---

### Post by Yellow Pasque on 2008-01-20
Unfortunately, if your BIOS doesn't support disabling the hardware, it's going to be a lot tougher to disable it. You could try blacklisting the appropriate modules in the /etc/modprobe.d/blacklist file. For example, to disable usb, you could blacklist usbcore, usbhid, ehci_hcd, and ohci_hcd.

Then again, it may be easier just to boot into "recovery mode" and seeing if you have a freeze-up there.

---

