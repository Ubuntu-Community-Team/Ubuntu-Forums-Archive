---
title: "Sound: Which is better, Nvidia Soundstorm or SB Audigy?"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by gkiller on 2006-04-03
Hello,

I have an Nvidia nForce2 mainboard with the Soundstorm onboard sound technology. Unfortunately, not everything regarding to the sound is working "out of the box" on my Ubuntu Breezy.

For example, the sound file preview in Nautilus is working for MP3 (after I installed the mpg123 package) but not for Ogg Vorbis.
Or sound in flash movies in Opera is only played when no other sound is playing and after I close Rhythmbox and restart Opera. And even then the sound lags behind the picture.
Or, I am simply unable to play movies with 5.1 AC3 audio track. I get sound but only downmixed to 2.0 (with totem-xine, mplayer and VLC), and sometimes if I try to change speaker settings I get error messages like "sound device already in use" and cannot play the movie. Also, I wanted to listen to music in 5.1 or at least 4.1 but as soon as I choose "duplicate front" in Volume Control, the bass disappears.

I am new to Linux, but I have heard that not all sound cards/chips/codecs are equally well supported. Also there are things like "hardware mixing" which apparently improves support for sound a lot, or so I have heard...

I have an old Creative Soundblaster Audigy lying somewhere (the first edition). Do you think that things would improve if I used it instead of my onboard Soundstorm chip? How well is the driver support for those both chips, do any of them use hardware mixing?

I like Ubuntu very much (it is my first Linux distro) and I am planning to keep it, but that the sound is only half working annoys me.

Any advice would be welcome.

/GKiller

---

### Post by gkiller on 2006-04-05
OK, after searching on the internet I believe that these are the facts:

* Soundblaster Audigy cards support hardware mixing, as do SB Live 5.1 and Audigy2 cards (but not Audigy LS), and there is driver support for them in Linux.
* nForce2 Soundstorm does support hardware mixing, but only with closed source Nvidia drivers, so no support for that "out of the box" in Ubuntu.

Can anyone confirm that?

So if the above is correct I think I'm going to plug my Audigy card back in. Can I simply insert the card and deactivate the onboard sound in the BIOS, and Ubuntu will automatically recognize the change and install/uninstall the correct drivers without problems?

---

### Post by brodock on 2006-04-11
i'm thinking off buying a new non-onboard sound card (like audiogy) and I really want to hear that answer too. :rolleyes:

---

### Post by gkiller on 2006-04-11
OK, apparently there are some nvidia drivers that activate hardware mixing. But since they are not in the Ubuntu repositories but have to be downloaded from nvidia, I went on and installed my Audigy Player.

And with this card, everything works. This is how sound should be. I can even listen to MP3s in full 5.1 (with center speaker) for the first time ever (even Windows couldn't do that). AC3 movies work and with the right player (gxine, the best I found so far, with powerful but easy configuration... you can't say that about totem, where half of the settings don't work and you have to change them in text files, or VLC that is a bit too complicated) I can easily switch from full 5.1 to stereo downmixing.

I had to experiment with the mixer a bit before I got the full sound, and I still don't know exactly which ruler does what... I also switched completely to ALSA (with the alsa-oss and libesd-alsa0 packages and by changing in the multimedia preferences and turning off the ESD server).

Now I can run ALSA and OSS programs and every sound can be played simultaneously from every source... great. Before this an OSS program would block others or would choke as soon as ALSA or ESD played any sound.

I had some minor problems, eg. after turning off ESD Gaim didn't play any sounds but this was easily solved in the preferences.

I haven't tested audio capturing, so I cannot tell anything about that.

I would recommend you to buy the Audigy 2 ZS, because I have heard only good things about that card and it has the newer chip (EMU10k2 AFAIK). Or if you want to save money then buy the old Audigy Player or SB Live 5.1 (*not* the "24bit 7.1"-version!), they have the EMU10k1 chip, that's what I have now.

Or you could try the nvidia nforce2 drivers. I heard they work well and are easy to install... (if you have an nforce2-chip)

---

