---
title: "Bluetooth headset AVRCP only partially works"
date: 2013-01-27
forum: Hardware
---

### Post by bdw on 2013-01-27
I have a Kinivo BTH-220 Bluetooth headphones with a Kinivo BTD-400 Bluetooth USB Bluetooth dongle.  The headphones work great with A2DP and HFS audio, but the AVRCP profile is sporadic.

I am running Kubuntu 12.10.

The AVRCP (Bluetooth Remote) only partially works, depending on the applications running:

VLC 2.0.6 - will not work at all
Amarok 2.7 - Next/Previous works but not Pause/Play
Rhythmbox 2.97 - Next/Previous works but will only Pause.  Play will not work.

I do have Pulseaudio running.

I did run xev and I tested the controls on my headphones.  I now have the following in ~/.Xmodmap based on the keycodes returned from xev:

```

keycode 209 = XF86AudioPause
keycode 208 = XF86AudioPlay
keycode 171 = XF86AudioNext
keycode 173 = XF86AudioPrev

```

But the AVRCP issue is not resolved, alas...

---

