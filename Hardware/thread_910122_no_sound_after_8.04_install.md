---
title: "no sound after 8.04 install"
date: 2008-09-04
forum: Hardware
---

### Post by vong on 2008-09-04
I am using a xfx nforce 780i board with onboard sound.  When I booted up from the live CD, the sound was working.  Now the sound does not work after I have installed and applied updates.

The audio seems to be loaded (see lspci below)

[QUOTE="lspci"]...
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: Unknown device 0175:10de
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at cfff0000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
...[/QUOTE]

Any suggestions to how to go about fixing the problem?

---

### Post by vong on 2008-09-26
fixed :) (i wont say how it was fixed because its kinda embarrassing ;))

---

