---
title: "strange sound problem"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by Hieronymus on 2005-05-01
I'm working with the 64bit (hoary hedgedog 5.04) and have the following problem:

I have sound when I start up, that is I have system sounds, but I have no sound when playing video/mp3/ogg etc. I have checked the properties of alsa mixer and volume is up. 
I have alsa selected in gstreamer-properties but when I try to test I get an error saying: Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'

I hope somebody can help me out before my hair turs gray

My card is recognised properly:

lspci output for audio
```

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)

``` 

dmesg output for audio
```

intel8x0_measure_ac97_clock: measured 63207 usecs
intel8x0: clocking to 48000
[CODE]

lsmod output for audio
[CODE]
snd_intel8x0		   34368  2 
snd_ac97_codec		 76704  1 snd_intel8x0
snd_pcm_oss			53668  1 
snd_mixer_oss		  19072  1 snd_pcm_oss
snd_pcm			    96012  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer			  24968  1 snd_pcm
snd				    55400  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore			  11168  2 snd
snd_page_alloc		 10888  2 snd_intel8x0,snd_pcm

```

---

### Post by lucus on 2005-05-01
the endless qualms with sound....
i feel your frustration, i was almost ready to throw my laptop like a frisbee.
i did a modprobe with all the specifics in it and then my sound miraculously worked

modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 
port=0x538 sb_port=0x220 wss_port=0x530

so hey... give it a try (with all your specifics inserted properly) and it may work.... if that doesn't work... say a prayer

---

