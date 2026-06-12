---
title: "kubuntu 9.10 ICH10R AD198x audio + ATI HDMI audio problems"
date: 2009-11-28
forum: Hardware
---

### Post by edccorp on 2009-11-28
I have kubuntu 9.10 and a i have problem with sound. My sound card is recognized but sometimes after boot i get message audio playback device hda intel (ad198x analog) does not work falling back to HDA ATI HDMI and i don't have sound at all, after that KDE informs me that sound device is removed and asks if i want that it forgets about that device (i choose no). I have used alsa update script to update alsa 1.0.21 but same problem continues to happen. I noticed that many people with similar configuration ich8-9-10 sound + ati hdmi sound have problems with audio. Both ad198x and ati hdmi use snd-hda-intel module, may be is that source of the problem? How to remove ATI HDMI sound card when it uses same driver module as ad198x? I'm using freshly installed kubuntu 9.10 with all updates. Please help!

---

### Post by arigram on 2009-12-21
> **edccorp said:**
> I have kubuntu 9.10 and a i have problem with sound. My sound card is recognized but sometimes after boot i get message audio playback device hda intel (ad198x analog) does not work falling back to HDA ATI HDMI and i don't have sound at all, after that KDE informs me that sound device is removed and asks if i want that it forgets about that device (i choose no). I have used alsa update script to update alsa 1.0.21 but same problem continues to happen. I noticed that many people with similar configuration ich8-9-10 sound + ati hdmi sound have problems with audio. Both ad198x and ati hdmi use snd-hda-intel module, may be is that source of the problem? How to remove ATI HDMI sound card when it uses same driver module as ad198x? I'm using freshly installed kubuntu 9.10 with all updates. Please help!

I have the same problem and we would very much appreciate a solution.

---

### Post by rickgo on 2009-12-21
i have the same problem also

---

### Post by jim_24601 on 2009-12-22
It is not restricted to ATI; I have the same problem with an nVidia motherboard and onboard sound. A reboot fixes it, but it is still annoying. I might be tempted to think that, in their efforts to speed up the boot process, the ubuntu guys introduced a race condition whereby KDE sometimes probes the sound card before it's done initialising. Of course, that's just a crazy guess.

---

### Post by drkronic on 2009-12-23
I have it too! This is a hugely annoying problem. Anyone find a fix yet (other than rebooting)?

---

### Post by hakcayurek on 2009-12-26
I have removed pulseaudio  and it seems to me it solved the problem.
apt-get --purge pulseaudio


 (I get the missing devices warning when I start a new kde session, but it will probably go away when I select remove or reboot the my machien).

---

### Post by jim_24601 on 2010-01-04
I haven't seen this problem in a week or so. It might have been fixed by a regular update in the meantime. Can anybody confirm that it is or isn't still a problem?

---

### Post by OmniBlade on 2010-01-24
I have the same problem and can't seem to find a working fix for it either. I have onboard NVidia ALC888 and ATI HDMI and will randomly get the notification that the ALC888 has been removed (sometimes on startup, sometimes when running a kde app that uses the audio) after which any application that uses phonon tries to fall back to ATI HDMI saying it can't use the NVidia ALC888. Any application that uses alsa directly and does not use phonon (basically anything not kde native) works fine, even the kde log out sound. This is on a fully updated clean install of 9.10.

---

