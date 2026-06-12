---
title: "Microphone not working on Maya with Compaq 6720s"
date: 2012-11-12
forum: Hardware
---

### Post by gawynus on 2012-11-12
Hi,
I recommended Linux Mint 13 to a friend, installed it and I am fighting with microphone on HP Compaq 6720s.

It doesn't work at all - not only in Skype. Sound recording only gives some buzzing.

I already tried:
1) Removing pulseaudio and pavucontrol by purge - the only effect was - I wasn't able to change sound settings at all :/.
2) pulseaudio -k / -D - not working - it said "deamon couldnt be started)
3) I was trying to set input to ALSA in sound setting - no effect.
4) Tried to mute one of channels in pavucontrol.

One thing I noticed is that I am not able to change volume of "Mic" in alsamixer at all - it is simply visible but disabled.

When I modified /etc/modprobe.d/alsa-base.conf  changing some line "...laptop" to alias snd-card-0 snd-hda-intel... I don't have sound at all even from speakers.

Please help - I am really considering to dump Maya and install other distro to a friend.

Thanks!

---

### Post by gawynus on 2012-11-13
Sorry for disturbing you all.

It appears the problem lied in the microphone who broke in the exact moment of plugging it off from another computer and plugging in to Compaq.
Dead object can be mean ;).

so it is SOLVED

---

