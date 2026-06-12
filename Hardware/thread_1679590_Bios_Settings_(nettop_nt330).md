---
title: "Bios Settings (nettop nt330)"
date: 2011-02-01
forum: Hardware
---

### Post by ajb_camvine on 2011-02-01
Hi.

We are attempting to set, or preserve, some of the non-standard bios settings for an embedded installation.

Specifically we want to change the "Restore on AC Power Loss" and "Full Screen Logo Display" options.

However - direct access via /dev/nvram causes the bios to detect tampering (bad checksum) and restore defaults.
Other tools (such as AFUDOS) claim to store the NVRAM settings, but do not affect these two.

Presumably the extra data I need to alter lives in an extended area - but I cannot find any guide to accessing this.
(There is a defunct sourceforge project NVRAM-WakeUp which knows how to access a few specific motherboards, but not this one)

Does anyone have any information newer than 2002?

The bios is American Megatrends (v02.61) and it claims that the motherboard is JTX-N (Foxconn)

If anyone can suggest a better forum to ask this in, that would also be helpful.

---

