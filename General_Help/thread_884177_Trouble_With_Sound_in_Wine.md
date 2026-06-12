---
title: "Trouble With Sound in Wine"
date: 2008-08-08
forum: General Help
---

### Post by MikeWanDo on 2008-08-08
I'm using Pulse Audio and I have the checkbox next to ALSA checked in Wine. When I push the "Test Sound" button it makes a noise, a sort of doo-doo-doop. But when I run an application I can't get any sound out of it. I've tried both Teamspeak and VLC media player. Neither puts out sound. The other odd thing is that I can talk in Teamspeak and it sound fine, but I can't hear anything and VLC plays but no sound comes out. I have hardy on AMD64 if that matters with Wine from the ubuntu repos.

---

### Post by Vivaldi Gloria on 2008-08-08
> **MikeWanDo said:**
> I'm using Pulse Audio and I have the checkbox next to ALSA checked in Wine. When I push the "Test Sound" button it makes a noise, a sort of doo-doo-doop. But when I run an application I can't get any sound out of it. I've tried both Teamspeak and VLC media player. Neither puts out sound. The other odd thing is that I can talk in Teamspeak and it sound fine, but I can't hear anything and VLC plays but no sound comes out. I have hardy on AMD64 if that matters with Wine from the ubuntu repos.

Why on earth are you using vlc with wine when there is a native ubuntu one? Get it using synaptic. You need to enable multiverse & restricted repos in the repository settings of synaptic and click refresh. Then search and install vlc.

To fix sound problems see the guide

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I choose oss in wine and start wine apps with

```
padsp wine <application>
```

as mentioned in the appendix of the link above.

---

### Post by MikeWanDo on 2008-08-08
I just installed VLC in Wine to test the sound, not that I play my music through it. Thought it might just be an issue with Teamspeak since the sound test in Wine config makes noise.

---

### Post by Vivaldi Gloria on 2008-08-08
> **MikeWanDo said:**
> I just installed VLC in Wine to test the sound

OK. Now it makes sense. ;)

I don't know what teamspeak is so I cannot comment on it.

Anyway, try the above method.

---

### Post by MikeWanDo on 2008-08-08
I tried that but still no luck.

---

### Post by Vivaldi Gloria on 2008-08-08
> **MikeWanDo said:**
> I tried that but still no luck.

Have you chosen OSS in wine? What happens when you start your app with padsp in the terminal. Do you get any errors?

---

