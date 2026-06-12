---
title: "Sound problems..."
date: 2008-10-02
forum: General Help
---

### Post by wardanian on 2008-10-02
Okay, rather seriously, I'm freaking tired of fiddeling around with my sound getting absolutely nowhere. Here's the deal: I want my microphones to work as they did back in Windows, I have one microphone that I have in the line-in part of my integrated soundcard, and a usb-webcam from Logitech with a built-in microphone. 

None of my programs recognize the microphones, even though the soundcard clearly says I have them installed and everything, in skype it cannot even play things. I was making a test call and I got some "Error in playback device" thing. Back in Windows I used Realtek '97 drivers, and everything worked.

How do I do this in Ubuntu? Running 8.04, Hardy Heron.

---

### Post by Calmatory on 2008-10-02
"Playback device *" error suggests that the device is already in use(OSS can cause this) or unavailable.

Can you get any sound out from the speakers? Or is it just mic not working?

If the sound plays, restart the machine, don't open up any programs except Skype and try again.

---

### Post by wardanian on 2008-10-04
Doesn't work, my microphone is still trashed. I do have sound - I use PulseAudio as my "driver" or w//e. ALSA, OSS and that Intel thingy I've got gives errors upon testing.

---

### Post by wardanian on 2008-10-05
Another problem - timidity doesn't seem to want to co-exist with pulseaudio.

Edit: Got the Skype *sound* working, but none of the inputs work.

---

