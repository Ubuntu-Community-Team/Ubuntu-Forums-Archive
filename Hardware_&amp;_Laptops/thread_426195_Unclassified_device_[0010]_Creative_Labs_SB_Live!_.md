---
title: "Unclassified device [0010]: Creative Labs SB Live! EMU10k1 (rev 04)"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by Innu on 2007-04-28
lspci -v:
```
01:06.0 Unclassified device [0010]: Creative Labs SB Live! EMU10k1 (rev 04)
	Subsystem: Unknown device 0010:0010
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at ac00 [size=32]
	Capabilities: <access denied>
```

cat /proc/asound/cards 
```
0 [Live           ]: EMU10K1 - SB Live [Unknown]
                      SB Live [Unknown] (rev.4, serial:0x100010) at 0xac00, irq 20

```

I have SB LIVE 5.1.
Somewhy it dosen't work. It loads snd_emu10k1 drivers automatically but no sound.

---

### Post by Innu on 2007-04-29
bring up my post

---

### Post by Innu on 2007-05-03
still need help

---

### Post by oxleyk on 2007-10-29
I have the same card and apparently it's still a problem with Ubuntu 7.10.

Kent

---

### Post by johnswb on 2007-12-30
I just installed ubuntu 7.10 and my sound works.  I have the same sound card as you guys.  I'm not sure why it is working for me and not you guys.  I did notice when playing video from a CD-rom the sound is choppy, but this could be my CD-rom is old.

00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs SBLive! 5.1 Model SB0100
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at 9000 [size=32]
        Capabilities: <access denied>

---

### Post by moddato on 2008-01-23
I have this sound device: 00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)... Same Problem!!

---

