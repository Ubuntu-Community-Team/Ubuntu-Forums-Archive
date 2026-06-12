---
title: "Asus M50sv-B1 Sound Issue"
date: 2009-06-03
forum: Hardware
---

### Post by Darkdelusions on 2009-06-03
I am running into a bit of an issue trying to get my speaker to auto mute when my headset is plugged in I have searched and searched for an answer however every thing that is suggested has not worked. 

So far I have 

Upgraded alsa to 1.20
Added options options snd-hda-intel model=laptop
Added options snd-hda-intel model=3stack-dig position_fix=0

Pretty much everything is the following posts have been tried 

[http://ubuntuforums.org/showthread.p...k+speaker+both](http://ubuntuforums.org/showthread.p...k+speaker+both)
[https://help.ubuntu.com/community/De...gSoundProblems](https://help.ubuntu.com/community/De...gSoundProblems)
[http://ubuntuforums.org/showthread.p...=1#post3309424](http://ubuntuforums.org/showthread.p...=1#post3309424)
[http://ubuntuforums.org/showthread.php?t=302543](http://ubuntuforums.org/showthread.php?t=302543)

LS PCI
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

Audio Code
```
Codec: Realtek ALC1200
Codec: Motorola Si3054

```

---

### Post by Darkdelusions on 2009-06-03
Does anyone know what switch needs to go into the alsabase.conf file for this card. The I have not been able to find it in the alsa information and using my headset on my laptop is crucial

---

### Post by Yellow Pasque on 2009-06-03
```
options snd-hda-intel model=3stack-dig position_fix=0 **probe_mask=1**
```

---

### Post by Darkdelusions on 2009-06-04
OK I sloved this the correct switch is options snd-hda-intel model=3stack-dig

---

### Post by Darkdelusions on 2009-06-19
OK time to rez this post from the dead. I thought I had this issue fixed till tonight I went and plugged my headset it and put on some music and noticed it still not working correct. 

I have the options snd-hda-intel model=3stack-dig position_fix=0 probe_mask=1 in my alsabase.conf file but all of a sudden tonight it stopped working.

---

### Post by Darkdelusions on 2009-06-30
Anyone have anymore ideas?

---

