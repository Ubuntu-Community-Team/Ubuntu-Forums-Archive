---
title: "What video card?"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by Jenda on 2005-05-22
The graphics on my friend's fresh Ubuntu aren't working properly. Sometimes, before the GUI boots and after it shuts down, most of the screen locks up and all that's happening is differently colored dots, that are probably supposed to be very small letters. The visual effects in Totem and a few games (chromium) are choppy. I haven't yet tried playing videos.
    We do not know what video card he has, and do not know how to find out. Can anyone give us a push the right way...?

---

### Post by f.prisson on 2005-05-22
```
lspci -v
``` will tell you what chipset your card is using

---

### Post by Jenda on 2005-05-22
The Terminal spat out the following, whatever that means:
> 0000:00:00.0 Host bridge: Intel Corp. 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
        Flags: bus master, fast devsel, latency 0

0000:00:01.0 VGA compatible controller: Intel Corp. 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Intel Corp.: Unknown device 4332
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ff800000-ff8fffff
        Prefetchable memory behind bridge: f6a00000-f6afffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corp. 82801AA IDE
        Flags: bus master, medium devsel, latency 0
        I/O ports at ffa0 [size=16]

0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corp. 82801AA USB
        Flags: bus master, medium devsel, latency 0, IRQ 9
        I/O ports at ef80 [size=32]

0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
        Subsystem: Intel Corp. 82801AA SMBus
        Flags: medium devsel, IRQ 10
        I/O ports at efa0 [size=16]

0000:01:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs CT4780 SBLive! Value
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at df80 [size=32]
        Capabilities: <available only to root>

0000:01:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at dff0 [size=8]
        Capabilities: <available only to root>

0000:01:0b.0 Communication controller: Lucent Microelectronics LT WinModem
        Subsystem: Askey Computer Corp.: Unknown device 1513
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at ff8ffc00 (32-bit, non-prefetchable) [size=256]
        I/O ports at dfe0 [size=8]
        I/O ports at d800 [size=256]
        Capabilities: <available only to root>

---

### Post by Jenda on 2005-05-23
[QUOTE=Jenda]The Terminal spat out the following, whatever that means:[/QUOTE]
 Need HELP! Please!

---

### Post by dare2dreamer on 2005-05-23
<quote>0000:00:01.0 VGA compatible controller: Intel Corp. 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
Subsystem: Intel Corp.: Unknown device 4332
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
Memory at f8000000 (32-bit, prefetchable) [size=64M]
Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <available only to root></quote>

Try running the command as root with sudo.

<code>sudo commandhere</code>

That should give us a bit more information to work with.

---

### Post by Jenda on 2005-05-23
Does this help?
[QUOTE=My friend's computer]0000:00:01.0 VGA compatible controller: Intel Corp. 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Intel Corp.: Unknown device 4332
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [dc] Power Management version 1[/QUOTE]

---

### Post by teme82 on 2005-05-23
[QUOTE=Jenda]Does this help?[/QUOTE]

It's intel i810 chip set... it has integrated viedocard :P

---

### Post by Jenda on 2005-05-24
Thanks, but does that mean that it's already installed? Then what is causing the graphics problem?

---

### Post by Jenda on 2005-05-25
OK, now I know he has an integrated video card, with i810 chipset. But WHAT causes this?
[Quote=me]Sometimes, before the GUI boots and after it shuts down, most of the screen locks up and all that's happening is differently colored dots, that are probably supposed to be very small letters. The visual effects in Totem and a few games (chromium) are choppy. I haven't yet tried playing videos.[/Quote]

---

### Post by Jenda on 2005-05-27
PLEASE!!! Help!!! What do I do? Why is the graphics so bad?

---

### Post by dare2dreamer on 2005-05-28
Can you please define in what way the graphics are "bad"?

It would make it easier to narrow down the problem.

For the record, I installed a system last Friday with an i810 video card with minimal issues, mainly that hoary was unable to correctly probe the attached monitor and therefore I was left at 640x480 until I hacked together some modeline settings.

The card itself configured with no issues.

---

### Post by Jenda on 2005-05-29
[QUOTE=dare2dreamer]Can you please define in what way the graphics are "bad"?

It would make it easier to narrow down the problem.

For the record, I installed a system last Friday with an i810 video card with minimal issues, mainly that hoary was unable to correctly probe the attached monitor and therefore I was left at 640x480 until I hacked together some modeline settings.

The card itself configured with no issues.[/QUOTE]
 [quote=me]Sometimes, before the GUI boots and after it shuts down, most of the screen locks up and all that's happening is differently colored dots, that are probably supposed to be very small letters. The visual effects in Totem and a few games (chromium) are choppy. I haven't yet tried playing videos.[/quote]
That's about all I can say. Also, i think that the text mode problem might be unrelated to the graphics card. The games and effects are definitely gc-caused.

---

