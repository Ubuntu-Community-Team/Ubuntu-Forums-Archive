---
title: "Optical (sound) on Realtek ALC888 in Ubuntu"
date: 2008-09-28
forum: Hardware
---

### Post by king vash on 2008-09-28
I have had no previous issues with my sound but when I went to use my optical port it does not work in Ubuntu, it works in windows. I have an IP-35E motherboard. I assume this is some easy configuration fix that I simply can not find on the forums. Does any one know how to configure optical ports in Ubuntu (8.04)?

---

### Post by Rickeo on 2008-09-29
Same problem here. No sound out of the S/PDIF port. Havent tried the analog ports, but I would assume they work. My speakers are hooked up to my reciever, which is connected to the optical port on my mobo. 

Relevant system specs:

Gigabyte GA-P35-DS3L Rev. 2.0
Realtek ALC888 on-board HD Audio
Ubuntu 8.04 x64

Everything works fine under Vista x64 (my main OS)

---

### Post by SleepingProphet on 2008-09-29
I had the same problem in my Shuttle barbones. The problem ended up being really stupid. If yours is like mine, it has a whole bunch of outputs because you've got a full set of analog surround outs, plus digital outs, plus SPDIF, plus inputs.

Under ALSA, the SPDIF channel was muted by default. I had to get to it and un-mute it and then it worked. I did that via a package called ALSAMix. I think thats the name, I'm at work right now and can't really check. Its basically a GUI version of the ALSA mixer app. The trick is to look for the muted / enabled icon at the top of each channel. The "this channel is muted" icon didn't really jump out at me and make me, but I eventually clicked on it and voiala, surround sound! After that everything's been working very well, especially from XBMC :)

---

### Post by Rickeo on 2008-09-29
That did it! Thanks!

---

### Post by king vash on 2008-10-02
I installed ALSAMixergui and played around for a bit but I did not see a S/PDIF line.

---

### Post by damnbiker on 2008-11-17
I have a similar problem too.  I'm not having any luck with my spdif passthrough on my HDMI cable.  I installed the ALSAmixerGUI program and didn't see an spdif option.  Am I missing something?

---

### Post by Fox5 on 2009-01-13
Same problem for me on Intrepid. I have an nvidia 630i motherboard. Sound works in older versions with just ALSA, but I can't get sound working with pulseaudio. The SPDIF option doesn't even show up in alsamixer when pulse is running.

---

