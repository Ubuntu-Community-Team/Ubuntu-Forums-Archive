---
title: "Sound Won't Un-mute"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by amtur_poet on 2008-01-14
I finally think that I got my sound working, but when I adjusted the volume, the sound muted, and now I can't un-mute it. I'm SO close to fixing my sound problem, so if someone who knows about this could give me a solution, it would be very appreciated. Thank you.

EDIT: Never mind, I guess it's just an icon that stays there. The sound still kind of works. I have sound, but it's very loud, and I can't control it.

---

### Post by tgalati4 on 2008-01-15
Perhaps you have the Line-Level activated.  It's a fixed signal used to power stereo equipment.  Try activating all of the channels in Edit-->Preferences of the Volume Mixer so you can play around to find the proper channel to control volume.  Also, some sound cards switch the ports around.  Make sure you are plugged into the correct port (headphone versus Line-Out).

---

### Post by amtur_poet on 2008-01-16
I have to do something in a certain order to get sound to come out at all. I have to start Ubuntu with the headset plugged in, then when it's started up, I have to unplug them, and plug them back in. Then, sound will come out very loudly, and I can't control it, but it will come out. It also doesn't recognize my laptop's built-in speakers.

---

### Post by amtur_poet on 2008-01-16
The only other channels are for the microphone.

---

### Post by amtur_poet on 2008-01-16
When I try to test the sound in ALSA, it gives me an error message saying "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."

The only setting that works for the test is the USB audio. [A side note, the sound works only in the test, and I can control it using the volume control setting. However, this doesn't work for any other application; only the test.]

Also, I saw that you could see the model of your sound card by running: > cat /proc/asound/card0/codec#* | grep Codec, but it gives me an error message saying "cat: /proc/asound/card0/codec#*: No such file or directory".

Could somebody tell me what this means?

---

### Post by amtur_poet on 2008-02-07
Nobody still has any idea on how to solve this?

---

