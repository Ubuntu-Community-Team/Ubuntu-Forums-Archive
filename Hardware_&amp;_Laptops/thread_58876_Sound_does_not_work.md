---
title: "Sound does not work"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by darkfusion on 2005-08-21
First off I would like to say that Im running debian 3.1 and not ubuntu . My hadware is a pci Creative Labs audigy 2 zs . Here is a print out of lspci . 

> 
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridg e
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:00:08.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (re v 04)
0000:00:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04 )
0000:00:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip co mpatible 10/100 Ethernet (rev 31)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Ra deon 9000] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000]  (Secondary) (rev 01) 

If you need any more info just ask. Thanks

---

### Post by mo_x on 2005-08-22
Is seems you also have an integrated sound  device on the motherboard. Try to disable that in the BIOS.

---

### Post by darkfusion on 2005-08-24
I did that and still nothing . I also tried the alsa driver and the guide provided here but still no luck . 

> 0000:00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04) 

I dont see EMU10k1 .

---

### Post by mo_x on 2005-08-26
Check if the correct module is loaded with the following command:
```
lsmod | grep snd
```

---

