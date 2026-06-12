---
title: "TOSHIBA SATELLITE A215-S7416 Sound / Wifi Problem"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by LinuxMaster9 on 2008-01-20
We have a Toshiba Satellite A215-S7416, we installed Gutsy i386 on it and it works fine except for the sound and wifi. We have tried the other forum posts suggestions and they did not work. Alsa is up to date but no avail.

---

### Post by balaknair on 2008-01-20
Hi
Could you please type the following commands in a terminal and post the output
aplay -l
lspci -v

---

### Post by 0mcg0 on 2008-01-21
What is the sound and wifi hardware in the laptop?  Looking at the output of lspci will probably show you the chips being used.  If the wifi is a Broadcom chip the new b43 driver might work, you can install it with the restricted driver manager, download and install the firmware.  Then you can activate it with 

modprobe b43

then set up and save a profile for connecting to the wireless signal with network-manager
and then append b43 to the /etc/modules file so that it will be activated when you reboot.
If that doesn't work you may have to try ndiswrapper.

If your sound chip is an HDA Intel ICH8 family chip then you should try the following easy fix:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

That is what worked for my hp dv6628us laptop with gutsy.

Good Luck

---

### Post by LinuxMaster9 on 2008-01-27
cameron@Skeetattack08:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cameron@Skeetattack08:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f8000000-f81fffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=0d, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f8200000-f82fffff
        Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0e, subordinate=13, sec-latency=0
        Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        I/O ports at 8440 [size=8]
        I/O ports at 8434 [size=4]
        I/O ports at 8438 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8400 [size=16]
        Memory at f8609000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at f8604000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f8605000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at f8606000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at f8607000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at f8608000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at f8609400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8420 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Toshiba America Info Systems Unknown device ff0a
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at f8600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=14, subordinate=19, sec-latency=64
        Memory behind bridge: f8300000-f83fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff1a
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at f0000000 (64-bit, prefetchable) [size=128M]
        Memory at f8100000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 9000 [size=256]
        Memory at f8000000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at a000 [size=256]
        Memory at f8200000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at f8300000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8300800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8300c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8301000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f8301400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

cameron@Skeetattack08:~$

---

### Post by balaknair on 2008-01-27
Hello Linuxmaster9
Please read to the end before you try these steps
As per what I found on the Alsa-project site, you need the hda-intel module, and my guess is the Codec is Realtek ALC268
The easiest way to fix it is I think to just use the backports modules
1) Enable backports in software sources (System Menu> Admin.> Software Sources--> Updates--> enable Backports)

2)Then open a terminal and type in
uname -r
*this will tell you what kernel you're running(eg 386 or generic)*

3) In a terminal
sudo aptitude install linux-backports-modules-generic

                     OR
sudo aptitude install linux-backports-modules-386

depending on what kernel you have.

4) In a terminal
sudo gedit /etc/modprobe.d/alsa-base
 this will open a file in gedit(the text editor). scroll down the page and
add this as the last line
options snd-hda-intel model=toshiba
Reboot.

This will upgrade your alsa to the 1.0.15RC3 version so chances are your sound should be fixed.

Remember you might need to Unmute all channels(default is muted) before you hear any sound.

If these steps don't fix your sound, you can try this guide(particularly Method E for Realtek ALC268)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

If this works, please reply and tell us what worked for you.
All the best

---

### Post by nwadams on 2008-01-27
or skip all steps except this one: 

sudo gedit /etc/modprobe.d/alsa-base
this will open a file in gedit(the text editor). scroll down the page and
add this as the last line
options snd-hda-intel model=toshiba

but instead of putting options snd-hda-intel model=toshiba in put 

options snd-hda-intel model=3stack

---

### Post by LinuxMaster9 on 2008-01-28
Thanks the only other thing about the sound is that it claims there is no mixer installed or gstreamer thing but I installed everything so i cant modify the sound mixer

---

### Post by LinuxMaster9 on 2008-01-28
Also, how do i get the wifi working? The wifi gets turned on via an "fn" key combination.

---

### Post by fermin on 2008-04-28
I had this same problem in this exact same laptop model Toshiba Satellite A215-S7416. I installed Ubuntu 7.10 Gutsy Gibbon last year and had dual boot with Windows Vista, but i couldn't get sound and wifi to work so i din't use my Ubuntu much. Now i upgraded to Hardy Heron two days ago and the sound is working! nevertheless, wifi is still not working and can't get it to work. Also, the desktop effects cannot be enabled anymore so im out of compiz fusion and emerald :( could anyone help us out?

---

