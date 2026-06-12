---
title: "No sound"
date: 2004-12-17
forum: Hardware &amp; Laptops
---

### Post by erredea on 2004-12-17
I can't get any sound. I can't listen to mp3, ogg, cd's, etc.

My sound card is a SiS 7012 and my PC is a x86.

Thanx

---

### Post by wulf on 2004-12-17
Nothing at all? I was getting desktop sound FX, such as the file played when logging in, but nothing when trying to play CDs. However, a bit of experimenting with the sound control panel  revealed which slider had to be taken off mute.

You should have a speaker icon towards the top right of your screen (assuming you desktop is still fairly close to the default setup). Left click to adjust the master volume; right click to get the full control panel. If it come up anything like mine, you should have quite a few options.

Wulf

---

### Post by erredea on 2004-12-17
Nothing at all. 

May be, this can help:

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS 645xx (rev 11)
        Subsystem: Asustek Computer, Inc.: Unknown device 8086
        Flags: bus master, medium devsel, latency 32
        Memory at f8000000 (32-bit, non-prefetchable)
        Capabilities: [c0] AGP version 3.5

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
        Flags: bus master, medium devsel, latency 0

0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
        Flags: medium devsel, IRQ 177
        I/O ports at 1000 [size=32]

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Asustek Computer, Inc.: Unknown device 8087
        Flags: bus master, medium devsel, latency 128, IRQ 185
        I/O ports at b400 [size=16]

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Asustek Computer, Inc.: Unknown device 80b0
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at a400
        I/O ports at a000 [size=128]
        Capabilities: [48] Power Management version 2

0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8087
        Flags: bus master, medium devsel, latency 32, IRQ 169
        Memory at f7800000 (32-bit, non-prefetchable)

0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8087
        Flags: bus master, medium devsel, latency 32, IRQ 201
        Memory at f7000000 (32-bit, non-prefetchable)

0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 8087
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at f6800000 (32-bit, non-prefetchable)
        Capabilities: [50] Power Management version 2

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
        Subsystem: Asustek Computer, Inc.: Unknown device 80a7
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at 9800 [size=febe0000]
        Memory at f6000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 00020000 [disabled]
        Capabilities: [40] Power Management version 2

0000:00:08.0 VGA compatible controller: S3 Inc. 86c775/86c785 [Trio 64V2/DX or /GX] (rev 16) (prog-if 00 [VGA])
        Subsystem: S3 Inc. 86C775 Trio64V2/DX, 86C785 Trio64V2/GX
        Flags: medium devsel, IRQ 217
        Memory at f0000000 (32-bit, non-prefetchable) [size=febd0000]
        Expansion ROM at 00010000 [disabled]

0000:00:0a.0 USB Controller: Lucent Microelectronics USS-344S USB Controller (rev 11) (prog-if 10 [OHCI])
        Subsystem: Lucent Microelectronics USS-344S USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ef800000 (32-bit, non-prefetchable)
        Capabilities: [50] Power Management version 2

0000:00:0a.1 USB Controller: Lucent Microelectronics USS-344S USB Controller (rev 11) (prog-if 10 [OHCI])
        Subsystem: Lucent Microelectronics USS-344S USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ef000000 (32-bit, non-prefetchable)
        Capabilities: [50] Power Management version 2

0000:00:0a.2 USB Controller: Lucent Microelectronics USS-344S USB Controller (rev 11) (prog-if 10 [OHCI])
        Subsystem: Lucent Microelectronics USS-344S USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ee800000 (32-bit, non-prefetchable)
        Capabilities: [50] Power Management version 2

0000:00:0a.3 USB Controller: Lucent Microelectronics USS-344S USB Controller (rev 11) (prog-if 10 [OHCI])
        Subsystem: Lucent Microelectronics USS-344S USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ee000000 (32-bit, non-prefetchable)
        Capabilities: [50] Power Management version 2

0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
        Flags: medium devsel, IRQ 217
        I/O ports at 9400

---

### Post by wulf on 2004-12-18
Where does that information come from? It doesn't suggest anything to me but might to someone else.

Meanwhile, I'm assuming you do have a speaker icon next to the calendar and clock in the top right corner of your screen. What options come up when you open the volume control (with a right click)?

Wulf

---

### Post by nemin on 2004-12-18
[QUOTE=erredea]I can't get any sound. I can't listen to mp3, ogg, cd's, etc.[/QUOTE]
I also could not get any sound out of my pc first.
I had three sound devices: a Soundblaster soundcard, an integrated soundcard and a webcam with built-in microphone. After disabling the integrated soundcard and disconnecting my webcam, everthing worked fine :) 
Maybe you also have multiple sound devices bothering each other?

---

### Post by boobytrapped on 2005-01-01
[QUOTE=nemin]I also could not get any sound out of my pc first.
I had three sound devices: a Soundblaster soundcard, an integrated soundcard and a webcam with built-in microphone. After disabling the integrated soundcard and disconnecting my webcam, everthing worked fine :) 
Maybe you also have multiple sound devices bothering each other?[/QUOTE]

Webcams indeed cause a problem.  I have a Quickcam Orbit webcam with a builtin microphone, and if I boot the machine with the webcam plugged in, Ubuntu picks as the webcam as the default "sound card", hence no sound is routed to the real sound card.

Is there a way to pick the default sound card?

---

### Post by nemin on 2005-01-01
[QUOTE=boobytrapped]Webcams indeed cause a problem.  I have a Quickcam Orbit webcam with a builtin microphone, and if I boot the machine with the webcam plugged in, Ubuntu picks as the webcam as the default "sound card", hence no sound is routed to the real sound card.

Is there a way to pick the default sound card?[/QUOTE]
 I'm don't know how to select the default sound device. But I'm very interested too: it's so annyoing to plug in and out the cam when I reboot to windows and back to unbuntu..

---

### Post by blakdragon1393 on 2007-05-15
> **wulf said:**
> Where does that information come from? It doesn't suggest anything to me but might to someone else.

Meanwhile, I'm assuming you do have a speaker icon next to the calendar and clock in the top right corner of your screen. What options come up when you open the volume control (with a right click)?

Wulf


[weather Debt Consolidation Cash Advance biology plants](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

### Post by dwnloaders8826 on 2007-05-15
> **wulf said:**
> Nothing at all? I was getting desktop sound FX, such as the file played when logging in, but nothing when trying to play CDs. However, a bit of experimenting with the sound control panel  revealed which slider had to be taken off mute.

You should have a speaker icon towards the top right of your screen (assuming you desktop is still fairly close to the default setup). Left click to adjust the master volume; right click to get the full control panel. If it come up anything like mine, you should have quite a few options.

Wulf


[generator bread baking blood pressure Paris Hilton](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

