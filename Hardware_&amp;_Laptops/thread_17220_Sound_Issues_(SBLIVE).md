---
title: "Sound Issues (SBLIVE)"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by JmSchanck on 2005-02-27
Ok yesterday sound just stopped working for me. I dont know exactly what I did but at some point I screwed something up, its not the card because when I boot into windows it still works. It had worked in Ubuntu flawlessly for 2 months so I first checked the Synaptic Commit Log, but nothing there seemed like something that would mess up a sound card. I grep'ed my history for apt-get and nothing there seemed harmful either.

running lspci shows the card:
```

0000:00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

0000:00:08.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)

```

and here is what sndstat says
```

john@ubuntu:~ $ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.4 emulation code)
Kernel: Linux ubuntu 2.6.8.1-5-686 #1 Sat Feb 12 00:50:37 UTC 2005 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Sound Blaster Live! (rev.10) at 0xc000, irq 169

Audio devices:
0: EMU10K1 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: EMU10K1 MPU-401 (UART)

Timers:
7: system timer

Mixers:
0: SigmaTel STAC9708/11

```

I'm thinking some setting got changed at some point so if anyone knows how I could have ubuntu detect the settings again (since it did such a nice job during the install) that would be awesome. or if you think theres another solution I'd be glad to hear that as well. thanks.

---

### Post by JmSchanck on 2005-02-27
Edit:// OK never mind I made a ton of tweaks and now it works again. For the most part i just reinstalled alsa, looked up my card on their website and followed the directions. Also when I ran "gstreamer-properties" regularly it was different from when i ran it with sudo.

---

