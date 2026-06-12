---
title: "volume control problem"
date: 2008-09-20
forum: General Help
---

### Post by Static42 on 2008-09-20
I recently installed OSS4 in attempt to make my creative X-Fi sound card to work. Now I followed the installation process, sound does work, but the sound is so low that I barely can hear it. I try to click on the Volume Control icon, but I get an error:

> No volume control GStreamer plugins and/or devices found.

I have no idea why it's doing that. Please, I could use some help.

---

### Post by zvacet on 2008-09-20
Look [here]("http://ubuntuforums.org/showthread.php?t=766683") or 

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Static42 on 2008-09-20
> **zvacet said:**
> Look [here]("http://ubuntuforums.org/showthread.php?t=766683") or 

```
sudo apt-get install ubuntu-restricted-extras
```

I installed the ubuntu restricted extras and restarted the computer, but it's still giving me that error. In the link that you provided, what exactly am I suppose to be looking for?

---

### Post by Static42 on 2008-09-20
Okay, I was able to somewhat fix the problem by installing gstreamer-ossv4-x86-32bit.tar.gz I found [here]("https://help.ubuntu.com/community/OpenSound"). The red x has disappeared from the volume control icon, which is good. However, one problem still remains: the volume is still very low. I am able to access the volume control bar, but it won't let me raise the volume to the max. It only goes half way, and if I try to raise the volume any higher, it just drops down to the half way point. I hope that makes sense.

---

### Post by Static42 on 2008-09-21
Hello, I'm still looking for a solution to my problem. Can anyone help?

---

### Post by mb_webguy on 2008-09-21
Are your speakers turned up?   Double-click on the volume icon in the notification area, turn Master down and every thing else (e.g. PCM, Front, etc.) all the way up, then gradually turn up Master until you get the volume you want.

Also, if you have external speakers with their own volume control, make sure they're turned up, also.  It sounds stupid, but I don't know how many times I've sat down at my computer and started wondering why I suddenly didn't have any sound, only to find out that someone had turned my speakers down.

---

### Post by Static42 on 2008-09-21
The picture below shows what I get when I click on the volume control icon.

[IMG]http://img.photobucket.com/albums/v91/SableyeRULES/ubuntuvolume.png[/IMG]

I don't have any other volume controls to mess with, and as I described earlier, the volume won't go any higher than that. The volume to my speakers are perfectly fine.

---

### Post by Static42 on 2008-09-23
I still have this issue. Can anyone help?

---

