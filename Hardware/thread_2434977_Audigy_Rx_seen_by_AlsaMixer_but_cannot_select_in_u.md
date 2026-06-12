---
title: "Audigy Rx seen by AlsaMixer but cannot select in ubuntu settings"
date: 2020-01-14
forum: Hardware
---

### Post by lemoonstar on 2020-01-14
I recently updated to Ubuntu 19.10 (from 19.04) and since then Ubuntu wants to output the sound via my HDMI monitor.
looking in the settings i cannot select my sound blaster Audigy Rx sound card. I then looked in AlsaMixer where it showed up. after some search i still cannot find any way of fixing it.
I have however already confirmed that the driver is installed and associated with the card:
(part of the output from sudo lspci -v)
```
05:00.0 Multimedia audio controller: Creative Labs CA0108/CA10300 [Sound Blaster Audigy Series]    Subsystem: Creative Labs SB1550 Audigy 5/Rx
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at d000 [size=64]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: snd_emu10k1
    Kernel modules: snd_emu10k1
```
 i hope that someone here can help me. i'll happily provide any needed information.

---

### Post by lemoonstar on 2020-01-14
ok, somehow a 7th restart fixed it...... i really don't know what the problem was

---

