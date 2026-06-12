---
title: "No audio with Fujitsu Amilo L7320GW laptop, Lubuntu 18.04"
date: 2018-11-27
forum: Hardware
---

### Post by dadaisnotdead on 2018-11-27
Hi everyone!

I'm having an issue with a Fujitsu Amilo L7320GW laptop running Lubuntu 18.04. It doesn't seem to play any audio.. The playback is shown in the PulseAudio Volume control (with the corresponding application, so if I start a video in VLC, the playback is shown in the volume control under VLC). I double checked and nothing is muted. I also tried all the tips in this post: [https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)
reinstalling asla-base and pulsaudio but it didn't resolve the issue.

Acording to this document: [http://datacomp.sk/img.asp?attid=9411](http://datacomp.sk/img.asp?attid=9411) the sound controller is in the VIA VT8237R+ chipset

Any help would be greatly appreciated!

Thank you in advance!

---

### Post by dadaisnotdead on 2018-11-30
Does anyone have any idea?

---

### Post by dadaisnotdead on 2019-01-09
Hi everyone!

Recently I've switched to Xubuntu 18.04 to try if it makes any difference but I didn't have any success so far...
I found this [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) very useful guide about sound troubleshooting and followed all the steps but none of the described solutions seemed to solve my issue.
I also wanted to try a BIOS update (as recommended in the last steps) but I already have the latest one provided for this laptop.

One interesting note though: I can't remember when it started but if I listen to the speakers/headphones very closely I can hear the sound playing super quietly (every possible volume settings is on max) so my assumption is that this sound card must be supported by Ubuntu?!

I did an ALSA test, you can find the results here:
[http://www.alsa-project.org/db/?f=e7e7f2c7e9cb10f56a710b102d60d0bbb351bf88](http://www.alsa-project.org/db/?f=e7e7f2c7e9cb10f56a710b102d60d0bbb351bf88)  

Any help would be greatly appreciated!

---

### Post by Yellow Pasque on 2019-01-10
Have you tried toggling this setting in alsamixer?:
```
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
```
Warning: If sound starts working, it may be loud if you have all the volumes maxed.

---

### Post by dadaisnotdead on 2019-01-10
Thank you for the tip!
Unfortunately turning the external amplifier on in alsamixer didn't resolve the problem...

---

### Post by Yellow Pasque on 2019-01-10
It was already on. Did you try turning it off and on? I got the idea from this thread: [https://www.insanelymac.com/forum/topic/67972-intel-82801db-ich4-ac97-audio-controller/](https://www.insanelymac.com/forum/topic/67972-intel-82801db-ich4-ac97-audio-controller/)

---

### Post by dadaisnotdead on 2019-01-11
yeah, it didn't work in either setting

---

### Post by Yellow Pasque on 2019-01-12
My only other (long shot) idea would be to toggle the "Duplicate Front" option.

---

