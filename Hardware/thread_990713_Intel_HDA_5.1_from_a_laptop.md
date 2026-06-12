---
title: "Intel HDA: 5.1 from a laptop?"
date: 2008-11-23
forum: Hardware
---

### Post by f4phantom2500 on 2008-11-23
EDIT:  Can a mod please move this to the "Multimedia & Video" forum? Also could the title please be changed to "Audio Jack Retasking"?



Hello all, I've come to a bit of a crossroads regarding the audio for my laptop.

Now, when I use my laptop at home, I typically have it hooked up to an external monitor and speakers. The speakers I use are Logitech Z-5500s. Now, I was thinking about getting a good USB sound card, but the audio quality of the Intel HDA in my Inspiron 1525 is surprisingly good...of course that could be partly due to the speakers.

Anyway, the major caveat of this audio setup is the lack of true 5.1, since I just have the speakers hooked into one of the laptop's headphone jacks. Now, these speakers do support Pro Logic II, so it's not that bad, but I'd still rather have real 5.1 if possible.

I've read that one of the specifications of Intel's HDA is support for 5.1 surround. However, on a laptop I'm not exactly sure how this would work. The laptop has 2 headphone jacks as well as a line in mic jack. I noticed when I go to Volume Control, there's a category for "Surround" and "Center" under playback. Is it possible to set the 2nd headphone jack for the rear channels and the mic jack for the center/sub channels? That would be perfect. If not, is there any other way of doing this without buying a new sound card?

The speakers also accept S/PDIF connections, if some kind of adapter would do the trick. I'm just not sure of Intel's HDA's limitations, especially through a laptop.

Thanks!

---

### Post by j_ubnet on 2008-11-24
Bump!

I have a Dell XPS laptop with two headphone jacks and one mic-in jack that I am trying to successfully connect Logitech 5.1 speakers to. In XP & Vista, the Sigmatel audio driver allows configuration when you plug the speakers in so the jacks can be setup as Front, Centre & LFE, and Rear speaker channels, which is quite handy.

I have tried the speaker-test command

 speaker-test -Dplug:surround51 -c6

with some fiddling with the volume levels and settings in GNOME ALSA Mixer, I found that I have successfully setup the mic jack as an output by selecting "Mic as Output", however, the output is the front channel. So, I have 2x front channel outputs & 1x rear channel output. **Does anyone know how to successfully configure the mic-in jack for centre/LFE channel output?**

---

### Post by f4phantom2500 on 2008-11-24
> **j_ubnet said:**
> Bump!

I have a Dell XPS laptop with two headphone jacks and one mic-in jack that I am trying to successfully connect Logitech 5.1 speakers to. In XP & Vista, the Sigmatel audio driver allows configuration when you plug the speakers in so the jacks can be setup as Front, Centre & LFE, and Rear speaker channels, which is quite handy.

I have tried the speaker-test command

 speaker-test -Dplug:surround51 -c6

with some fiddling with the volume levels and settings in GNOME ALSA Mixer, I found that I have successfully setup the mic jack as an output by selecting "Mic as Output", however, the output is the front channel. So, I have 2x front channel outputs & 1x rear channel output. **Does anyone know how to successfully configure the mic-in jack for centre/LFE channel output?**

So you got the second headphone jack to output the rear channels? How did you manage that? Hopefully we can get an answer to this solution, I really don't want to have to reformat and install XP :S.

Also I don't see the "Mic as Output" thing?

---

### Post by k.p.odoherty on 2008-11-29
Hi,
I have an INspiron 1525 too and have been trying for ages to get sound out on both headphone jacks & the mic jack, to no avail. You someone manages to get it working, please let me know!
Regards,
Peter

---

