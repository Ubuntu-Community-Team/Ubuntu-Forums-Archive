---
title: "Cirrus Logic sound card on Thinkpad X21 not working?"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by zratis on 2007-06-09
I can't get sound to work.  I get the red dot on my speaker icon indicating something's wrong with sound.  When double clicked I get the message: "No volume control GStreamer plugins and/or devices found."

lspci | grep audio shows me:
00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)

I was looking around for a driver for this sound card, but no luck so far.  In my Device Manager I see it listed as Crystal CS4281 PCI Audio, with details showing:
Vensor: Cirrus Logic
Device: Crystal CS4281 PCI Audio
Status: Status
Bus Type: PCI 
Device Type: Unknown 
Capabilities: Unknown

Under PCI tab:
OEM Vendor is IBM
OEM Product: Unknown (0x0183)

I have Ubuntu 7.04, on ThinkPad X21.

System is great, I would like it a lot more with sound!

Thanks in advance for any pointers with this problem.

---

### Post by neptho on 2007-06-09
Open a terminal, and run this command:
```
aplay /usr/share/sounds/question.wav 
```

Does it make any sound or show any errors?

Also, paste back the contents of running:
```
cat /proc/asound/pcm
```

---

### Post by zratis on 2007-06-09
Thanks for your help.

The first commands produces:

ewa@ewa-laptop:~$ aplay /usr/share/sounds/question.wav
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:550: audio open error: No such device


The second one's output is nothing at all.

Regards,
zratis

---

### Post by trippinnik on 2007-06-09
have you checked the bios settings?  my g/f has the same laptop and i've heard sound coming out of it.  make sure it's enabled, you have plug and play OS set to yes, and IRQs are set to auto.

---

### Post by zratis on 2007-06-09
Thanks.  Unfortunately I couldn't find my PnP config in BIOS.  I did find IRQ settings, and switched them to Auto from 11, but it did not work.


Also, another error showed up in addition to the original one that might give better clues.  I think it's the same cause.

It says:

"The volume control did not find any elements and/or devices to control.  This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

It also says how to remove the volume control icon from the panel...

Any help appreciated.

---

