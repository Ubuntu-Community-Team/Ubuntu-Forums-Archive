---
title: "no sound"
date: 2009-01-07
forum: Hardware
---

### Post by Embiggens on 2009-01-07
I'm trying to get sound from an onboard intel audio controller.  I'm working with an old desktop, and I'm running 8.04.  Recently, I swapped in a new motherboard (on which the audio is integrated), so I'm wondering if my alsa configuration is messed up because of this.  

Output from "lspci -v" (just the relevant part):
```
00:1f.5 Multimedia audio controller: Intel Corporation 6300ESB AC'97 Audio Controller (rev 02)
	Subsystem: DFI Inc Unknown device 1001
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e000 [size=256]
	I/O ports at e400 [size=64]
	Memory at fb202000 (32-bit, non-prefetchable) [size=512]
	Memory at fb203000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

Output from "aplay -l":
```
card 0: I6300ESB [Intel 6300ESB], device 0: Intel ICH [Intel 6300ESB]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I6300ESB [Intel 6300ESB], device 4: Intel ICH - IEC958 [Intel 6300ESB - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I feel like there's something messed up about having the device listed twice, but feelings are all I have at this point. 
I also see 2 cards elsewhere, in this case I think I'm still looking at my old card: 

output from "cat /proc/asound/cards"
```
 0 [I6300ESB       ]: ICH4 - Intel 6300ESB
                      Intel 6300ESB with ALC202 at irq 21
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5

```

So I've tried *a lot* of the common advice- I'm 80% sure I've got the right driver (snd_intel8x0), its module seems to be loaded correctly, and I've made sure nothing's muted.  Does anyone have any ideas?  Thanks.

---

