---
title: "Dell Mini 9 Netbook Remix - Audio and Visual Effects issues"
date: 2009-04-24
forum: Hardware
---

### Post by bawbag on 2009-04-24
Hey folks, thought I'd give NBR a spin on this laptop but it's been a while since I've used ubuntu so bear with me.

The only major hiccup so far is sound, particularly with Skype.  Playback seems to be working okay with the headphone jack detecting and switching over when plugged in.  The main issue is with input for the built in mic, and the mic port.

Sound Preferences:
All set to Autodetect, Sound Capture set to ALSA

Volume Control:

HDA Intel (Alsa Mixer)
Recording tab has 2 controls called Capture and Capture1.  Both have their slider up, but there is a red cross on the mic icon below them.  If I click the mic buttons the cross will disappear, then immediately come back if I close and open the volume control again.  Both sliders for mic boost are at absolute minimum due to feedback/static if they're turned up.
 
In the options tab there are two sources, one set to Mic, one set to Front Mic. Using sound recorder and tapping the front mic shows the level meter jump up, but does not play back.  Nothing at all with the external microphone plugged in.

Skype:
Output only seems to work if Sound Out and Ringing are set to pulse.  Test call gives sound with the speaker and headphones, but the input will only give static whether it's set to pulse or HDA Intel.

Any clarification on where I'm going wrong here would be much appreciated.  Love the netbook interface and hoping to stick with it.

As for visual effects, is there a workaround yet for the NBR issues with intel gfx and Visual Effects?

Thanks for your help.

---

### Post by jespdj on 2009-04-24
I had to fiddle a bit with the sound settings, but it works without any problems with Skype on my Mini 9. I installed Skype from the [Medibuntu repository](http://www.medibuntu.org).

See the attachments for my mixer and Skype sound settings.

---

### Post by bawbag on 2009-04-24
Thanks for the response. :)

I've set everything up exactly as in your screenshots and rebooted the computer.  Everything seems okay with the built-in mic but still no joy with the microphone jack.

Also the sound in skype seems a bit glitchy, small frequent skips every few seconds.

---

### Post by phicam on 2009-04-29
thanks for the config input, got my 9.04 NBR working as well!

---

