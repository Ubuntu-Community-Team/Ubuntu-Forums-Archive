---
title: "Audio disappeared in Ubuntu Studio 21.10 with KDE desktop"
date: 2022-02-13
forum: Hardware
---

### Post by david-daking on 2022-02-13
Recently all my audio disappeared in Ubuntu Studio 21.10 with KDE desktop.

It all worked fine until today, and now there is no audio. I installed Kmix and the sound came back, but in the KDE System Settings program it no longer lists any section for Audio, which was there before.

The volume icon had disappeared from the main Panel, but one reappeared after installing Kmix, at which point audio was working again, but just for a short time, as the audio stopped working again after rebooting.

I had tried uninstalling and reinstalling pulseaudio but no change.

I have tried restarting pulseaudio, or using pulseaudio -k to kill it which had worked yesterday when the audio did not come on at bootup, but it had worked okay after that. Today even that does not work.

What can I do to get back the audio? And to have it listed in the System Settings? And to get back the original icon for sound in the Panel that I had before?

---

### Post by him610 on 2022-02-14
I have a similar issue, Xubuntu 20.04.3 LTS Linux h270m 5.13.0-28-generic, noticed just today.

Even though *alsa-utils* are installed, *alsamixer* can not be run from command line.
Usually present input and output devices are not showing up in *pavucontrol*.
Previously, the audio devices could be seen in *pavucontrol*.
```
$ inxi -Axx
Audio:     Device-1: Intel 200 Series PCH HD Audio vendor: ASRock driver: N/A bus ID: 00:1f.3 
           chip ID: 8086:a2f0 
           Device-2: NVIDIA GK208 HDMI/DP Audio driver: N/A bus ID: 01:00.1 chip ID: 10de:0e0f 

```

Out of ideas. Maybe someone else has some advice.

---

### Post by #&amp;thj^% on 2022-02-14
It's not uncommon for an updated kernel breaking sound, I have not seen any fresh bugs on this yet. ;)
Good place to start until we know for certain that was the case: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by him610 on 2022-02-16
@1fallen
> Good place to start until we know for certain that was the case: [https://help.ubuntu.com/community/So...otingProcedure](https://help.ubuntu.com/community/So...otingProcedure)

Thanks for the suggestion. I wound up posting my issue on launchpad. Here is a link to the thread with resolution, [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/700635]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/700635")

---

