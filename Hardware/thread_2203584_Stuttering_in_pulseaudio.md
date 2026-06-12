---
title: "Stuttering in pulseaudio?"
date: 2014-02-04
forum: Hardware
---

### Post by xakh on 2014-02-04
I've tried a few other fixes in the past, the only thing that came close to working was purging pulseaudio entirely, but that's a really dumb solution, as my music programs and such rely on pulse. This is currently an almost perfectly clean Xubuntu install, since I just installed it a few hours ago. I posted it on the Reddit tech support section, so I'm just copy pasting it here. Any help is appreciated, I'm going to bed, as it's 6 AM here, but I'll be on afterward to reply.
I've had this problem once before, and if I recall, the original solution involved completely disabling pulseaudio. I feel like that's rather drastic, and that a medium can be reached here. My motherboard is a Sabertooth, I believe it's a revision 2, which I've looked up the specs for here([http://pcpartpicker.com/part/asus-motherboard-sabertooth990fx](http://pcpartpicker.com/part/asus-motherboard-sabertooth990fx)), which comes from the leftover PCPartpicker list I had when I made it a year or so ago. Anyway, I really would just like to have my audio play smoothly, but every so often, could be a few seconds apart, sometimes a few minutes apart, there's a little stutter in the sound playing. Doesn't matter what I'm doing, doesn't matter what program I'm using, could be using Audacious, Banshee, Rhythmbox, could be listening through Youtube, could be playing a game. Point is, for about half a second, there's this really, really annoying little tick, when I'm trying to just listen to something. I know it seems minor, and it totally is, but it bothers the heck out of me, heh.

I should also mention that pulseaudio randomly keeps changing my volume slightly up or down, I believe it's the headphone/speaker adjustment system, where it can lower the volume when headphones are inserted, but I always use headphones, so that's not really useful to me. After I'd originally posted this on the Linux4noobs sub, I realized the stutters have been a bit more pronounced here. Lasting up to a second or so, and just killing my audio. It doesn't happen to any particular layer, and even if there is only one layer, it still acts up. It seriously cannot be a performance issue, since, well, none of my 8 cores are even close to registering full load, and I'm at about 10% memory usage. Is it the onboard soundcard?

---

### Post by sudodus on 2014-02-05
Which version of Xubuntu are you running? Did you update/upgrade it after installation?

Please specify your hardware not only mobo: 'Sabertooth, I believe it's a revision 2'

- CPU
- RAM (size)
- graphics chip/card
- audio chip/card/system

Maybe the computer is not quite powerful enough or there is some mis-match between some driver and the hardware. My experience is that pulse-audio was buggy some years ago, but that it works well nowadays. Often when I run Lubuntu in old computers I install pulseaudio and pavucontrol.

---

### Post by pqwoerituytrueiwoq on 2014-02-05
so audio works, but there is something coming out of the speakers that does not sound like it used to
i had that issue and i got it fixed
[http://ubuntuforums.org/showthread.php?t=2183466](http://ubuntuforums.org/showthread.php?t=2183466)

---

### Post by Yellow Pasque on 2014-02-05
Tried this yet?
[https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by xakh on 2014-02-06
> **sudodus said:**
> Which version of Xubuntu are you running? Did you update/upgrade it after installation?

Please specify your hardware not only mobo: 'Sabertooth, I believe it's a revision 2'

- CPU
- RAM (size)
- graphics chip/card
- audio chip/card/system

Maybe the computer is not quite powerful enough or there is some mis-match between some driver and the hardware. My experience is that pulse-audio was buggy some years ago, but that it works well nowadays. Often when I run Lubuntu in old computers I install pulseaudio and pavucontrol.

Alright, I did provide a link which explained the motherboard in detail, which shows that it's an AM3+ motherboard meant for high performance computing. I don't think it's going to be a system specs issue, but in case it is.
AMD FX 8 core, from the Bulldozer series.
32GB DDR3
GTX 670
Realtek ALC892.
I'm running Xubuntu 13.10. The issue was there upon installation, I've installed pavucontrol, though I don't think that'd be the issue.

> **Temüjin said:**
> Tried this yet?
[https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)
I have tried the second fix, but as I'm not using an intel card I doubt the first would help me.

> **pqwoerituytrueiwoq said:**
> so audio works, but there is something coming out of the speakers that does not sound like it used to
i had that issue and i got it fixed
[http://ubuntuforums.org/showthread.php?t=2183466](http://ubuntuforums.org/showthread.php?t=2183466)

I don't have a whistling sound, I have an occasional stutter from any audio source at all, that seriously just sounds like the singers have speech impediments, haha. Either way, this seems to have fixed it, downgrading fluendo, despite the fact that any audo stream was doing this, so far, no problems in the last 15 minutes, which is a lot longer than it usually takes! Thanks dude, will update if it comes back.

---

### Post by Yellow Pasque on 2014-02-07
> Either way, this seems to have fixed it, downgrading fluendo, despite the fact that any audo stream was doing this
Have you tried Audacious or Youtube yet? Those don't use gstreamer, so downgrading gstreamer-fluendo would have no effect on them

> I have tried the second fix, but as I'm not using an intel card I doubt the first would help me.

The Realtek ALC892 codec confroms to the Intel HDA/Azalia standard (as do most modern onboard soundcards). You're still using the snd-hda-intel kernel module, even if you don't have any Intel branded hardware.

---

### Post by xakh on 2014-02-07
Well, thus far, stopping the scheduling on Pulseaudio seems to have worked. I'll check other things if this fails. The issue I've been seeing though is it seems to "flip" back and forth between speaker and headphone output, changing the profile for audio. I've just set both volumes to identical, since I use headphones at all times anyway, and that seems to kind of fix it, but the stupid indicator for volume keeps popping up like crazy.

---

### Post by B._P. on 2014-02-10
Signed up just to say thanks for working through this issue - Stopping PulseAudio's scheduling fixed my friend's computer, which is running Ubuntu 12.4LTS.

---

### Post by avadeaux on 2014-10-31
Thank you! I had the same problem on Raspbian on my Raspberry Pi. Editing /etc/pulse/daemon.conf, changing

; realtime-scheduling = yes

to

realtime-scheduling = no

solved the problem.

---

