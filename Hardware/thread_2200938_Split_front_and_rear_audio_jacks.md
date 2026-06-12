---
title: "Split front and rear audio jacks"
date: 2014-01-21
forum: Hardware
---

### Post by bawng on 2014-01-21
Hi!

I'm new to Ubuntu.
In my old Windows installation I could easily separate the front and rear audio jacks on my computer in the Realtek HD Audio app. Thus, I know that my soundcard is capable of separating outputs.

However, I've not been able to do so in Ubuntu. If I turn automute off in alsamixer, I always get sound from both rear and front. If I turn it on, I'll always get sound from headphones only, if they are plugged in, and speakers only if headphones are unplugged.
However, If I manually go into alsamixer and mute either "Front" (which is actually rear) or "Headphones", I only get sound from the other.

Does anyone have any idea on how to solve this?

Thanks!
Erik

---

### Post by bawng on 2014-01-26
bump

---

### Post by Yellow Pasque on 2014-01-26
Not quite sure what you're trying to accomplish. I take it this is the behavior you desire?
> However, If I manually go into alsamixer and mute either "Front" (which is actually rear) or "Headphones", I only get sound from the other.
If so, what is wrong then?

> "Front" (which is actually rear)

Front = front speakers (not front jack)

---

### Post by Yellow Pasque on 2014-01-26
Info is always helpful..
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by bawng on 2014-01-26
> If so, what is wrong then?

I would like to split the Headphones and Front channels into different Audio devices, in order to be able to use them simultaneously but in different applications. That's how I have it in Windows. I.e., Skype goes into Headphones, but VLC goes into Speakers. Also, I managed to get it working in Linux Mint a while back, but I don't think I used PulseAudio then.

---

### Post by bawng on 2014-01-26
> **Temüjin said:**
> Info is always helpful..
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Here's my info:
[http://www.alsa-project.org/db/?f=a7bc645d2dbda5845dd8f575aa1067f038b4b315](http://www.alsa-project.org/db/?f=a7bc645d2dbda5845dd8f575aa1067f038b4b315)

Thanks in advance!

---

### Post by Yellow Pasque on 2014-01-26
[http://thomasa88.blogspot.com/2008/11/pulseaudio-and-speakersheadphones.html](http://thomasa88.blogspot.com/2008/11/pulseaudio-and-speakersheadphones.html)

---

### Post by tgalati4 on 2014-01-26
Perhaps there is a switch that you can use directly with the Realtek chip:

!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC892

Some things to try:  [http://community.linuxmint.com/tutorial/view/1236](http://community.linuxmint.com/tutorial/view/1236)

[http://unix.stackexchange.com/questions/26305/no-sound-with-mint-12-and-realtek-alc892](http://unix.stackexchange.com/questions/26305/no-sound-with-mint-12-and-realtek-alc892)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

