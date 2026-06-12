---
title: "CPU Runs at half speed with a Toshiba Libretto L5"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by gnu2tux on 2006-01-08
Hi everyone,

I've been hunting the net for the answer to this, but I can't find it anywhere. I'm sure it's to do with the toshset information, but basically I have an ACPI only Toshiba Libretto L5 laptop.

Sorry about the length of this post, but most of it is debugging that would just get asked of me anyway.

The laptop runs at around 400MHz, but it's supposed to be 800MHz. The toshset has a feature for fast or slow mode, depending upon how long you want the batteries to last. Problem is, this mode can't be set :(

Here is a bit of debugging:

toshset -v -q gives:

```

machine id: 0xfc8b    BIOS version: 1.40    SCI version: 200.196
toshset version: 1.70                  Toshiba Model: Libretto L5
error when querying feature: battery save mode: FAILURE
error when querying feature: power source: FAILURE
HCI/SCI access mode: kernel            LCD backlight: on
error when querying feature: select bay: FAILURE
error when querying feature: select bay lock: FAILURE
error when querying feature: IR port: FAILURE
error when querying feature: USB legacy mode: FAILURE
error when querying feature: USB FDD emulation mode: FAILURE
fan: off                               LAN controller: enabled
error when querying feature: sound logo: FAILURE
error when querying feature: startup logo: FAILURE
error when querying feature: HibInfo: BIOS size: FAILURE
error when querying feature: HibInfo: memory size: FAILURE
error when querying feature: HibInfo: VRAM size: FAILURE
error when querying feature: Hibernation LBA: FAILURE
Video out: internal: LCD               flat panel:  1280x600, 18 bit TFT
error when querying feature: system beep: FAILURE
lcd brightness: bright                 lcd intensity: 2/7
error when querying feature: CPU speed: FAILURE
**error when querying feature: CPU sleep mode: FAILURE**
error when querying feature: Display stretch: FAILURE
error when querying feature: CPU cache: FAILURE
error when querying feature: cache policy: FAILURE
error when querying feature: speaker volume: FAILURE
error when querying feature: battery alarm: FAILURE
error when querying feature: panel alarm: FAILURE
error when querying feature: panel power: FAILURE
error when querying feature: hard disk auto-off time: FAILURE
error when querying feature: display auto-off time: FAILURE
error when querying feature: power-up mode: FAILURE
battery percent: 26%                   cooling method: performance
error when querying feature: power-up alarm: FAILURE
error when querying feature: auto-off time: FAILURE
error when querying feature: parallel port mode: FAILURE
error when querying feature: second battery: FAILURE
error when querying feature: Standby time: FAILURE
error when querying feature: Hibernation: FAILURE
error when querying feature: Pointer: FAILURE
boot method: floppy->CDROM->hard disk
...

```

I note that /proc/acpi/toshiba contains only entries for fan, keys, lcd,
version and video, probably explaining the above output.

I attempt to set it to 'fast' mode with the -cpu flag but I
get the following error:

```

% toshset -cpu 1 -v
SciFeature:action: error setting CPU speed
        SciSet returned: FAILURE

```

This is the end of my kernel audit output when I insert toshiba_acpi manually:

```

[4297632.326000] Toshiba System Managment Mode driver v1.11 26/9/2001
[4299557.707000] Toshiba System Managment Mode driver v1.11 26/9/2001
[4299565.835000] toshiba_acpi: Toshiba Laptop ACPI Extras unloaded
[4299571.654000] Toshiba System Managment Mode driver v1.11 26/9/2001
[4299640.786000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[4299640.788000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[4299640.930000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[4299640.930000] toshiba_acpi: ktoshkeyd will check 2 times per second
[4299641.302000] toshiba_acpi: Dropped 0 keys from the queue on startup

```

If you could help out I would be much obliged! - Even if you know someone else
to contact (perhaps someone at Ubuntu with Toshiba knowledge or something?). I know the machine is working fine speedwise because when it's in Windows the speed settings are set for performance, and it definitely feels about double the speed.

I used to run 5.04 on that machine, and I don't think the problem existed there (but I may be wrong, it was a long time). I'm running 5.10 now with all updates.

Please help - without a fix, I can't use this Laptop with Linux :(

Regards,

        Alistair Ross

---

### Post by runderwo on 2006-09-12
My friend had this problem with a 7010CT (also ACPI).  The solution was to use the Toshiba Windows utility and set the CPU settings to "max" or something similar in there.

---

