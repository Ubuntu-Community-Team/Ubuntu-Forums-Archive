---
title: "Dummy Output/no sound card detected on System 76 Lemur running 15.10"
date: 2016-06-08
forum: Hardware
---

### Post by vadertater on 2016-06-08
So I am running a System 76 Lemur with Ubuntu 15.10. I have been using it for no problem for nearly 6 months. This morning I was able to hear audio on speakers and headphones and a few hours later, no audio at all. Apparently there is no sound card anymore!

aplay: device_list:268: no soundcards found...

I checked my sound settings and there is a dummy output under "Play Sound Through"

the only thing I can think of that *may* have effected my sound card, was that I install some drivers to make a printer compatible with my laptop. 

Anyone know what the problem is?

---

### Post by vadertater on 2016-06-08
So I tried to reboot. Nothing happened. 

I then tried to unistall/reinstall alsa and pusleaudio with the following commands. 

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie ~/.config/pulse
sudo apt-get install --reinstall alsa-base alsa-utils pulseaudio linux-sound-base libasound2
sudo alsa force-reload

The result was this: 

Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

---

### Post by X-RED_Tech on 2016-06-08
Printer drivers shouldn't mess with audio but it's not impossible.
What drivers have you installed and other actions you might remember prior to the issue?

---

### Post by vadertater on 2016-06-08
I installed the drivers for a [SIZE=3][FONT=arial]Brother HL-L2340DW printer and I also updated 12 hours before the problem. I'll look up exactly what I did and post it in a couple minutes.

I can't remember anything else significant. Just web browsing, then I close the laptop while I went for a walk, and then the sound card 'disappeared'.

I have asked for some help from System 76, and they had me reinstall the kernel because the drivers are part of the kernel. That didn't work. 

Here are the results for```
 lspci -v[/FONT][/SIZE]
``` 
```
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: bus master, fast devsel, latency 0, IRQ 126
    Memory at de000000 (64-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:14.0 USB controller: Intel Corporation Device 9d2f (rev 21) (prog-if 30 [XHCI])
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: bus master, medium devsel, latency 0, IRQ 122
    Memory at df200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:14.2 Signal processing controller: Intel Corporation Device 9d31 (rev 21)
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: fast devsel, IRQ 255
    Memory at df21a000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

00:16.0 Communication controller: Intel Corporation Device 9d3a (rev 21)
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: bus master, fast devsel, latency 0, IRQ 127
    Memory at df219000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: mei_me

00:17.0 SATA controller: Intel Corporation Device 9d03 (rev 21) (prog-if 01 [AHCI 1.0])
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 123
    Memory at df214000 (32-bit, non-prefetchable) [size=8K]
    Memory at df218000 (32-bit, non-prefetchable) [size=256]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at df217000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: df100000-df1fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation Device 9d11 (rev f1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: df000000-df0fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1f.0 ISA bridge: Intel Corporation Device 9d48 (rev 21)
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: bus master, medium devsel, latency 0

00:1f.2 Memory controller: Intel Corporation Device 9d21 (rev 21)
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: fast devsel
    Memory at df210000 (32-bit, non-prefetchable) [disabled] [size=16K]

00:1f.4 SMBus: Intel Corporation Device 9d23 (rev 21)
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: medium devsel, IRQ 255
    Memory at df216000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]

01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Memory at df115000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at df100000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci

01:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device 2425
    Flags: bus master, fast devsel, latency 0, IRQ 125
    I/O ports at e000 [size=256]
    Memory at df114000 (64-bit, non-prefetchable) [size=4K]
    Memory at df110000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
    Subsystem: Intel Corporation Device 1010
    Flags: bus master, fast devsel, latency 0, IRQ 128
    Memory at df000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
```

I'm not proficient at all with reading code, but to me it looks like there is nothing for the audio in there... which would explain a lot.

---

### Post by vadertater on 2016-06-08
So, to install the printer, I did the following commands:

```
wget http://download.brother.com/welcome/dlf006893/linux-brprinter-installer-2.0.0-1.gz
gunzip linux-brprinter-installer-2.0.0-1.gz
sudo bash linux-brprinter-installer-2.0.0-1


```

I was then asked what model, so I said: 
```
HL2270-DW
```

Then I used a USB connection to finish the installation. All of this worked, courtesy of Eric Carvalho.

EDIT: grammar

---

