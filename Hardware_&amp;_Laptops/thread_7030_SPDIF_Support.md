---
title: "SPDIF Support?"
date: 2004-12-03
forum: Hardware &amp; Laptops
---

### Post by Eraph on 2004-12-03
Howdy, just wondering if anyone has SPDIF working on their computer - I know it works in Windows fine, but Ubuntu just ain't having it! I'm using a laptop with some form of Realtek audio device, and I think I'm using the ALSA drivers for it. Any ideas on where to start looking for getting this to work?

---

### Post by hndrcks on 2004-12-03
Open the volume control from Applications -> Multimedia

Select the "Alsa Mixer" tab (will probably have your sound device name too)

Find the value IEC958 Output, uncheck the mute.

If you want analog to work at same time, find value IEC958 In Monitor and uncheck that too.

---

### Post by Eraph on 2004-12-03
[QUOTE=hndrcks]Open the volume control from Applications -> Multimedia

Select the "Alsa Mixer" tab (will probably have your sound device name too)

Find the value IEC958 Output, uncheck the mute.

If you want analog to work at same time, find value IEC958 In Monitor and uncheck that too.[/QUOTE]
 IEC958 has been unchecked, and there is still no sound coming out the main speakers. I'm using a laptop, so there are two sets - the speaker setup in my room (5.1 through an audio reciever), and the wee ones on the laptop itself. Both sets are normally handled independently, as you suggested.
While I'm in that panel... There are four tabs altogether:
Realtek ALC202 rev 0 [OSS Mixer]
Silicon Laboratory Si3036/8 rev [OSS Mixer] (empty)
Intel ICH5 [ALSA Mixer]
Intel ICH5 Modem [ALSA Mixer] (Also empty, but being the modem sound, it matters not)

So to me, it looks like there are two recognized sound cards for some reason.
If it helps any, my audio reciever supports Dolby Digital, Dolby Pro Logic II, and DTS.

---

### Post by hndrcks on 2004-12-03
Hmm. Coax or TOSlink on the SPDIF? If I remember correctly the settings are different for COAX - of course, I have a CMedia sound chip so it may be completely different.

As a test, try playing media through XMMS and go to Options-Preferences and make sure the Alsa driver is selected, not the OSS.

---

### Post by Tommy on 2004-12-04
[QUOTE=Eraph]Howdy, just wondering if anyone has SPDIF working on their computer - I know it works in Windows fine, but Ubuntu just ain't having it! I'm using a laptop with some form of Realtek audio device, and I think I'm using the ALSA drivers for it. Any ideas on where to start looking for getting this to work?[/QUOTE]

My mother-in-law's Gateway PC has a very strange audio system with what LOOKS like a normal blaster-like audio card, but it connects to the speakers using a mono 1/8" to RCA audio cable, and it took a lot of Google searching to find the settings it needed.

I had to find the exact module that needed to be loaded and add

drivername spdif=1

to /etc/modules.conf

in order for ALSA to drive the speaker system.

To find out what module I needed, I used the lspci command and did some Google searches on what it reported for that card. I am sorry I can't give you specifics because (fortunately) the machine is working fine and at my Mother-In-Law's house now.

---

### Post by Spacecaptain on 2005-01-03
Am trying to get my SPDIF output (electrical, meaning coaxial) to work on my newly setup warty ubuntu.
I have a Sound Blaster Live! 5.1 Model SB 0100 working with alsa (that is, i tried the soud output with XMMS selecting the alsa mixer instead of the default one)

i have my computer connected by SPDIF to a homecinema amp and used to have that as a setup to get surround-sound emulation on win2k played movies. i would love to have the same here in ubuntu and not have to fall back on the stereo line out (wich is working okay).
I have done all the volume control unmutes on the alsa tab, but no luck....
i have also completed the "HOWTO: Hear multiple sounds at once" without any error messages.
Does actually anybody have SPDIF working on ubuntu?

as a subsidiary question i see in my modules.conf at the alsa section:
### update-modules: start processing /etc/modutils/alsa-base
above snd-pcm snd-pcm-oss

shouldn't that be

above snd-pcm snd-pcm-alsa   ?

and yes, I'm a complete newb trying to jump over to ubunto straight over from win2k... I feel like i'm flying right now... hope i won't smash on the ground ;)

---

