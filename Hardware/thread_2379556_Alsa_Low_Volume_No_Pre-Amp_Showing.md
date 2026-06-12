---
title: "Alsa Low Volume No Pre-Amp Showing"
date: 2017-12-06
forum: Hardware
---

### Post by alsetema on 2017-12-06
Hello people of the Ubuntu forums.

I am currently running Xubuntu 17.10 on my HP laptop, with a Realtek ALC295 chip.

For my experience, audio in Linux has always sounded lower in volume in comparison to Windows, and after doing some research it is apparently due to some kind of preference for sound quality over volume ALSA has.

This aside, I have Googled several solutions for this, and the one I would like to implement is the following one I found in the Archwiki that would insert a software pre-amp to the alsamixer.

Here is the link:

[https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture/Troubleshooting#Low_Sound_Volume](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture/Troubleshooting#Low_Sound_Volume)


And the respective code:

```
pcm.!default {
    type plug
    slave.pcm "softvol"
}

pcm.softvol {
    type softvol
    slave {
        pcm "dmix"
    }
    control {
        name "Pre-Amp"
        card 0
    }
    min_dB -5.0
    max_dB 20.0
    resolution 6
}
```
 


This said, I have copied the code into /etc/asound.conf and restarted. Played a video and tried finding the new control in alsamixer. Since nothing appeared I also tried changing the type from "plug" to "hw" and restarting, without result.

I cannot find a way to fix this since I simply want a pre amp that allows me not to go to the pavucontrol and manually overdrive the settings to over 100%
I have tried seeking help in the ALSA IRC channel with no result, and all the posts I have found in google have deemed useless since I they all end up giving up on this and falling back to pavucontrol, something I would not want.

Thank you very much and I hope this can get a solution!

---

### Post by VMC on 2017-12-07
I've had same result, that Windows has higher volume, but my linux install plays loud enough. I use PulseAudio plugin, which is addressed further down in that link you supplied.("Other Issues").

---

### Post by Yellow Pasque on 2017-12-07
I always found the asound syntax very confusing, but I'm guessing you want something other than "slave dmix" (maybe hw:0,0 for example) since systems configured for Pulseaudio generally don't use dmix. Pulseaudio does the mixing.

---

