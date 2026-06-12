---
title: "Nvidia 210 and HDMI 5.1 audio"
date: 2012-02-28
forum: Hardware
---

### Post by Alan1977 on 2012-02-28
Good morning, hope somone can help me here im pulling my hair out, i have tried following numerous guides but am at a dead end.
I am using an Nvidia geforce 210 connected to my tv via hdmi, tv to amp via spdif
I have tested this setup using xbmcubuntu and all works fine in 5.1 dts
Now, my main install is 11.10 desktop
go into the sound properties and i have multiple outputs to choose form under hardware;
something like:
nvidia HDA 5.1 9
nvidia HDA 5.1 8
nvidia HDA 5.1 7
nvidia HDA 5.1 3
nvidia HDA 2.0 9
nvidia HDA 2.0 8
nvidia HDA 2.0 7
nvidia HDA 2.0 3
(this is from memory the exact naming may vary)

output works on HDA 5.1 and 2.0 number 3
however, speaker test only works on the stereo left and right on both outputs.

going into ALSAmixer from the terminal shows 1 soundcard and 4 channels
on my working xbmcbuntu setup, ALSAmixer shows 1 channel only (as i recall)
my understanding is that the GPU has 4 individual chips for 4 pairs of audio channels. XBMCbuntu knows how to handle these, but i can not get my main Ubuntu installation to work correctly.

Could anyone kindly guide me through this please?
i tried putting an entry in /etc/asound.conf as per 
[http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_HDMI_audio_on_GeForce_GT210,_GT220,_or_GT240)

i may have done something wrong but am truly baffled
Now, i am not sure, but i think i have pulseaudio and alsa installed (not sure if i shoudl have only alsa?)

thanks for any guides/tips

---

