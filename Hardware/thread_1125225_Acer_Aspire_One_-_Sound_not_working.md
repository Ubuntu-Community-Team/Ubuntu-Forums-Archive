---
title: "Acer Aspire One - Sound not working"
date: 2009-04-14
forum: Hardware
---

### Post by jbeiter on 2009-04-14
Ubuntu 8.10

Sound was working when I first booted windows. Installed Ubuntu 8.10 using unetbootin. I can't seem to get sound working at all. PCM volume is up, nothing is muted in alsamixer. I recompiled alsa-driver, lib, and utils.. no good results.

I am seeing this in dmesg:
 HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.875069] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.957121] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   21.049022] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   21.156925] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
 HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.875069] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.957121] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   21.049022] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   21.156925] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
---------------------------------

in /etc/modprobe.d/alsa-base, I appended this as the last line:
options snd-hda-intel model=auto (tried model=acer too)

Other folks seem to be getting sound to work out of the box on this notebook. I can't figure out what I am missing. Any tips?

---

### Post by jbeiter on 2009-04-14
I tried recompiling the alsa drivers with all cards and added the following line to /etc/modprobe.d/options:

"options snd-hda-intel model=acer-aspire" (no quotes)

Still no change... I always have to do a "make install" after recompiling alsa for the wifi or wireless stops working too.

volume on everything is up.. nothing unmuted. Man I am stuck. I don't know what else to try.

---

### Post by jbeiter on 2009-04-14
sorry for the bump.. any suggestions at all??

---

### Post by Noblacktie on 2009-04-15
Sound works OOTB in Jaunty. Alternately, you could apply kernel 2.29 and ALSA 1.0.19 to your Intrepid install to get sound working.

But it's simpler to just install Jaunty :)

---

### Post by jbeiter on 2009-04-15
Thank you! I did compile/install alsa 1.0.19 but it still didn't work.

I ended up loading Jaunty using the netbook remix image ([https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)) and this was MUCH easier. Sound works and the wireless networking worked out of the box.

I am extremely impressed at the cost and performance of this setup.

The external mic isn't working yet but that seems to be a universal flaw at this point.

Thank you again for your suggestion!

---

