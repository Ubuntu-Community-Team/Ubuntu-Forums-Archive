---
title: "Fresh install, fluxbox, only one program can play audio at a time"
date: 2010-02-26
forum: Hardware
---

### Post by IceDane on 2010-02-26
The topic says it all, basically. However, there is a bit more to it.

A while ago(a few months) I upgraded from 9.04 to 9.10 via dist-upgrade. It seemed to have worked well, but I kept having the issues in the topic; I could only play audio from one source at a time. I didn't really care though, but eventually(yesterday) I figured I would fix it because it was getting pretty annoying.
Every time I wanted to listen get audio from a video online through chrome, I had to stop playing the music. Obviously, audio from a video whilst playing music wouldn't be audible, but that's not the point.
After I finished listening to the audio of the video in the browser, and wanted to start playing music again, I would get errors from whatever music player I was using(mpd currently): "cannot open audio device"

Now, I'm a programmer so I can somewhat understand what's going on. It's quite clear that, for some reason, the audio 'resource' is being locked in one way or another, and after one application stops using it, I have to wait until it releases its hold on it so I can play music again.
This can easily be 15-30 seconds, so it's pretty annoying.

Anyway, I knew that ubuntu was using pulseaudio along with alsa, but I didn't really understand what the difference was. I did some research and found out that pulseaudio was just an audio server, and alsa was more of a 'driver'(Is this right?)

I googled some stuff up and tried 'enabling pulseaudio' properly. It broke stuff. I tried reverting my steps, and it broke stuff. I then thought I might as well go all out, and remove pulseaudio, and lo and behold, it broke stuff. I fixed it to an extent, but not quite.

I reinstalled 9.10 fresh, and as soon as I start playing music and using chrome, I get the same issues.

What the hell is going on? What is it exactly that ubuntu is doing with pulseaudio? Do I need it? Does ubuntu even need it? Is it even remotely useful? Can ALSA not play audio from two audio sources at a time? 

As a side note, I'd like to point out that mpd is configured to use alsa, and I before I was going to try modifying its config to make it use pulseaudio, I tried making VLC use pulseaudio, and it lagged to **utter $#!7**. 

I'd really appreciate any help I can get - It's the "Intel Corporation 82801H (ICH8 Family) HD Audio Controller", and I'm thus using the snd_hda_intel modules, if that is of any importance. 

Thanks in advance.

---

