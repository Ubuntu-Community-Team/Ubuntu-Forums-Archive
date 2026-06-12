---
title: "HDMI/DP only left channel sound since kernel 4"
date: 2016-02-26
forum: Hardware
---

### Post by doyenne on 2016-02-26
Since kernel 4.x I have problems with HDMI / DiplayPort sound. The internal speakers of the laptop and headphones both work without problems.

I checked with all the kernel versions that are currently available in my GRUB boot menu.

3.16.0-30-generic DisplayPort (and HDMI) has stereo sound (ok)
3.19.3-31-generic DisplayPort (and HDMI) has stereo sound (ok)
4.2.0-18-generic DisplayPort (and HDMI) has sound from left channel only
4.2.0-19-generic DisplayPort (and HDMI) has sound from left channel only
4.2.0-21-generic DisplayPort (and HDMI) has sound from left channel only
4.2.0-22-generic DisplayPort (and HDMI) has sound from left channel only
4.2.0-23-generic DisplayPort (and HDMI) has sound from left channel only
4.2.0-25-generic DisplayPort (and HDMI) has sound from left channel only
4.2.0-27-generic DisplayPort (and HDMI) has sound from left channel only

FWIW, Windows 10 (dual-boot) gives stereo sound.

Of course I looked for the problem in fora and Google, but the only thing I could find was a different HDMI problem (no sound at all since kernel 3.9, solved in kernel 4.0). 

Any ideas and possible solutions highly appreciated!

Hardware info:
Laptop: Asus Notebook Zenbook NX500JK-DR012H
Connection to monitor: DisplayPort (HDMI also tested, same problem)
Monitor: Dell UltraSharp U2713
Video: NVIDIA GM107M [GeForce GTX 850M]
Video Driver: X.Org X server - Nouveau display driver (open source)

---

