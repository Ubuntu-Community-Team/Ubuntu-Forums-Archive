---
title: "Installing 9.04 on a Toshiba Satellite L45?"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by AoSteve on 2009-06-12
Alright, I had a hard drive failure on my laptop and absolutely refuse to reinstall a windows operating system on it.   So, here's my question, I tried through the HCL, but didn't come up with much on results.   I've tried the live CD, since I don't have an HDD right now and I know the following work with the CD.

The sound works on boot (the drums)
The video, obviously..  came up at 1280x800 I believe
The CD Drive obviously works (no idea for the HDD until it get my new one)
The touch pad works but I'm not sure how to do some things as I've NEVER installed ubuntu on a laptop.

Here's the specs, just incase it's important:

Intel Pentium Dual Core 1.73Ghz
1GB 533mhz DDR2
Intel GMA (I believe it's a 3100)
Some el-cheapo sound system
DVD-Super multi whatever the heck
Atheros wireless G internal wireless card

It's a budget laptop, and it struggled like heck with Vista Home Premium on it.  I'll be upgrading to 2GB (Max for system) soon enough.

Here's my questions..

How can I get the "tap to click" function to work when I do the install for my laptop.  Also, will the "side" scrolling work with it?  Not sure on the software available for it.   I like that function in windows.   It's a synaptics touchpad, but I never could get any model or serial numbers for it in windows.

Are there any special drivers for the Atheros that I'll have to download?   I remember trying to boot the system with my Ubuntu 8.whatever CD I downloaded and it wouldn't work at all.   I haven't tried the adapter on the 9.04 CD as my router is disconnected so there's no point in trying.

This system is mostly going to be used to browse the internet, play a DVD once in a while, and do basic schooling chores.   Nothing major.   I just would like to be ready before I go to install my hard drive and get it running again.  

I remember a friend of mine having all kinds of trouble getting his wireless card to work in 7.10 and he has the same exact one as I do.   Hopefully there's a driver that works with 9.04?    

My last question, sorry for being so "information hungry" here.   Where exactly is the ubuntu's HCL?   I searched for it but it doesn't come up?   

I appreciate any information,
Steve  :)

---

### Post by leandromartinez98 on 2009-06-12
> **AoSteve said:**
> 

How can I get the "tap to click" function to work when I do the install for my laptop.  Also, will the "side" scrolling work with it?  Not sure on the software available for it.   I like that function in windows.   It's a synaptics touchpad, but I never could get any model or serial numbers for it in windows.

This works like that by default on Ubuntu, unless there is a driver problem. It is configurable through system->preferences->mouse

> 
Are there any special drivers for the Atheros that I'll have to download?   I remember trying to boot the system with my Ubuntu 8.whatever CD I downloaded and it wouldn't work at all.   I haven't tried the adapter on the 9.04 CD as my router is disconnected so there's no point in trying.

I had problems with Atheros chips with 8.04 but all of them got solved since 8.10. Probably now it will work fine, but, of course, only testing it to be sure.


> 
I remember a friend of mine having all kinds of trouble getting his wireless card to work in 7.10 and he has the same exact one as I do.   Hopefully there's a driver that works with 9.04?    

Hopefully it will. Trying it with the liveCD is the best to do.

> 
My last question, sorry for being so "information hungry" here.   Where exactly is the ubuntu's HCL?   I searched for it but it doesn't come up?   

I don't know.

---

### Post by AoSteve on 2009-06-12
I really appreciate it.   I just want to be able to sit on my couch and browse again.  I mean, my desktop is a killer rig, but the luxury of a laptop is nice..   I can recline and browse the ubuntu forum or one of my hobby sites! :)

Hopefully the Atheros chip will work.   I have to re-enable my router to find out I guess.  My new HDD will be here next Tuesday anyways, so I'll test it on the install.  If I have to, I'll unplug it internally and run an external USB one.  :)

---

### Post by chadk5utc on 2009-06-12
I have an older Toshiba laptop and 9.04 runs Great on it. Also have several PCI/miniPCI cards that use the Atheros chipsets they also work out of the box as it were Except for one in my EeePc I had to compile a driver for, it now works great. I would suggest trying the live cd and see what happens it may surprise you?? If not lets us know what Atheros cards in it.

      Chad








Asus 1000HE 32GB SSD 2GB RAM Eeebuntu 2.0 Plus Extras 100% Working

---

### Post by AoSteve on 2009-06-13
I will definitely be running it regardless.   I'm not going to pay for a new copy of windows for something I don't HAVE to have windows on.  It came with it, so we used it.  The wife uses the laptop more and even she says, "Put Ubuntu on it!"    Just hoping to know what I may be getting into with the wireless card mainly, but the others, maybe someone has had a good/bad experience with and I can prep myself.

---

### Post by AoSteve on 2009-06-15
I'm happy as could be finally!  I was able to instantly connect to my router with Ubuntu!  WOOOOHOOOO!!   Ok... but, with myself as always, I absolutely have the WORST luck when it comes to hardware..

I don't have any sound :(

Maybe someone can help me with what all I can do here?  The install went perfectly flawless with 9.02 x86(32-bit) and it seems like everything is working correctly aside from the sound.   Also, is it possible at all to enable compiz?

Here's a shot from the terminal with lspci -v   I can't determine what the sound card is :\

```

steve@Toshiba:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at ff640000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0
    Memory at ff580000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at ff63c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: ff200000-ff2fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at e400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff63bc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ff300000-ff3fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Askey Computer Corp. Device 7128
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at ff2f0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k

05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at ff300000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 0000d000-0000d0ff
    I/O window 1: 0000d400-0000d4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Toshiba America Info Systems Device ff40
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at d800 [size=256]
    Memory at ff3ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

steve@Toshiba:~$ 

```

---

### Post by AoSteve on 2009-06-15
In a terminal, aplay -l  lists the following..

```

steve@Toshiba:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
steve@Toshiba:~$ 

```

---

### Post by Amilo1718 on 2009-06-15
80% = the same with my Satellite
sound = different from my Satellite
network card = different from my Satellite but the same as my Amilo

i'd give it a try :D

---

### Post by AoSteve on 2009-06-15
I've already installed it, if that's what you're meaning by trying it.  Now I'm having no sound :(   The wireless worked out of the box! :D   But, alas, no sound.

Any idea where I should go from here?

---

