---
title: "Sound stopped working after upgrade"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by julian on 2005-02-10
I am running Warty on a Dell Inspiron 500m laptop.  When I first installed Ubuntu sound worked fine, but sometime over the past few weeks it has stopped working.  I suspect it stopped after I performed an upgrade.

Sound modules are loaded:

snd_intel8x0m          18632  0
snd_intel8x0           33068  0
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  10 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  1 snd

But there don't seem to be the right sound devices in /dev, e.g. there is no /dev/mixer, /dev/dsp.  The only things that are sound related are /dev/snd/controlC0 and /dev/snd/timer.  My understanding is that since Ubuntu uses udev then the device nodes should be automatically created.

I also don't see anything sound related in dmesg.

Any clues as to what is going on.

Thanks

Julian

---

### Post by julian on 2005-02-10
I found the answer.  I noticed that drivers were now failing to grab irq 7 during boot (also affecting my wireless network card).

Adding "acpi_irq_isa=7" to the kernel parameters fixes the problem.

Julian

---

