---
title: "Sound not working on Dell laptop"
date: 2004-11-21
forum: Hardware &amp; Laptops
---

### Post by calisto on 2004-11-21
HI guys

I am a newbie to linux. I am having problem getting the sound to work on DELL inspiron 4150 laptop with ubuntu warty (2.6.8.1-3-386) installed. Not sure what my sound card is but the driver is Crystal CS4205 WDM Driver. Below are some info that might be helpful:

**run lspci gives:**
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: Cirrus Logic: Unknown device 5959
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at d800
        I/O ports at dc80 [size=64]

I believe the sound card is detected by the Kernel but /proc/asound/cards tells me otherwise:

**run cat /proc/asound/cards gives:**
--- no soundcards ---

**run alsactl restore gives:**
alsactl: load_state:1134: No soundcards found...

**run lsmod | grep snd gives: **
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

from what I ve read i810_audio sound module can be used for Crystal CS4205. and snd_intel8x0 is ALSA equivalent of i810_audio of OSS.

I am not sure why /proc/asound/cards says no sound cards. Is my sound card deteced by the Kernel? or could this be a driver problem? Please help.

Thanks so much

---

### Post by duff on 2004-11-22
[http://ubuntuforums.org/showthread.php?t=4258&highlight=acpi_irq_isa%3D7](http://ubuntuforums.org/showthread.php?t=4258&highlight=acpi_irq_isa%3D7)

---

