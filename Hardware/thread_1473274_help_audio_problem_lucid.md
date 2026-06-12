---
title: "help audio problem lucid"
date: 2010-05-05
forum: Hardware
---

### Post by cosmicbuff on 2010-05-05
installed lucid in my compaq v6106 au,
found that after reboot my audio doesnot work. there are no devices listed under audio properties.

i have a MCP 51 nvidia card for audio. (Nvidia go 6150) and installed propirietary drivers for graphics. everything is working fine except for the audio. I did not have problems in karmic and jaunty for the same laptop

my lspci -v output for audio and it says intel!!

```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Device 30b7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

how do i fix that..

---

### Post by lidex on 2010-05-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by cosmicbuff on 2010-05-06
thank you lidex for support,
but i have reverted back win for now. i encountered too many problems in this release.just dont have much time to sort all these out.

in just one day,
had gdm froze many times.
couple of unresponsive programs, 
shutdown bug,had to terminal to shutdown.
the ugly flickering by plymouth,with nvidia drivers
and not to mention the sound problem.


the worst release i ever tried till date,but my partion will be intact,may be i ll come back and try say after a month or two.

---

