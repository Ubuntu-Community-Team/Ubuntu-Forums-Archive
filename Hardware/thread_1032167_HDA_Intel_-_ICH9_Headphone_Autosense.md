---
title: "HDA Intel - ICH9 Headphone Autosense"
date: 2009-01-06
forum: Hardware
---

### Post by h_box on 2009-01-06
Want to disable the speakers with headphone output enabled;

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

8.10 w/updates to the minute

I've searched through quite a few discussions of this problems and have tried various fixes in the form of modifying /etc/modprobe.d/alsa-base with snd-hda-intel options. 

- Tried the 'off-hook' switch & the headphone switch without the intended effect. 

- The 'headphone' switch does toggle the headphone output on and off.

- Adding the "6stack" option gives me control over 3 more outputs but they only change the volume of the various speakers on the laptop, the "front" seems to always be on.

However I have been unable to get the headphone output to function without the speakers.

Best and thanks for any input,

-JH

---

### Post by hotweiss on 2009-01-06
> **h_box said:**
> Want to disable the speakers with headphone output enabled;

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

8.10 w/updates to the minute

I've searched through quite a few discussions of this problems and have tried various fixes in the form of modifying /etc/modprobe.d/alsa-base with snd-hda-intel options. 

- Tried the 'off-hook' switch & the headphone switch without the intended effect. 

- The 'headphone' switch does toggle the headphone output on and off.

- Adding the "6stack" option gives me control over 3 more outputs but they only change the volume of the various speakers on the laptop, the "front" seems to always be on.

However I have been unable to get the headphone output to function without the speakers.

Best and thanks for any input,

-JH

To get my headphone autosense feature working in my Asus notebook, I had to add this:

options snd-hda-intel model=haier-w66

---

### Post by cristian.vrabie on 2009-03-28
Thanks hotweiss! Had the same problem on Asus laptop with 82801I (ICH9 Family) Audio Controller and adding "options snd-hda-intel model=haier-w66" to "/etc/modprobe.d/alsa-base" fixes it.

---

