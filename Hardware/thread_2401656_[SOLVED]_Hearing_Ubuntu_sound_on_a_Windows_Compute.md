---
title: "[SOLVED] Hearing Ubuntu sound on a Windows Computer"
date: 2018-09-20
forum: Hardware
---

### Post by reduz on 2018-09-20
Hi Guys! I have two computers, one with Ubuntu Desktop and another with Windows 10. They sit next to each other.
The Windows 10 computer has an USB sound card connected to studio monitors, while the Ubuntu one has no sound.
Both computers share a private LAN via ethernet which I use to run Synnergy 1 (share mouse and kb). 

Is there any way to create a virtual sound card in Ubuntu that sends sound over ethernet to the Windows computer? This way both can play sound via the same soundcard and speakers.

Thanks!

---

### Post by TheFu on 2018-09-20
I have no clue about Win10.  Never seen it in the real world, sorry.
If it is running any of the media server programs, those almost always support remote control.

But if both systems ran Linux, there are methods via pulse audio remote.
[https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Network/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Network/)

There are also a few different client/server techniques if Linux was the server. mpd is popular. There are clients for almost any OS.

There's always something like Synergy to share the mouse/screen between 2 systems. I've never used it - prefer to use a KVM device myself. Using a 4-port Belkin.  But only you know your setup and what will work.

---

### Post by reduz on 2018-09-20
Thanks! Yeah, I have found that pulseaudio can stream over the network in multiple format, but
the main issue is that the sound system is set on Windows due to pro audio needs. 
I can't find any way to "listen" and playback this sound on Windows. I know there is icecast, but the process of encoding/decoding sound has delay, so I was expecting something more efficient.

---

### Post by reduz on 2018-09-20
I solved it, this tutorial:
[https://www.joshcurry.co.uk/posts/synchronised-low-latency-multi-client-network-audio-mpd-pulseaudio-vlc](https://www.joshcurry.co.uk/posts/synchronised-low-latency-multi-client-network-audio-mpd-pulseaudio-vlc)
to cast from PulseAudio
I also forced PA to stream only to the Windows computer, via ethernet. On Windows, opened a stream from VLC to rttp://@:port and set latency to 0.
Works perfectly!

---

