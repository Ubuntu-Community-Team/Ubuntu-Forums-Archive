---
title: "TV tuner"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by ddover on 2007-04-04
ubuntu 7.04 all new updates
mythtv .20 fixes
pchdtv 5500

I am able to load the card and watch Standard Def with no problem. However, I can not load it for High Def. The problem is that it can not be detected as a dvb card

I found someone with the same problem and I think they did a better job at explaining the problem 


"The card chipset is detected and the modules load apparently correctly. However, the /dev/dvb/adaptor directory is not created as it should be. Rather, a /dev/.static/dev/dvb/adaptor is created with the correct devices for this card. So, no apps can use the card because the devices don't exist in /dev/dvb"

[http://ubuntuforums.org/showthread.php?p=1859204](http://ubuntuforums.org/showthread.php?p=1859204)

Unfortunetely no one was able to answer that users question. If anyone could offer me some advice it would be truly appreciated.

Danny

---

### Post by newlinux on 2007-04-04
I have dvb cards that don't create /dev/adapterx that worked fine in myth. I used to have a pchdtv 5500 and I think it behaved the same way. Did you set the card up as a dvb card or as a pchdtv card in myth?  what does dmesg output about this card?

---

### Post by ddover on 2007-04-04
When I set it up as a pchdtv card in mythtv and it only works in SD. On Fedora Core 5 when i set it up as DVB it works as HD. On my current ubuntu system in myth it says it can't be probed. Here is the output from dmesg

[   26.472083] CORE cx88[0]: subsystem: 7063:5500, board: pcHDTV HD5500 HDTV [card=47,autodetected]
[   26.472089] TV tuner 64 at 0x1fe, Radio tuner -1 at 0x1fe
[   26.597489] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   26.597533] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   26.600156] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[   26.600199] tuner 1-0061: type set to 64 (LG TDVS-H06xF)
[   26.600202] tuner 1-0061: type set to 64 (LG TDVS-H06xF)
[   26.645717] cx88[0]/2: cx2388x 8802 Driver Manager
[   26.645742] ACPI: PCI Interrupt 0000:01:01.2[A] -> GSI 21 (level, low) -> IRQ 23
[   26.645754] cx88[0]/2: found at 0000:01:01.2, rev: 5, irq: 23, latency: 64, mmio: 0xcd000000
[   26.645823] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   26.645839] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   26.789262] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 23

thanks for any advice you can offer.

---

### Post by superm1 on 2007-04-05
there is a bug in kernels 2.6.20+, you will have to:
sudo modprobe cx88_dvb

and then add cx88_dvb into /etc/modules

---

