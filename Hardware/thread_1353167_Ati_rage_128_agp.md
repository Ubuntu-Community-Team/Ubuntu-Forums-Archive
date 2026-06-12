---
title: "Ati rage 128 agp"
date: 2009-12-12
forum: Hardware
---

### Post by zcruzm on 2009-12-12
Hi!

I am new to Ubuntu and I am trying to configure it in an old machine. I am almost there and I'd like to pose a question.

The machine I am using is an old Athlon 1000 with a Transcend TS-AKT4 motherboard. I have a graphics card ATI Technologies Inc Rage 128 RF/SG AGP with 32 MB of RAM, and everything seems fine except for this message I get from Xorg.0.log:

> 
(II) R128(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x0305; Card 0x1002/0x5246]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(EE) R128(0): [agp] Could not bind
(WW) R128(0): [agp] AGP failed to initialize -- falling back to PCI mode.
(WW) R128(0): [agp] Make sure you have the agpgart kernel module loaded.Question 1: Does this mean that the graphics card is being used only as PCI and not as an AGP card? Can this have performance issues?

The message seems to imply that agpgart is not loaded, however, doing lsmod | grep agp shows:

> via_agp 7932 1
agpgart 34988 2 drm, via_agpwhich seems to me a confirmation that agpgart is there.

Can anybody please clarify a bit the situation? I've googled about agpgart but got no clear answer of what's going on.

Thanks,

Alberto

---

