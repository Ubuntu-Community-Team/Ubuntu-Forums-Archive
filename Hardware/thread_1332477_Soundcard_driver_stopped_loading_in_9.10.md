---
title: "Soundcard driver stopped loading in 9.10"
date: 2009-11-20
forum: Hardware
---

### Post by PsyberS on 2009-11-20
My soundcard seems to not be loading drivers all of a sudden.  I know it worked fine in 9.04 and I am fairly certain (though neither I nor my girlfriend can seem to recall 100% clearly) that it worked after upgrading to 9.10.  

At any rate it appears to be that it cant identify my model now.  Here is my relevant information.  Any ideas?  I did some searching and know I can specify the model in /etc/modprobe.d/alsa-base.conf but I am unsure what to put in there!

In dmesg I see this:

[458799.874929] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[458799.906154] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...

Here is my sound card identified by lspci:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

---

