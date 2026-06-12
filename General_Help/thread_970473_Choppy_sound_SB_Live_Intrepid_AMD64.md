---
title: "Choppy sound SB Live Intrepid AMD64"
date: 2008-11-04
forum: General Help
---

### Post by jony121 on 2008-11-04
I couldn't find the board rules so I am not sure if a first post request is accepted
I have already put something up on launchpad [https://bugs.launchpad.net/ubuntu/+bug/293574](https://bugs.launchpad.net/ubuntu/+bug/293574)

I am having terribly choppy sound with my SB Live!
In Volume Applet 2.24.1 (by right clicking on that little speaker.)
Under device:
1: SB Live 5.1 (alsa mixer)
2: SigmaTel STAC9708,11 (OSS Mixer)
3: Playback: ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA (Pulse Audio Mixer)
4: Capture: Monitor Source of ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA (Pulse Audio Mixer)
5: Capture: ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA (PulseAudio Mixer)

My volume is controlled by three sliders.
1st: Master in device 1 which the same as Master in device 3. Under playback.
2nd: PCM in device one. Under Playback.
3rd: Volume in device 2. Under Recording.

Why is my volume controlled by something under recording I wonder.

Not sure where the problem lies here. In alsa maybe.

I was wondering first of all how I might stop the card from being multichannel. I think that might help. I found this: [http://manpages.ubuntu.com/manpages/intrepid/man4/snd_emu10kx.html](http://manpages.ubuntu.com/manpages/intrepid/man4/snd_emu10kx.html)
And it said about putting
snd_emu10k1x_load="YES"
hint.emu10k1x.0.multichannel_disabled
in /boot/defaults.conf however that does nothing.
My logic is that if it's not multichannel then it won't get split up and that bit in OSS won't be there which is my only hint of what the problem might be.

I may also try downgrading my alsa as I had no trouble with sound in gentoo and I think that used a different version.

Anyway, any ideas or help are greatly appreciated. Thank you in advance.

---

### Post by jony121 on 2008-11-04
I just re-compiled my kernel without any OSS in it. Even took out the OSS mixer in alsa. Problem is still there. This problem has nothing to do with an oss conflict with alsa.
Now I am going to try downgrading alsa.

---

### Post by jony121 on 2011-06-03
This bug worked itself out with version upgrades.

---

