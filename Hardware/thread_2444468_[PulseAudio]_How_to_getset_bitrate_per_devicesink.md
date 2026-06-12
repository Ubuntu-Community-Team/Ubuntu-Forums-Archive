---
title: "[PulseAudio] How to get/set bitrate per device/sink?"
date: 2020-05-30
forum: Hardware
---

### Post by aneganov on 2020-05-30
Is there a way to **know** what bitrate is used by a device or sink in PulseAudio?

And then is there a way to **configure** this bitrate?

I have an ugly problem now with different bitrates mixed into some broken stream. 

Basically I stream Desktop Audio into an external mixer device (Yamaha AG03) where the sound is mixed with Microphone (connected to the same mixer) and then it's sent back to the PC. And where it comes absolutely broken - with gaps, wrong pitching/speed and etc.

So I feel like I need to configure PulseAudio devices somehow. But currently it looks like a damned blackbox: UI provides no info, pavucontrol too. 

(In parallel I'm trying to switch to a JACK-only setup, but it provides its own *refined* *tortures* for a user either...)

---

### Post by CatKiller on 2020-05-30
The configuration is a couple of quite well documented text files, and pactl and pacmd are quite powerful. The GUI parts are a bit limited. 

> **aneganov said:**
> (In parallel I'm trying to switch to a JACK-only setup, but it provides its own *refined* *tortures* for a user either...)

Ah, yes, JACK. Fun. 

FWIW, going strictly JACK-only is a mistake. You can have a JACK-only workflow and PulseAudio will be suspended automatically for the duration. Some people naïvely try to remove PulseAudio in favour of JACK or ALSA, and it just gives them headaches.

And some point in the future we'll be getting PipeWire as a PulseAudio that also handles video, and with the low latency of JACK, but it's not here yet.

---

