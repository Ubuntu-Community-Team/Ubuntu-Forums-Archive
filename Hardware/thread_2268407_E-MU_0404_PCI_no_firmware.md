---
title: "E-MU 0404 PCI no firmware?"
date: 2015-03-08
forum: Hardware
---

### Post by abraham-sewill on 2015-03-08
I bought this particular card years ago and held onto it thinking it would get support in ubuntu.  Alsa has it working as of several years ago, but whatever firmware packages are in the ubuntu repositories still don't have the firmware.  I didn't expect I'd have to re-compile alsa every time I do an upgrade that effects alsa or the kernel version.  Anyway, here's what I get from dmesg:

```

[   17.170169] snd_emu10k1 0000:04:06.0: enabling device (0000 -> 0001)[   17.170269] snd_emu10k1 0000:04:06.0: emu1010: Special config.
[   17.170356] snd_emu10k1 0000:04:06.0: emu1010: EMU_HANA_ID = 0x3f
[   17.717033] snd_emu10k1 0000:04:06.0: Direct firmware load failed with error -2
[   17.717037] snd_emu10k1 0000:04:06.0: Falling back to user helper
[   17.868643] snd_emu10k1 0000:04:06.0: emu1010: firmware: emu/emu0404.fw not found. Err = -12

```

What needs to happen to get the 0404 PCI alsa firmware package into ubuntu and what can I (or anyone) do to help accomplish that?  Perhaps I'm just lacking information or missing a step.  Is there a better way to get this card working in Ubuntu?

---

