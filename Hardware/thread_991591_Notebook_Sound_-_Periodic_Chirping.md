---
title: "Notebook Sound - Periodic Chirping"
date: 2008-11-23
forum: Hardware
---

### Post by Benniee on 2008-11-23
I've recently upgraded from Kubuntu 8.04 to Kubuntu 8.10 on my Dell Inspiron 8500 notebook.

8.04 was working really well - 8.10 seems to need a bit of a polish to get to the same stage (for my situation anyway).

I'm aiming to clean out my problems one at a time - first one being the sound system is recognised and set up ok - can play audio no problem. But I get a low level periodic "chirp" every 10 seconds or so. The period is not constant, and depends greatly on what the system is doing. Moving the touchpad or typing seems to make it happen a lot quicker than an idle system.

From a little bit of googling the onboard sound for my notebook is a Sigmatel 9750 chipset.

The volume of the chirping seems to depend on the "front" level in KMix. The PCM level doesn't seem to change it at all.

Any ideas on where I start tracking this one down?

Benniee

---

### Post by Trent T on 2008-11-23
Hi Benniee--

I had a similar problem after loading Xandros Linux onto my laptop a couple of years ago--
Apparently, my laptop sound card has an integrated microphone that was not 'on' when operating under Win XP, but IS 'on' when operating with Linux. When I gently scratch on the laptop case above the physical location of the sound card, the scratching sound is magnified thru the laptop speakers.

The chirping noise, in my case, is feedback from the laptop speakers to the microphone. I could not figure out how to turn off the microphone, so I cope with it by turning down the speaker volume.

Suggestion: If you lightly tap or scratch on your laptop case above the sound board location, and you hear it through your speakers, you may have the same problem.

My Laptop:
Toshiba Tecra A7
Realtek sound card
Xandros Pro (2006) Linux, dual booted with Win XP.

---

### Post by Benniee on 2008-11-24
Thanks for the reply.

I took a close look at all the channels in KMix and the Mic one was set to Mute. I thought there may be a problem with this one so I unchecked it - made no difference.

I tried scratching and tapping on the keyboard but that doesn't always cause the noise.

With all the other sound working ok it's almost as though the system is somehow generating the noise deliberately, as in some routine is sending data to the sound driver when it shouldn't be.

Benniee

---

