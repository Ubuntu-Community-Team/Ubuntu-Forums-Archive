---
title: "sound card instaled but sound will not work"
date: 2009-06-12
forum: Hardware
---

### Post by joshpike on 2009-06-12
I have a new HP laptop,  when I instaled ubuntu everything worked fine except for the sound. only my headphones worked, the build in speakers did not

I checked and ubuntu did see the sound card, and did have the driver for it.

I downloaded some programs involving the alsa mixer(dont remever what ones, I might have changed some settings but I dont think I changed anything seroius) now my headphones will not work.

my mic still does though, I can see when I talk.

when I try to test sound with every setting it does nothing, except for "HDA ATI SB STAC92xx (OSS)" (there are two of these I can click, idenical.

for these I got "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application."

---

