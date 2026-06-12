---
title: "Vox Adio Air GT - USB audio interface recording"
date: 2018-08-25
forum: Hardware
---

### Post by spadewarrior on 2018-08-25
Hi all,

I recently purchased one of [these guitar amps]("http://www.voxamps.com/AdioAirGT") and saw they can be used as a USB audio interface. No linux support is provided but I thought I'd try it out as being able to record directly from the amp would be nice.

I plugged it in and amazingly Linux + alsa saw it immediately. Trouble is when hooking it up in Jack using qjackctl, and then trying to record (I'm using Renoise) the sound is distorted (choppy like a tremelo pedal but worse) and detuned by a few notes. However I could record the output of the amp and it played back through my monitors, via my (ICE) M-Audio Delta 44 which I normally use for recording.

Increasing the buffer helped a bit but not by much, and after fiddling about with some settings I didn't understand, apparently crashed jack or alsa. Pulseaudio is sitting somewhere in there as well...

Does anyone have any idea what settings I should use, or even which settings I could play around with to get this working?

Thanks :)

---

