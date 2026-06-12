---
title: "microphone not working on an HP dv7"
date: 2012-01-19
forum: Hardware
---

### Post by biodiesel-bri on 2012-01-19
I have an HP dv7-6b78us and I wasn't able to get the mic working.  =D>

Here's my specific sound card:
```
cat /proc/asound/card0/codec* | grep Codec
Codec: IDT 92HD81B1X5
Codec: Intel CougarPoint HDMI
```

The standard fix given was to edit /etc/modprobe.d/alsa-base.conf with:
```
options snd-hda-intel model=ref
```

That enabled the beats audio subwoofer but the microphone failed to work.  I dug around and came across this which worked:
```
options snd-hda-intel model=dell-s14 power_save=0 power_save_controller=N
```

The mic is a bit crackly in Skype but it works; the tradeoff is that the headphone jack now doesn't shut off the speakers.  If anyone comes across a better solution please let me know.

---

