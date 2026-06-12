---
title: "Screen turns off randomly"
date: 2012-12-22
forum: Hardware
---

### Post by Mountaingod on 2012-12-22
Hi all,

I'm running 12.04.1 (upgraded incrementally from 11.04) on a Toshiba C660 laptop.
It has Intel integrated graphics and is using the "Intel® Ironlake Mobile" driver. See my lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 6050 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d2605000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d2608000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d2600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00005fff
	Memory behind bridge: d1e00000-d25fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d0cfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00003fff
	Memory behind bridge: d1500000-d1dfffff
	Prefetchable memory behind bridge: 00000000d0d00000-00000000d14fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d2607000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
	I/O ports at 6048 [size=8]
	I/O ports at 605c [size=4]
	I/O ports at 6040 [size=8]
	I/O ports at 6058 [size=4]
	I/O ports at 6020 [size=32]
	Memory at d2608800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: medium devsel, IRQ 11
	Memory at d2604000 (64-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d2606000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
	Subsystem: Toshiba America Info Systems Device fd3c
	Flags: bus master, fast devsel, latency 0, IRQ 41
	I/O ports at 4000 [size=256]
	Memory at d0404000 (64-bit, prefetchable) [size=4K]
	Memory at d0400000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 2000 [size=256]
	Memory at d1500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0
```

This started about a month ago:

Every now and again the screen turns off, like it would after inactivity for power saving. Quite often this will be triggered by opening a new program, bringing up the unity panel with superkey or generally "putting something new on the screen". If I hit a key or wiggle the cursor the screen 'wakes up' again, though quite often I had to unlock with my password until I disabled locking.

Typically I'm actually doing something at the time so the screen turns off & on again in about 1/2 second when it immediately detects my input.

Unusually, I've searched but cannot find anybody else who's had this issue. Something has been installed / modified which borked my power saving. I don't know if this is a software or hardware issue.

Thanks for your insight

---

### Post by Mountaingod on 2013-01-11
I should state that unlike power saving mechanisms, there is no minimum time delay.

It just happened to me three times in the space of a couple of minutes. Screen just turns off and on again.

There is literally nobody else I can find on the net who's had this. I'm thinking of resorting to a clean install...

---

### Post by dannyboy79 on 2013-01-11
check your /var/log/Xorg.0.log file, sounds like a power saving issue to me

---

### Post by Mountaingod on 2013-01-12
Thanks for your help,

When it happens, this gets appended to the log:
```
[ 13243.345] (II) intel(0): EDID vendor "SEC", prod id 21825
[ 13243.345] (II) intel(0): Printing DDC gathered Modelines:
[ 13243.346] (II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
```

There are lots of identical entries in there, presumably from all the times it's happened in the past. Occasionally there's also
```
[  2153.968] (II) XKB: reuse xkmfile /var/lib/xkb/server-E0CEE3138D3C43CB52C449CA640DB68169ADC155.xkm
```

Am I right in thinking Xorg is restarting here?
It can't be a 'full' restart because looking at the start of the log (when my PC booted) there's loads of stuff to do with loading modules etc.

EDIT: Closest I've found to my problem (and it has no solution):
[http://askubuntu.com/questions/176433/xorg-intermittently-restarts-after-suspend](http://askubuntu.com/questions/176433/xorg-intermittently-restarts-after-suspend)

---

### Post by Mountaingod on 2013-01-13
I think (but not certain) it might be to do with Firefox.
It happened when I started FF just now. Quite often it happens when switching windows to FF.
FF is usually open somewhere when it happens, although it's pretty much always open on my laptop.
Other people online with Xorg crashing issues often mention Firefox.

I wonder if it's this [https://bugzilla.redhat.com/show_bug.cgi?id=495733](https://bugzilla.redhat.com/show_bug.cgi?id=495733) ?

Also, I wonder if it's possible to make xorg logging more verbose than it currently is, in case I'm missing error messages...

---

### Post by tlhIngan on 2013-01-13
Just to cover all the bases, make sure your vga and power cables are snug and secure at the back of your monitor and into your tower. Could be a vibration from using your keyboard or mouse is jiggling the wires.

---

### Post by Mountaingod on 2013-01-15
> **tlhIngan said:**
> Just to cover all the bases, make sure your vga and power cables are snug and secure at the back of your monitor and into your tower. Could be a vibration from using your keyboard or mouse is jiggling the wires.

Thanks for the suggestion, but it's a laptop.

I've tried increasing the log level of X by adding this to my lightdm.conf:
```
xserver-command=/usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none -logverbose 9 -I
```

Which according to lightdm.log caused it to start X thus:
```
DEBUG: Launching process 1119: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none -logverbose 9 -I :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
```
(where the -I option tells X to ignore all further options, thus abusing the xserver-command conf-option to do what I want)

But it didn't make a difference to Xorg.0.log . I don't know what the highest log level is (couldn't find it anywhere) but it seems X doesn't have any more to say about these mini-restarts.

The best I have so far is my (ever-increasing) hunch it's Firefox somehow.

---

### Post by Mountaingod on 2013-09-06
Just to say I switched to Xubuntu a few days ago, and upgraded to kernel 3.8.0-30-generic , and the damn thing just happened again.

There are very many people with a similar problem, across Linux distros: [Google search]("https://www.google.co.uk/search?client=ubuntu&channel=fs&q=droid+x+restarts+randomly&ie=utf-8&oe=utf-8&gws_rd=cr&ei=trspUtW0C-vL0AWbroCQCw#channel=fs&q=x+server+restarts+randomly&safe=off") - not a single solution or possible explanation.

...except for memory leaks, possibly from Firefox. I think (but not sure yet) the frequency has gone down since installing Xubuntu - which uses less RAM. The fresh install may also have cleared RAM-hungry bloat.

Really, really irritating. Xorg.0.log is useless.

---

### Post by tgalati4 on 2013-09-06
How old is the laptop?  It could be failing video RAM.  I don't know of any way to check it.  I would reseat your regular RAM on the laptop and run memtest for 30 complete cycles.  Check the BIOS for RAM sharing with video.  Either turn it off or set it to maximum.  Play with different values to see if there is any difference in behavior.

Boot a Live DVD/USB session and run from RAM.  If it happens in that case, I would suspect a hardware problem as opposed to your installed distro.

Also, be mindful that a thin, multi-wire cable runs through the hinge.  It can be a wear point causing shorting and blackouts.  Is your hinge loose and floppy?

I agree, Xorg.0.log is useless for capturing errors that are outside of xorg's control--like a hardware error.

If it is a worn cable, does it happen more at maximum brightness or minimum brightness?

---

