---
title: "Ubuntu not recognizing my sound blaster x-fi sound card"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by JoakimW on 2009-08-25
Hi everyone. I'm quite new to Ubuntu, but not completely green.

My problem is that I have an on board sound card, that I can get working just fine. But it's kinda silly when I cant get Ubuntu to recognize my $100 x-fi card. I've tried looking through the sound set-up, couldn't really find anything about it. So I checked out [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and found out with "lspci -v | less" that it's plugged in correctly since I get:

05:01.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Device 0021
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d000 [size=32]
        Memory at e8000000 (64-bit, non-prefetchable) [size=2M]
        Memory at e4000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

The on board sound card also shows:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 02)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f2100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

How can I make my better sound card take the place of the on board one? I tried disabling the on board one in the BIOS, but that left me with no options to play anything at all.

Thanks in advance.

---

### Post by running_rabbit07 on 2009-08-25
This [link]("http://www.opensound.com/download.cgi") may be helpful.

---

