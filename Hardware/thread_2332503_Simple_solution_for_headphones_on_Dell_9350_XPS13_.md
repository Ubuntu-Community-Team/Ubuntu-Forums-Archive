---
title: "Simple solution for headphones on Dell 9350 XPS13 with 16.04 Kernel 4.4.0-31-generic"
date: 2016-08-01
forum: Hardware
---

### Post by lindeling on 2016-08-01
Here is a simple solution if your headphones are not working on Dell 9350 XPS13 with 16.04 Kernel 4.4. Works also in kubuntu
```
echo "options snd-hda-intel model=dell-headset-multi" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

On kubuntu a little bit annoying, but if you have plugged in the headphone click first the speaker symbol in the kicker (lower right corner). Turn on and off in the "Capture devices" section the "Built-in Audio Analog stereo"

---

