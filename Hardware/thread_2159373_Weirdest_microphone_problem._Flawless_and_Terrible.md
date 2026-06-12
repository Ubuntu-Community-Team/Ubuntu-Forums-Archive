---
title: "Weirdest microphone problem. Flawless and Terrible at the same time :/"
date: 2013-07-02
forum: Hardware
---

### Post by vbgunz on 2013-07-02
If I open up alsamixer and go to the first "Front Mic" option and un-mute and talk, the sound is absolutely perfect. I come in crystal clear and everything works like a dream.

If I record myself over audacity or talk on Mumble or do anything other than what I said above, a static popping hissing sound is always heard. If I open my mic as I first said above my recording is flawless, if I do anything else it's terrible.

I messed with all sorts of settings and absolutely nothing works. I lowered recording input to the lowest in which I can hear myself speak and I lowered the capture input too, I raised them, muted them, changed backends from gstreamer to VLC, etc. I changed from plugging in the front to plugging in the back and nothing I do or know how to do is helping.

I am at a lost and cannot figure out why when my mic is open input is perfect but when I record myself or speak over a voip app, some static popping hissing sound always accompanies it :(

Any help appreciated!

I am on Kubuntu 13.04 64 with all the latest updates.

---

### Post by tgalati4 on 2013-07-03
It's possible that your audio monitor (feedback channel) is being recorded and overdriving the input.  Try turning off the output and monitor channel then record again.

The way to tell is to use a headset microphone.  Then you can hear yourself speak and the microphone is isolated from the headphones.

---

### Post by vbgunz on 2013-07-03
Microphone works perfectly in Windows 7, no crackling, popping, hissing or static, etc. It works perfect when I un-mute the microphone for immediate feedback. I uninstalled a TV Tuner I never quite got working (thought that might help) and tried 3 different microphones and different inputs (front, back and KVM switch) but the mic never sounds clear in an actual use-case. I tried the low-latency kernel, resetting mumble by purging it and wiping any configurations I could find for it, I played with boost and volumes and anything I could find in (pavucontrol and alsamixer) but I'm missing something big here. I tried pulseaudio, alsa and oss (pulse and alsa sound exactly the same, oss doesn't work at all).

Sound from music, movies, the web are perfect. Mic is perfect in live feedback but something horrible happens when I use the mic for something useful.

I tried understanding [COLOR=#000000]tgalati4's response but even googling couldn't help me decipher exactly what was said :(

I'd really hate to get caught up in one of those corner problems that never gets answered and is dismissed forever. Any insight and ideas would be appreciated.[/COLOR]

---

### Post by vbgunz on 2013-12-29
After more than several releases and perhaps a couple years, I finally solved a multitude of issues. It seems that it all came down to pulseaudio and it for some reason was really breaking my system down badly. Poor performance all around, in compositing, in games, in audio, pulseaudio was the devil on my system. A horrible cracking, hissing, popping, staticky feedback from the microphone even on low was infuriating. Games stuttered horribly in framerates, some games ran great but had terrible audio and Mumble was a huge pain in the ass to get a clear sounding microphone. I'm going over these issues because out of the box, something like audio SHOULD JUST WORK. For several releases I dealt with the fact it simply didn't and tenacity led me to figure out the problem was with pulseaudio.

I've googled this issue to death and all the usual tips and tricks, workarounds and fixes didn't fix anything for me. Here's what I did and if this works for you, I'd like to hear your feedback on it, I'd appreciate a thanks *because* if this works for you, I see no reason why they can't just add this fix to all releases going forward. Here we go.

You're gonna make a copy of a file and then you're going to open it up in your favorite editor (don't use vim if you're not comfortable with it, use another editor).

```
sudo cp /etc/pulse/daemon.conf /etc/pulse/daemon.conf.origin
sudo vim /etc/pulse/daemon.conf
```

All we need to do is un-comment and change 3 directives. Below on the left of -> is what the directive is by default in 13.10. On the right of -> is what you want to change it to. If you leave the semi-colon ";" in, you might as well not change anything at all because the semicolon comments the directive out and changes won't get picked up.

```
; daemonize = no -> daemonize = yes
; cpu-limit = no -> cpu-limit = yes 
; nice-level = -11 -> nice-level = 0
```

Now reboot. Hopefully, stuttering in some games is completely gone. Hopefully your microphone is clearer in Mumble. Hopefully your compositing is fresher and hopefully your audio in some games is perfect.

Tell me if this works for you. If it doesn't work and your problems aren't going away, tell me, I did do other stuff but I'm convinced it didn't really help (maybe it did).

---

