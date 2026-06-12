---
title: "Toshiba L655 wireless, audio, and battery issues"
date: 2010-12-09
forum: Hardware
---

### Post by canucked on 2010-12-09
I configured Ubuntu 10.10 Maverick 64-bit for a friend who recently purchased a **Toshiba Satellite L655-S5115** laptop.  Here are the hardware issues I encountered:

**1) Wireless adapter, Realtek RTL8188CE, is not recognized.**

Solution:
-Add the following PPA and install deb package with DKMS module.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

References:

[https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/~lexical/+archive/hwe-wireless")
[http://guide.ubuntuforums.org/showthread.php?t=1580036&page=2]("http://guide.ubuntuforums.org/showthread.php?t=1580036&page=2")

Alternative solution: (did not attempt)
-Download Realtek driver from Realtek's website.  Downloaded driver is for RTL8192CE.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE")
-Compile downloaded Realtek driver for current linux kernel.
-The problem with this solution is that the realtek driver must be manually recompiled each time a new kernel is installed.

Reference:
[http://ubuntuforums.org/showthread.php?t=1604101]("http://ubuntuforums.org/showthread.php?t=1604101")


**2) Built-in microphone, microphone input jack, and headphone output jack do not work.**
-Built-in speakers work.  Plugging in headphones do not mute speakers.

Audio: Conexant CX20585

Solution: 
-edit /etc/modprobe.d/alsa-base.conf and add:
```
options snd-hda-intel model=thinkpad
```

References:
[http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/post/2698401/]("http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/post/2698401/")
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Note: Upgrading to the latest alsa development code (3 Dec 2010) did not resolve the sound issue.
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")


**3) Battery not recognized.**
-The laptop runs on battery power, but there is no way of determining the level of battery charge.

/var/log/syslog:
ACPI: Battery Slot [BAT1] (battery absent)

Solution: NONE FOUND

Related posts and bug reports:
[http://ubuntuforums.org/showthread.php?t=1546463]("http://ubuntuforums.org/showthread.php?t=1546463")
[http://ubuntuforums.org/showthread.php?p=10189252]("http://ubuntuforums.org/showthread.php?p=10189252")
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/620414]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/620414")
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/564488]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/564488")
[https://bugs.launchpad.net/ubuntu/+bug/668148]("https://bugs.launchpad.net/ubuntu/+bug/668148")


Other notes:
-Linux kernel 2.6.35-23-generic.
-BIOS upgraded to most recent: v1.70 09-15-2010.
-Ubuntu 11.04 Natty alpha1 64-bit had the same wireless, audio, and battery issues.
-None of these issues are present in Windows 7.

I hope this post helps those of you with similar hardware problems!  And if anyone finds a work-around for the Toshiba battery not being recognized, please share your solution!

---

### Post by tdrusk on 2010-12-13
Thank you. I will be doing this today. 

I have Debian Squeeze installed and the battery is recognized. 

What restricted driver was installed in Ubuntu for the graphics card if there was any? I had something come up in Linux Mint, but Debian doesn't have a restricted drivers manager.

---

### Post by tdrusk on 2010-12-13
Hey I got it all working. I just installed the official driver from [the website. ]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE")

Sound worked out of the box. Now I am just going to disable the touchpad while typing because I keep accidentally tapping it.

---

### Post by canucked on 2010-12-13
That's great your battery is recognized with Debian Squeeze!  Which linux kernel is it running?  Hopefully that fix will make it into Ubuntu soon.

There were no restricted drivers to enable in Ubuntu Maverick 64-bit.  The graphics seemed to work fine, with extremetuxracer getting ~60fps with default settings, IIRC.  It's curious that Mint offered a restricted driver.

Congrats on getting everything working.  And feel free to post if you find a workaround for the battery issue in Ubuntu.  I assume it affects Mint as well.

---

### Post by tdrusk on 2010-12-14
> **canucked said:**
> That's great your battery is recognized with Debian Squeeze!  Which linux kernel is it running?  Hopefully that fix will make it into Ubuntu soon.

There were no restricted drivers to enable in Ubuntu Maverick 64-bit.  The graphics seemed to work fine, with extremetuxracer getting ~60fps with default settings, IIRC.  It's curious that Mint offered a restricted driver.

Congrats on getting everything working.  And feel free to post if you find a workaround for the battery issue in Ubuntu.  I assume it affects Mint as well.

I forgot that our laptops may not be identical. This could explain the restricted drivers and battery issue. My laptop is a Toshibal Satellite L655-S5093. I am also running kde which may just pick up on the battery easier(no idea). Regardless :)

```

# uname -r
2.6.32-5-amd64
```

```

#lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 0
        Capabilities: [c4] HyperTransport: Slave or Primary Interface
        Capabilities: [54] HyperTransport: UnitID Clumping
        Capabilities: [40] HyperTransport: Retry Mode
        Capabilities: [9c] HyperTransport: #1a
        Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Toshiba America Info Systems Device 9602 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: d4100000-d42fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
        Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
        I/O behind bridge: 00007000-0000afff
        Memory behind bridge: d3100000-d40fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+), MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50
        Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [110] Virtual Channel
        Kernel driver in use: pcieport

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: d3000000-d30fffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+), MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50
        Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [110] Virtual Channel
        Kernel driver in use: pcieport

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at c038 [size=8]
        I/O ports at c04c [size=4]
        I/O ports at c030 [size=8]
        I/O ports at c048 [size=4]
        I/O ports at c010 [size=16]
        Memory at d4307000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [70] SATA HBA v1.0
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d4306000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at d4307600 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port: BAR=1 offset=00e0
        Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d4305000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at d4307500 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port: BAR=1 offset=00e0
        Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: 66MHz, medium devsel
        Kernel driver in use: piix4_smbus

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at d4300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Kernel driver in use: HDA Intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=64

00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0f, sec-latency=0
        I/O behind bridge: 00002000-00005fff
        Memory behind bridge: d2000000-d2ffffff
        Prefetchable memory behind bridge: 00000000d1000000-00000000d1ffffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot+), MSI 00
        Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [b0] Subsystem: ATI Technologies Inc Device 0000
        Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Kernel driver in use: pcieport

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at d4304000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at d4307400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port: BAR=1 offset=00e0
        Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
        Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200] (prog-if 00 [VGA controller])
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at b000 [size=256]
        Memory at d4200000 (32-bit, non-prefetchable) [size=64K]
        Memory at d4100000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [50] Power Management version 3
        Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Kernel driver in use: radeon

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
        Subsystem: Realtek Semiconductor Co., Ltd. Device 8185
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 7000 [size=256]
        Memory at d3100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [160] Device Serial Number 01-91-81-fe-ff-4c-e0-00
        Kernel driver in use: rtl8192CE

08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
        Subsystem: Toshiba America Info Systems Device fd50
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at d3000000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at 6000 [size=128]
        Capabilities: [40] Power Management version 3
        Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [58] Express Endpoint, MSI 00
        Capabilities: [6c] Vital Product Data
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [180] Device Serial Number ff-3f-b4-bc-60-eb-69-ff
        Kernel driver in use: atl1c


```

---

### Post by bwdave on 2010-12-15
I got my Toshiba L675 working by running:

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

Thanks Canucked!

I had problems with it dropping connections and then establishing a connection but not getting DNS addressing.  I had to delete my old connection and re-establish a connection to my wifi (WPA) but it is now working and no dropping connections.

---

### Post by canucked on 2010-12-16
@tdrusk: I may try Debian Squeeze and see whether it recognizes the battery on my friend's L655.  Thanks for telling me about it.

@bwdave: I'm glad you got your wireless working!

---

### Post by temperer on 2011-01-09
I have L655 (asian model) it is Core i3 and HM55 chipset.
WiFi is Broadcom.
Yesterday I tried maverick 10.10.
Installed without any problems. WiFi started out of the box.
Graphics started too with compozition 3d cube. One must mention however some white points flickering between title bar and window client area while moving window.

But sound - doesn't work properly. Sound check left/right ok but mic doesn't work.
After I tried as mentioned above (options snd-hda-intel model=thinkpad) mic works but sound level is awfully low.

And ACPI - total problem. Battery not detected. sensors utility was unable to find sensors.
Problem with (I may wrong) Intel Turbo Boost.

And again synaptics touchpad two finger scrolling disabled in mouse config. And pressing pad with two fingers causes cursor to move randomly across the screen.

Notes:
Bios 1.70 as in the first post.

PS. tried 2.6.37 rc2 kernel - nothing changed.

The problem seems to be in HM55 (budget intel mobile chipset).

---

### Post by temperer on 2011-01-11
Unfortunately. The thread takes so few attention...((

---

### Post by canucked on 2011-01-11
temperer: Thanks for posting your issues with your Toshiba L655.  I also noticed a similar touchpad problem.

The L655 I configured belongs to a friend so I haven't had a chance to try different settings or distributions (such as Debian Squeeze, mentioned by tdrusk in this thread).  If I am able to make any progress with my friend's L655 I will post it here.

And by the way, the Intel Core i3 does not support Intel Turbo Boost.  Turbo Boost is found in the Core i5 and i7 CPUs.

---

### Post by techinterplay on 2011-01-12
Got same problem here. I have Toshiba L650 X5310 and have issues in detecting battery. The two issues I noticed after installing 10.10 were the in-built mic not working and battery not being detected and the problem with mic I got fixed by appending the line "snd-hda-intel model=thinkpad", thanks for mentioning that fix. I have tried different versions/distros of Linux and all posses the same issue. 

> dmesg
[    0.974500] ACPI: Battery Slot [BAT1] (battery absent)l> spci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d6000000-d60fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: [88] Subsystem: Toshiba America Info Systems Device fd50
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d6106100 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d6105c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d6100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d5000000-d5ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device fd50
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d4000000-d4ffffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d1ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device fd50
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d3000000-d3ffffff
    Prefetchable memory behind bridge: 00000000d2000000-00000000d2ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Toshiba America Info Systems Device fd50
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d6105800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: [50] Subsystem: Toshiba America Info Systems Device fd50

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 6048 [size=8]
    I/O ports at 6054 [size=4]
    I/O ports at 6040 [size=8]
    I/O ports at 6050 [size=4]
    I/O ports at 6020 [size=32]
    Memory at d6105000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: medium devsel, IRQ 10
    Memory at d6106000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at d6104000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d6000000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 5000 [size=256]
    Expansion ROM at d6040000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d6020000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
    Subsystem: Askey Computer Corp. Device 7175
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-df-ff-ff-00-e8-39
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl

04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at d3000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-a3-c6-a2-c8-0a-a9-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0@tdrusk shall I confirm that we are on the same boat ;) atleaset the same battery? I might need to switch for Debain squeeze?

---

### Post by DarKMaTTeR.tm on 2011-01-31
I have a satellite L655 - 113

I can't get my headphones work properly.

appending
options snd-hda-intel model=thinkpad
made no difference.

i also found somewhere else a tip to add
options snd-hda-intel model=ideapad
which had no effect either.

any advise?

---

### Post by canucked on 2011-02-04
@DarKMaTTeR.tm:
You can try installing LinuxAlsaDriverModules
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

or you could try other models for options snd-hda-intel model=thinkpad
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If neither of the suggestions in those links works, you may want to start a new thread for your problem.

---

### Post by ljerez on 2011-03-24
Has anyone figured out a fix for the battery recognition problem? I just got this laptop and I have fixed the audio/wireless, but battery still remains a problem with being detected in Ubuntu.

---

### Post by tdrusk on 2011-03-27
> **canucked said:**
> I configured Ubuntu 10.10 Maverick 64-bit for a friend who recently purchased a **Toshiba Satellite L655-S5115** laptop.  Here are the hardware issues I encountered:

**1) Wireless adapter, Realtek RTL8188CE, is not recognized.**

Solution:
-Add the following PPA and install deb package with DKMS module.
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```References:

[https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/%7Elexical/+archive/hwe-wireless")
[http://guide.ubuntuforums.org/showthread.php?t=1580036&page=2](http://guide.ubuntuforums.org/showthread.php?t=1580036&page=2)

Alternative solution: (did not attempt)
-Download Realtek driver from Realtek's website.  Downloaded driver is for RTL8192CE.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)
-Compile downloaded Realtek driver for current linux kernel.
-The problem with this solution is that the realtek driver must be manually recompiled each time a new kernel is installed.

Reference:
[http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101)


Just a note on this. The driver does not seem to connect to WEP 40/128-bit Key with Open Authentication connections well. If you are having problems with the internet not working after a few minutes you may need to change it to a WEP 40/128-bit Key with Shared Authentication.

---

### Post by Rich D on 2011-04-11
I'm getting a similar problem with a Toshiba L640 PSK0LA-05X00T on Natty - no battery is visible.

I had working wireless until I tried a BIOS update to fix the battery problem. Now I have no wireless *and* no battery. (After the update a bluetooth icon popped up in my menubar, so perhaps the updated did do something positive?)

After the BIOS update I also tried adding acpi_osi="Linux" to grub to see if that would fix the battery. But it didn't seem to do anything at all.

I now have to fix up my wireless and any other issues that may have occurred. I haven't tried anything yet - not even the proprietary drivers that Ubuntu suggests or other suggestions in this thread. This is just a preliminary report to let others know about my BIOS experience!

[I]More info: I updated my BIOS from 1.70 to 2.30. Here's the link I used to download the update:
[http://www.mytoshiba.com.au/support/notebooks/satellite/l640/psk0la-05x00t/download](http://www.mytoshiba.com.au/support/notebooks/satellite/l640/psk0la-05x00t/download)[/I]

---

### Post by theCoder on 2011-04-22
> **tdrusk said:**
> Just a note on this. The driver does not seem to connect to WEP 40/128-bit Key with Open Authentication connections well. If you are having problems with the internet not working after a few minutes you may need to change it to a WEP 40/128-bit Key with Shared Authentication.

From your previous posts, you are using an older kernel in debian squeeze than Ubuntu Maverick uses.
You run uname -r and get kernel version 2.6.32, while in Maverick we get version 2.6.35.

This is important, because the drivers from realtek say in the readme for these drivers that kernels older than 2.6.35 are not supported, and may not even work.

Also note that older kernels do support the battery. I tried installing Ubuntu Lucid (also kernel version 2.6.32) first, and the battery meter works, but not any of the wireless or ethernet.

So something is either broken or no longer supported upstream.

---

### Post by rejekt on 2011-05-01
I have a Toshiba L650 laptop that I just got, Core i3, 4gb ram, etc. etc.

It arrived the same day Ubuntu 11.04 was released, so I right away I downloaded the ISO and reformatted over the Windows 7 64-bit Home Edition that was pre-installed.

After getting Ubuntu 11.04 installed I did run into the built-in microphone issue not working. It was resolved rather easily by following the configuration change at the start of this post. I didn't have any issues with the wireless though.

However, I am still having issues with the battery not being detected and I have searched high and low over these forums and other forums using Google and have found nothing that has resolved the issue.

There has been talk about rebuilding the kernel, about updating the BIOS of the machine, etc. but no one has been able to 100% determine the actual fix.

uname -r
2.6.38-8-generic

cat /proc/acpi/battery/BAT1/state
present:                 no

lshw -C power
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 2
       version: 10/12/2007
       serial: Battery 0
       slot: Fake

Is it because acpi is looking at BAT1 while lshw is showing the battery in slot "Fake" with serial "Battery 0"?

If there's any other information that I can provide to possible help, please let me know.

Thanks,
Brian

Edit: I'm not exactly sure what I've done different now than previously except for reboot the laptop.

However now I get the following, but still no battery monitor in the status menu in the upper-right.

cat /proc/acpi/battery/BAT1/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            1126 mA
remaining capacity:      3591 mAh
present voltage:         12571 mV


acpi -V
Battery 0: Full, 100%
Battery 0: design capacity 4500 mAh, last full capacity 3591 mAh = 79%
Adapter 0: on-line
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10

dmesg | grep battery
[    1.421954] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.421990] ACPI: Battery Slot [BAT1] (battery absent)

Which configuration location would I want to try and set the CONFIG_ACPI_PROCFS_POWER option that it is recommending?

Ughhhhh, wish I could fully resolve this issue. =\

---

### Post by techinterplay on 2011-06-03
Hello Everyone,

Good News :-) battery issue has been resolved [http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html)
Hope this helps!

---

### Post by kroq-gar78 on 2011-06-24
[SIZE=4]OMG THANK YOU!!!!!!!

[SIZE=2]I can now use UBUNTU ON MY LAPTOP [/SIZE][/SIZE][SIZE=4][SIZE=2]:D[/SIZE][/SIZE]
[SIZE=4][SIZE=2] Now I feel smarter 'cuz I compiled a kernel! [/SIZE][/SIZE][SIZE=4][SIZE=2]:twisted:[/SIZE][/SIZE]
[SIZE=4][SIZE=2] 
THANK YOU! 8-)

UPDATE 07/15/10: I had to run some extra commands on the kernel source to get the newest version of Virtualbox (it was 4.0.10) to get the kernel module for vbox to install:
```

make oldconfig

```and there was one more which I can't seem to remember :/
[/SIZE][/SIZE]

---

