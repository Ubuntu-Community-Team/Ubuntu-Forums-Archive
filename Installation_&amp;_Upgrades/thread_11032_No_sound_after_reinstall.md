---
title: "No sound after reinstall"
date: 2005-01-13
forum: Installation &amp; Upgrades
---

### Post by Ndlovu on 2005-01-13
I've just reinstalled Ubuntu (Warty) on my IBM ThinkPad R30 laptop (model 2676PG1) and notice that the sound is not working now. The BIOS has been doing some strange things lately (switching and forgetting IRQ settings for PCI), and I'm wondering whether this is a hardware or software issue. I tried booting with the LiveCD and had no sound there either. When I use a microphone and try to tune the audio with GnomeMeeting, it does give a graphical indication of the sound, so it seems to be getting input but giving no output. Before reinstalling, the sound was working fine under Warty. It's a fairly stock installation, the only non-standard thing I installed was MyPasswordSafe (from binaries), but I can't imagine that would affect the sound at all. Back in my Windows days, Belarc Advisor identified the audio driver as being the ALi Audio Accelerator WDM driver, and the PCI controller as the ALi M5229 PCI Bus Master IDE Controller.

Any ideas? I've attached the outputs of aplay, lspci and dmesg. Thanks.

Rudi

---

