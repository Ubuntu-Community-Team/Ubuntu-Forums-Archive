---
title: "Obtaining PID and VID of sound cards?"
date: 2010-11-22
forum: Hardware
---

### Post by jbreckmckye on 2010-11-22
Hi, I have a sound problem.

Effectively, I'm getting two sound cards being recognized as snd_hda_intel devices. The wrong one is being used by ALSA. I'm informed that I can specify ALSA indexes in a particular order, for instance by using the ALSA instruction

```

options snd-usb-audio index=1,2 vid=0x0ccd,0x0d8c pid=0x0028,0x000c

```

Unfortunately, I don't know any way to obtain the PID and VID values of my devices. Is there a *buntu-compatible command I can use that may tell me?

Thanks in advance.

---

### Post by Fafler on 2010-11-23
lspci and lsusb does just that.

---

