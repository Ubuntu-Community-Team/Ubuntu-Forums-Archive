---
title: "Sound configuration issue Dell laptop"
date: 2014-07-29
forum: Hardware
---

### Post by jensvdw on 2014-07-29
Hi,

I am running Ubuntu 14.04 on a Dell Studio 1745. Today, my sound configuration seems to be "missing". Sound still works, I can enter alsamixer. However, the sound options in the GUI does not show any "play through" options. The sound indicator in the menu bar is also not showing. I have found some other topics with similar problems, although the posted solutions were either outdated or not applicable (or I was too dumb to put them into practice).

Any help would be very much appreciated!

---

### Post by Yellow Pasque on 2014-07-29
Try resetting and restarting pulseaudio:
```
rm -r ~/.config/pulse
pulseaudio -k
```

If that doesn't work, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by jensvdw on 2014-07-31
Thank you for you repy.

I followed your advice, and also reinstalled ubuntu-desktop. This seemed to do the trick.

---

