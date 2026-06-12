---
title: "Audio Failure"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by mmoo9154 on 2009-06-02
I recently did a clean install of Ubuntu 9.04 (AMD64) (Xubuntu to be precise).  Things progressed quite nicely, but the audio is completely dead.

This seems like a pretty big failure since audio is so important, so I'm hoping someone can help.  More importantly, I want to help get this fixed for the next release so others don't have to go through this pian.

I'm a relative n00b to Ubuntu, but I'm a developer and can find my way around with a little bit of help.

Here's the output from lspci -v:

> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0145
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at db300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

The laptop I have is a brand new Acer Aspire 8930.  It's a super hot desktop replacement, by the way.  Huge screen!

Does anyone have any ideas how to solve this?  If not, any ideas where I can spelunk from here?

-Mark

---

### Post by afrodeity on 2009-06-02
Please refer to the [Pulseaudio FAQ and HOWTO]("http://ubuntuforums.org/showthread.php?t=789578"). Its in the multimedia forums.

---

