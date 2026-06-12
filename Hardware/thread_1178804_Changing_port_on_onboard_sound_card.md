---
title: "Changing port on onboard sound card?"
date: 2009-06-04
forum: Hardware
---

### Post by kaiz0r.ku on 2009-06-04
Is there some sort of code to change the audio port? there are 6 ports on my onboard sound card, and it just so happens that the default one only has Right Channel sound. It has been a problem ever since i've got the motherboard, but yeah. can i change the port?

I have a Realtek ALC889A.

---

### Post by markbuntu on 2009-06-06
It depends on what you are using but it is possible to remap the sound output from front to rear and plug your speakers in the rear output if that is what you are wanting to do.

If you are using pulseaudio you can use module-remap-sink to do that. There is an explanation about using it here

[http://pulseaudio.org/wiki/Modules#module-remap-sink](http://pulseaudio.org/wiki/Modules#module-remap-sink)

---

