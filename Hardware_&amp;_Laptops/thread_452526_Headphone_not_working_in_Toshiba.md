---
title: "Headphone not working in Toshiba"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by Adrain on 2007-05-23
I installed Ubuntu 7.04 on a Toshiba Satellite L35. I was getting no sound at all earlier, even though it detected my sound-card(ATI SB450 HDA Audio/Realtek ALC861-VD), but adding "options snd-hda-intel model=3stack" to "/etc/modprobe.d/alsa-base" seemed to fix that. Now I'm getting sound out of the speakers, but I'm not getting any sound out of the headphone jack. I went into alsamixer and unmuted the headphone jack, but I can't raise the volume. It doesn't even have "00" under the volume bar.

---

### Post by stchman on 2007-05-23
> **Adrain said:**
> I installed Ubuntu 7.04 on a Toshiba Satellite L35. I was getting no sound at all earlier, even though it detected my sound-card(ATI SB450 HDA Audio/Realtek ALC861-VD), but adding "options snd-hda-intel model=3stack" to "/etc/modprobe.d/alsa-base" seemed to fix that. Now I'm getting sound out of the speakers, but I'm not getting any sound out of the headphone jack. I went into alsamixer and unmuted the headphone jack, but I can't raise the volume. It doesn't even have "00" under the volume bar.

You need to add the headphones in the preferences.  When you do that check the box to enable the headphone jack.  The thing now with my laptop is that when I have the headphones plugged in the speakers work at the same time.  I would really like to find a way to listen with headphones and not have the speakers on.

Hope this helps.

---

### Post by Adrain on 2007-05-23
Preferences > Sound or Preferences > Hardware Information? I don't see any option under Preferences > Sound for adding headphones.

---

### Post by Adrain on 2007-05-23
bump

---

### Post by karmahaus on 2007-06-01
> **Adrain said:**
> I installed Ubuntu 7.04 on a Toshiba Satellite L35. I was getting no sound at all earlier, even though it detected my sound-card(ATI SB450 HDA Audio/Realtek ALC861-VD), but adding "options snd-hda-intel model=3stack" to "/etc/modprobe.d/alsa-base" seemed to fix that. Now I'm getting sound out of the speakers, but I'm not getting any sound out of the headphone jack. I went into alsamixer and unmuted the headphone jack, but I can't raise the volume. It doesn't even have "00" under the volume bar.
Well, now we are two in the same situation. I also have a Toshiba L35 with exactly the same problem and after doing just what you did (following some suggestions given in this forum) I now have sound in the speakers but when I plug the headphones the speakers mutes but there is still no sound in the headphones. Some people in this forum had a similar problem with this sound-card but they ended with sound on BOTH, headphones and speaker at the same time. And obviously this is not the case. Have you found a solution?

---

### Post by H4ck3rx on 2008-02-17
Add this line to end of "/etc/modprobe.d/alsa-base"
```
options snd-hda-intel model=lenovo
```
Then run this command:
```
sudo alsa force-reload
```

---

