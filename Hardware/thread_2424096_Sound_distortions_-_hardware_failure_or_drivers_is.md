---
title: "Sound distortions - hardware failure or drivers issue? (video attached)"
date: 2019-08-03
forum: Hardware
---

### Post by ground21 on 2019-08-03
Recently I encountered (happened already few times) some audio distortions, but those were for very short time so I kinda ignored them. Today, when playing some YouTube video audio started to be disordered. Out of nowhere. Also playing anything on Spotify revealed some "problem". Have a look at this video - it shows the issue. [https://1drv.ms/v/s!Av_uzlzC33mugd4z0jWU8CfO9M_vgg]("https://1drv.ms/v/s!Av_uzlzC33mugd4z0jWU8CfO9M_vgg")

Switching output device few times in audio settings helped - audio is now OK (without need to restart machine). I'm wondering if this might be hardware failure or it's something driver-related. 
Please help me troubleshoot this. Ubuntu 19.04 on Asus Z170 deluxe.

---

### Post by vidtek on 2019-08-03
> **ground21 said:**
> Recently I encountered (happened already few times) some audio distortions, but those were for very short time so I kinda ignored them. Today, when playing some YouTube video audio started to be disordered. Out of nowhere. Also playing anything on Spotify revealed some "problem". Have a look at this video - it shows the issue. [https://1drv.ms/v/s!Av_uzlzC33mugd4z0jWU8CfO9M_vgg]("https://1drv.ms/v/s!Av_uzlzC33mugd4z0jWU8CfO9M_vgg")

Switching output device few times in audio settings helped - audio is now OK (without need to restart machine). I'm wondering if this might be hardware failure or it's something driver-related. 
Please help me troubleshoot this. Ubuntu 19.04 on Asus Z170 deluxe.

You don't give much information about your system, specifically the hardware.

If you can attach another source to your amplifier/audio input and the audio is clear, then the hardware is probably ok.

Work backwards through a logical sequence from your speaker, amplifier, source, then start looking at the computer interface, O/S, gui, if you can play undistorted through a CLI driven source
that will eliminate the computer side and you can then concentrate on the applications and ALSA/PULSE.

Cheers, Tony

---

### Post by ground21 on 2020-01-13
Sorry for not updating for long time. 
Very same issue happens on my PC at work (which runs on Ubuntu 19.10 installation). So this is totally different hardware but same/similar issue - audio plays distorted for about a minute and then problem disappears. Turning off my USB headset and plugging it again helps (audio is fine after re-plugging).

---

