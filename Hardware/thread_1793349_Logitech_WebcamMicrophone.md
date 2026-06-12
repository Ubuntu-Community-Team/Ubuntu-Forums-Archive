---
title: "Logitech Webcam/Microphone"
date: 2011-06-29
forum: Hardware
---

### Post by ChuckyZ28 on 2011-06-29
I recently upgraded from 10.04 to 10.10 and 11.04 and in doing so my computer no longer recognizes the microphone associated with the webcam. I remember when I bought the microphone back in 10.04 I plugged it in, went to the sound area and changed to the usb mic for default input. But it is not showing up as an option any more. Any ideas on how to fix this?

---

### Post by dabl on 2011-06-29
You need to have the snd_usb_audio module loaded.

```
sudo modprobe snd_usb_audio
```

The next level of investigation would be a conflict between your onboard sound chip and the webcam.  So, install alsamixergui and then I also use pavucontrol (on Kubuntu/KDE). I'm not sure what your Gnome interface to the sound system looks like.  But the idea is you may need to mute the onboard chip, as an input source, while using the mic on the webcam.

---

