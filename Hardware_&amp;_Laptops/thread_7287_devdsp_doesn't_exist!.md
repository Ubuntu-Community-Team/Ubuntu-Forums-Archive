---
title: "/dev/dsp doesn't exist?!"
date: 2004-12-05
forum: Hardware &amp; Laptops
---

### Post by flamesrock on 2004-12-05
Hi,

Support for my sound card (sblive!) has just been added in alsa-1.05a..the version that comes with ubuntu. The installer correctly detected it, but it will not recognize the device...

I did a modprobe snd-emu10k1 (my chipset) and it gives me the following output:

 ```
aaron@ubuntu:~ $ modprobe snd-emu10k1
WARNING: Error inserting soundcore (/lib/modules/2.6.8.1-3-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_util_mem (/lib/modules/2.6.8.1-3-386/kernel/sound/synth/snd-util-mem.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.8.1-3-386/kernel/sound/pci/ac97/snd-ac97-codec.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.8.1-3-386/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.8.1-3-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
FATAL: Error inserting snd_pcm (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-pcm.ko): Operation not permitted
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.8.1-3-386/kernel/sound/core/snd-rawmidi.ko): Operation not permitted
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.8.1-3-386/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Operation not permitted
``` 

**What does it all mean, and how can I get it to work?!**  :evil: Ubuntu says that /dev/dsp, /dev/mixer do not exist, but I know they do..

better yet, support for my sound card is supposed to be MUCH better in alsa-1.06. However, I can't find this package in debian universe... how can I install it without compiling source and messing with the kernal?

-thanks in advance for any help.

---

### Post by p!=f on 2004-12-05
You have to use modprobe under root privileges
```

sudo modprobe snd_emu10k1

```

---

