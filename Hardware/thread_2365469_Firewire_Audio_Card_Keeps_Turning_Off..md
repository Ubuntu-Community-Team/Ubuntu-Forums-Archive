---
title: "Firewire Audio Card Keeps Turning Off."
date: 2017-07-07
forum: Hardware
---

### Post by j0330h on 2017-07-07
Hello,

I am running Ubuntu-GNOME 17.04 although I have also had this issue with Ubuntu Studio 16.04 and Ubuntu 16.04. I use a Focusrite Saffire Pro 14 as my daily driver sound card, that runs over firewire into my computer. The issue is although it plays back audio, it constantly shuts off after a certain period of inactivity has passed. Upon audio being generated after it's shut off the entire OS hangs for a moment, the firewire card starts up, and it plays audio until it times out from inactivity again. I have tried referring to the Ubuntu Firewire audio guide but have not had any success. Another more minor issue is Ubuntu interprets my sound card as a multi channel sound card. So anything that isn't explicit stereo ends up getting sent to audio channels that have no actual speaks. Is there a way to force multi-channel audio to be stereo?

Thanks!

---

### Post by CatKiller on 2017-07-07
I think both of those things can probably be fixed by playing around with your PulseAudio config.

I believe the audio device is turned off by the module *module-suspend-on-idle*.

I believe you can also change the channel mapping to more accurately reflect where the speakers are connected.

I have no expertise on this, I've just seen the options while poking around.

---

### Post by j0330h on 2017-07-07
> **CatKiller said:**
> I think both of those things can probably be fixed by playing around with your PulseAudio config.

I believe the audio device is turned off by the module *module-suspend-on-idle*.

I believe you can also change the channel mapping to more accurately reflect where the speakers are connected.

I have no expertise on this, I've just seen the options while poking around.

Thanks, that does seem to work, however my computer freezes eventually after a few minutes upon commenting out that entry. Is there a better suited community/board I could post this issue in?

---

### Post by CatKiller on 2017-07-07
Maybe the multimedia section? It seems to be a PulseAudio config thing rather than a FireWire hardware thing.

I also don't know if there's such a thing as a PulseAudio community, or something similar, with more knowledge of the nitty-gritty of how PulseAudio works. The introduction of PulseAudio was rough, so most of the posts here at the time were about turning it off, and since then it mostly just works on most people's hardware, so again there's not masses of expertise from having to fix things. I could be wrong, though, and there's an expert here just dying to dig into your problem.

It might be possible to change the settings of that module rather than disabling it entirely. I'm just a dabbler, though.

---

### Post by j0330h on 2017-07-08
> **CatKiller said:**
> It might be possible to change the settings of that module rather than disabling it entirely. I'm just a dabbler, though.

Well you got further than me, I've been trying to troubleshoot my interface with Ubuntu for like a year. Hopefully mods won't slap me on the wrists if I make another post in multimedia.

---

### Post by CatKiller on 2017-07-08
As I understand it, PulseAudio does all the nice user-facing stuff like routing audio to the correct device, setting samplerate and so on, and ALSA does the device-facing stuff, like interrogating its state and setting channel volumes and so on. Perhaps they need to both be configured in some way to prevent the card going into idle?

Another thing that occurred to me is that it's possible that the FireWire port itself is powering down after a period of inactivity. So even though Pulse is still running as you want, the FireWire device itself has mysteriously vanished because it's been turned off by something else? Hence the freeze.

This is all speculation on my part; this is much further into the weeds than I've ventured before.

I've also looked around a bit, and there's something called FFADO for manipulating FireWire audio devices. I have no idea if that's being used at all in your case; the PulseAudio -> ALSA thing is what I've seen for internal sound devices. FireWire could be different, or it could be the same. I have no idea. As of 5 years ago, which is the latest I saw, support for your device was listed as "Experimental."

---

