---
title: "thinkpad_acpi doesn't work"
date: 2011-02-19
forum: Hardware
---

### Post by Eisdiele on 2011-02-19
Hi,

I just tried to run thinkfan on my T410 under Ubuntu 10.10 when I remembered that I need to change something in the thinkpad_acpi.conig file. When I remember correctly this should be under etc/modprobe.d/thinkpad_acpi.conig. But I can't find the file anywhere.

lsmod | grep thinkpad says:

```
thinkpad_ec             5522  1 hdaps
thinkpad_acpi          67659  0 
nvram                   6342  1 thinkpad_acpi
snd                    49038  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
led_class               2633  2 thinkpad_acpi,sdhci

``` 

So the Kernel module should be loaded? It worked perfectly under 10.04. Did I forget to do something? Sorry if I missed something simple but I don't get it at the moment.

Thanks

ps. I can only read the cpu temperature as well, so the kernel module seems not to work at all?

---

### Post by Eisdiele on 2011-02-25
no ideas? I'm still stuck and the fan is really annoying. Anything I can post to help?

thanks

---

