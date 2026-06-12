---
title: "Audio Outputs detected inconsistently"
date: 2020-12-10
forum: Hardware
---

### Post by yaminb on 2020-12-10
HI all,

I'm having an issue where my audio outputs are not detected consistently. 
I generally either use
1. HDMI audio out (monitor speakers)
2. Headset (via audio jack)

The headset is always detected correctly. 
It's the HDMI audio out that is finicky. Sometimes it won't be detected on a fresh boot (Even with monitor on). Sometimes it won't be detected coming out of sleep.

My workaround so far is to do a:
```
pulseaudio -k
```

This takes a good 5-10 seconds before things reset and I can see all my audio devices. 

Anyone have any ideas on how to fix this.
1. Either detect it correctly always
2. Have a better way to refresh the audio outputs? I had investigated one way, which I seem to have lost track of. It seemed to work better, but it resulted in additional entries each time I ran it. I should note that I use the following extension to set my audio outputs.
[https://extensions.gnome.org/extension/906/sound-output-device-chooser/](https://extensions.gnome.org/extension/906/sound-output-device-chooser/)

Edit. I think the other way I tried was:
> pacmd unload-module module-udev-detect && pacmd load-module module-udev-detect

---

