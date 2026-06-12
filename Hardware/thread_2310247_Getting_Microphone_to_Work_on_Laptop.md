---
title: "Getting Microphone to Work on Laptop"
date: 2016-01-17
forum: Hardware
---

### Post by RangerK on 2016-01-17
SITUATION

I just bought a microphone, the popular Audio-technica ATR2100.  On my box which doesn't have an internal mic, running Xubuntu 14.04, it works perfectly.  So I know the mic is fine.  On my laptop, a Dell Inspiron 5423, I can't get it to work.  

TROUBLE SHOOTING SO FAR

1)  The microphone shows up as Source option in Audio-Recorder.

[IMG]http://i.imgur.com/bJBdEVa.png[/IMG]

Despite being selected, Audio-Recorder pulls sound from the internal microphones, and no sound from the ATR2100 USB mic.

2)  Kazam.

The same thing happens if I use Kazam screencaster instead of Audio-Recorder.

3) Alsa Mixer -- "check default subdevice configuration" ([https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2FMicrophone_Troubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2FMicrophone_Troubleshooting)).

The ATR2100 USB mic appears as a separate sound card.
[IMG]http://i.imgur.com/ApNBwCk.png[/IMG]

But I can switch back and forth, turn down the levels on the internal microphone, and turn up the levels on the ATR2100.

[IMG]http://i.imgur.com/i500lt8.png[/IMG]

This didn't work either.  Only the faintest sound was recorded in Audio-Recorder and I assume it seemed like it from the internal microphones.

4)  Check Pulse Audio Volume meter.

The meter registered almost nothing unless I used Alsa Mixer to turn up the internal mics.

5) Set Microphone levels using pavucontrol

Under both "input devices" and "recording" I turned up the ATR2100 USB microphone and turned down the internal microphones.

[IMG]http://i.imgur.com/hyFrWid.png[/IMG]

The Pulse Audio Volume meter now clearly registered sounds in the microphone!!!  I thought I had fixed the problem.

But neither Audio-Recorder nor Kazam registered any sounds.

6) Edit alsa-base.conf.  ([https://www.youtube.com/watch?v=tULmqpe5Yos](https://www.youtube.com/watch?v=tULmqpe5Yos))

I scrolled to the end of the file and add the this "options  snd-hda-intel position_fix=1" as a new line, then rebooted.
This didn't seem to change anything.


Any help is appreciated.  Thanks!

---

### Post by howefield on 2016-01-17
Thread moved to the "*Hardware*" forum.

---

### Post by RangerK on 2016-01-18
bump

---

