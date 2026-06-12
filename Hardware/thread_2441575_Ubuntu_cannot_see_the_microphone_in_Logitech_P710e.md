---
title: "Ubuntu cannot see the microphone in Logitech P710e speakerphone over bluetooth"
date: 2020-04-24
forum: Hardware
---

### Post by mrjohnc on 2020-04-24
Hi all

I have a Logitech P710e speakerphone, when I connect it via bluetooth it can only see the speaker, not the microphone, but when I connect it via USB it sees both. Is there anything I can try to do to encourage it to be able to see the microphone over bluetooth?

I'm using Ubuntu 19.10 (Ubuntu 20.04 has some really bad graphical glitches for me so haven't updated). 

Thanks very much

---

### Post by CelticWarrior on 2020-04-24
As with any other Bluetooth device with a microphone, you need to change the default A2DP (HiFi Stereo, no Mic) to "hands-free" (HFP) (Mono + Mic) in order to use the microphone.

---

### Post by mrjohnc on 2020-04-24
Thanks very much for the reply, how would I do this? Also just to make sure I understand if I enable the microphone it would change from stereo to mono? (it has a headphone jack which I use and don't really want one of the ears to stop working).

---

### Post by CelticWarrior on 2020-04-24
> **mrjohnc said:**
> Thanks very much for the reply, how would I do this?

System Settings > Sound
In the output panel you should see the Bluetooth device select and below that a dropdown "Configuration" menu.

> Also just to make sure I understand if I enable the microphone it would  change from stereo to mono? (it has a headphone jack which I use and  don't really want one of the ears to stop working)

Yes, it changes from Stereo to Mono. The current Bluetooth technology allows 2 channels only. It's either L+R or Mono+Mic.
I don't know how yours work. With headphones and the same profiles it just lowers noticeably the audio quality but the (mono) output is the same for L and R. Of course, this is used for voice applications only.

---

