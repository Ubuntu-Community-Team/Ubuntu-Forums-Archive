---
title: "m-audio fast track ultra not managed properly by ubuntu"
date: 2013-06-01
forum: Hardware
---

### Post by baskak on 2013-06-01
i have filed a bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1186512](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1186512)
the problem is as follows:
there's an artificial spatilization when using usb multichannel audio interface. in 12.10, in the "sound settings" window it did manifest itself as "analog surround 7.1" profile, which is inadequate (i have 2.0 setup) and it applies some bombastic fx (reverberation?) and virtual channels to the stereo. in 13.04 i don't see the "analog surround 7.1" label anymore.
it also has no input.
there's only this fake surround profile available. seemingly it tries to put all channels (with reverbs) into two physical channels if it detects it's a multichannel device. and it happened specifically since 12.10, cause with 12.04 i had no problem. 12.04 had no "analog surround" profile forced on it.
there are some reverbed virtual channels (side l, side r and center) added to outputs 1 and 2 (why?), and controls for balance and "distance" are entangled (moving one moves the another). also i have NO analog surround 7.1 setup.
there are no other options.
perhaps somebody did manage to solve it outside the bug-tracking procedure.

---

### Post by stevegh on 2013-06-01
If you install the ALSA mixer through the software center, and run it you'll notice the USB Mixer and the huge number if channels. I just adjusted the Effect slider up and then down, even though it was already set to 0, and after doing so the reverb went away. Hope this works for you as I was kinda bummed after just installing ubuntu on my desktop!

---

