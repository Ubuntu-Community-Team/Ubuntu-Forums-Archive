---
title: "WLAN don't work on laptops without wlan switch"
date: 2009-12-30
forum: Hardware
---

### Post by giacos73 on 2009-12-30
Hello!

It seems that the wlan framework don't work well with older laptops that don't have a wlan switch to enable/disable the wlan.
I'm using Ubuntu 9.10...

I have a ASUS L5800C with a Broadcom 4301 chip
rfkill reports the following:
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

After pressing Fn-F2 on the keyboard it changes to:
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

I'm unable to switch the "Hard blocked" to "no". So the b43 driver show's the following messages in the dmesg (see the "Radio hardware status changed to DISABLED" line!):

[    1.846521] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.839015] b43legacy-phy0: Broadcom 4301 WLAN found
[   20.901965] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[   20.901988] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[   20.924247] b43legacy-phy0 debug: Radio initialized
[   21.352091] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   21.510986] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   21.519951] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   21.652897] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   21.710532] b43legacy-phy0 debug: Chip initialized
[   21.710817] b43legacy-phy0 debug: 30-bit DMA initialized
[   21.716509] b43legacy-phy0 debug: Wireless interface started
[   21.716524] b43legacy-phy0 debug: Adding Interface type 2

[   26.816069] b43legacy-phy0: Radio hardware status changed to DISABLED

[   26.816080] b43legacy-phy0 debug: Radio initialized
[   26.816143] b43legacy-phy0 debug: Removing Interface type 2
[   26.816245] b43legacy-phy0 debug: Wireless interface stopped
[   26.816357] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 1/64
[   26.816404] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[   26.816456] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[   26.825178] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[   26.832085] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[   26.840082] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[   26.848095] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 2/128
[   26.858263] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[   26.865585] b43legacy-phy0 debug: Radio initialized
[   26.865604] b43legacy-phy0 debug: Radio initialized

Is there any way or patch for this issue !?

Thanks

---

### Post by giacos73 on 2009-12-30
... I'm using Ubuntu 9.10, updated today (30.12.2009)!

---

### Post by giacos73 on 2010-01-02
Hi!

Is there somebody? What's wrong with my question, that no one want to answer? :confused:

Don't tell me, that i have to install windows on my old laptop for wlan capability !

---

### Post by IcarusR on 2010-01-02
The reason why nobody has replied is that no one has anything positive to add on this subject !!

---

### Post by giacos73 on 2010-01-03
I have found the "solution" myself.

The solution was to recompile the kernel without RFKILL option.

Maybe in the future there is a better way...

---

### Post by strk on 2010-02-20
Hi giacos73, I have the same laptop and same problem since I upgraded
kernel to 2.6.30,31,32.
This thread may be of interest for you:
[https://lists.berlios.de/pipermail/bcm43xx-dev/2010-February/006928.html](https://lists.berlios.de/pipermail/bcm43xx-dev/2010-February/006928.html)

I still haven't tried the compile-time disabling of rfkill (doing next).

---

### Post by strk on 2010-03-19
Well, I tried disabling rfkill in kernel but still no luck

---

### Post by jasonkirk2006 on 2010-03-22
> **giacos73 said:**
> I have found the "solution" myself.

The solution was to recompile the kernel without RFKILL option.

Maybe in the future there is a better way...

Hi;

I've been suffering from the same thing. How did you manage to recompile the kernel without RFKILL option? Would you please give some detail?

---

### Post by mandyb on 2010-03-23
With a Broadcom 4306 mini-PCI card I had success masking pins 11 & 13 with cellophane tape.  Now always on in a laptop that has no hardware switch.

---

### Post by Harpette on 2010-04-22
I'm having the same problem on an HP Pavilion zx5000 equipped with a BCM4303 rev. 2.
The laptop has a toggle switch to disable wireless, but it is useless in Linux (Xubuntu 9.10): its light remains off, confirming that the wireless network adapter is indeed turned off.
When running Windows, wireless works upon boot-up, and that switch works too, if i choose to use it.

---

