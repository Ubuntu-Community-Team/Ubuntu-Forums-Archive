---
title: "No sound in 9.04 Realtek ALC889 (Acer 8935G)"
date: 2009-11-14
forum: Hardware
---

### Post by mrkazoodle on 2009-11-14
Hi

Yet another Acer Aspire 8935G problem, is it just me or is Acer not the best manufacturer when it comes to Ubuntu?

I installed 9.04 through wubi and I can't get any noise out of my built-in 5.1 speakers.
I tried unmuting alsa mixer and also tried to add my username to the /etc/group

Though when I booted the 9.10 live cd, I could play the sample audio file without any problem.
Maybe I could update some sound related packages that have been upgraded in 9.10?

here's aplay -l
```

**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: Intel [HDA Intel], apparaat 0: ALC889 Analog [ALC889 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 1: HDMI [HDA ATI HDMI], apparaat 3: ATI HDMI [ATI HDMI]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

```

---

