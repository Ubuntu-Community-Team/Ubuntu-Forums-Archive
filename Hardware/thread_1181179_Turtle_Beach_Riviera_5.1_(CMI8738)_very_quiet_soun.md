---
title: "Turtle Beach Riviera 5.1 (CMI8738) very quiet sound even though turned up"
date: 2009-06-07
forum: Hardware
---

### Post by thelusiv on 2009-06-07
I am experiencing a very frustrating problem. I just got a new sound card and plugged it in, disabled the onboard sound, and connected my speakers. From past experience I know to go through the volume control and make sure everything was unmuted/turned up, so I did this. At first I thought it wasn't working, so I started reading on these forums as well as googling for solutions. I found padevchooser, and through that was able to monitor the devices and see that there was indeed sound playing. I turned my speakers all the way up and can now faintly hear the audio.

Everything has been turned all the way up, the applications I'm playing audio with (rhythmbox, amarok, test sounds), the ALSA devices are at 100% (on both Master and PCM channels) and unmuted in volume control, the volume is at 100% in padevchooser, and the PCM and Master controls are at 100% in alsamixer. If the problem is due to software volume control, then there is some channel which is disabled and I can't turn it up. The speakers are also all the way up. I am playing through a Logitech 5-speaker set and usually it is quite loud. If I put my ear up to the speakers, I can hear a very faint sound coming from each one, with everything turned up to the max (software and hardware). I am using a known working analog cable directly from the sound card to the speakers. The connections are all good, I have even tried wiggling the cables in the sound card and unplugging/replugging them.

I have read through some sound troubleshooting tutorials on the forums and though they have some useful information (like padevchooser), I haven't found anything that's helped. There doesn't seem to be much information about the cmi8738 chipset other than it is popular amongst Linux users for its digital output (I don't have anything with a digital input to test that with).

I've seen some users with a similar issue on HDA Intel sound cards. They use the option "3stack" when they load the snd_hda_intel module and it fixes this for them. As far as I can see, this option is only for snd_hda_intel, and wouldn't do anything on the cmi8738. I may try it anyway.

Has anyone had a similar problem? I probably should mention that this is a Ubuntu 9.04 64-bit system which was upgraded from 8.10 (which was upgraded from 8.04, ...7.10, ...7.04). Generally I don't think this should matter, however I would not be opposed to blowing away my pulse/alsa configurations and letting them be set up again - however I haven't found a good tutorial on how to do this (one of the sound troubleshooting tutorials mentions something like that but then doesn't link to it)... I would rather not have to do a full reinstall, because it will take me a while to get all the necessary packages installed again. I will only do this as a last-ditch effort...

This is incredibly annoying. I know the card is working, I just can't get it to be loud enough. It's like the card is just passing the bare signal through without any amplification at all.

Please help! :-k

---

### Post by thelusiv on 2009-06-11
Well, I did a full reinstall of 9.04 AMD64, hoping that would clear out whatever bad configuration was there and maybe get some working sound. Alas, this is not the case. Can anybody think of a reason why this card wouldn't work?

---

