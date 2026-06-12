---
title: "No sound through headphones; ALSA to blame?"
date: 2011-01-31
forum: Hardware
---

### Post by Darkness Falls on 2011-01-31
I was recently given a pair of Microsoft LifeChat LX-3000 USB headphones as a gift, to replace my ageing pair that I've been using for several years now. Unfortunately, the gift-giver didn't take into account that I've not used Windows in about two years, and thus, the installation CD that came with it is useless to me! And, unfortunately, they're not working properly. I can use the handset on the cable to adjust the volume - that works fine - but all sound comes from the speakers, and nothing through the headphones. I haven't even attempted using the microphone on them yet.

I'm running Ubuntu 9.04 on an HP Pavilion dv-7 laptop; the most major (potentially relevant) change I've made from the standard installation is that I'm running ALSA as opposed to Pulseaudio (which was necessary in order to get any sound out of the laptop at all). The sound works fine through my old pair of headphones (which plug into the jacks, as opposed to being a USB pair), as well as the microphone on them, which I use for Skype calls. From a brief Google search it seems like the LX-3000 can and does run under Ubuntu, but everything I've read so far suggests that it works right from startup, and doesn't need any additional tweaking (bar the "start MSN call" button on the handset, which usually does nothing, for obvious reasons).

Does anyone have any advice? Could it be an issue with ALSA that's stopping it from sending sound to the USB ports? Is there a way to tell it to look for sound output hardware at the USB ports? I really don't want to go back to Pulseaudio, since I lose all sound output that way. Is there a package that mimics the effect of the installation software for the LX-3000, or is there anything else anyone can think of that might help?

Thanks in advance,

D.F.

---

### Post by Darkness Falls on 2011-02-04
Update on this, as well as a quiet bump for this topic: if I plug the headphones into the USB port before turning the laptop on, I can hear a 'pop' noise through them during boot-up, as though the laptop's trying to send a signal to them. Still no luck actually getting sound out, though. Any suggestions, anyone?

D.F.

---

