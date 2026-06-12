---
title: "Problem with sound card"
date: 2010-10-31
forum: Hardware
---

### Post by momas1200 on 2010-10-31
hi all
my sound card has disabled after removing alsa driver
i reinstall alsa driver but it not work

> momas@momas-desktop:~$ sudo aplay -l
aplay: device_list:235: no soundcards found...> lspci -v | less

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio C
ontroller (rev 01)
        Subsystem: Giga-byte Technology GA-8I945PG-RH Mainboard
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at e4200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>> find /lib/modules/`uname -r` | grep snd 
Nothing!

what should i do?

i have ubunutu 10.10 amd64

---

