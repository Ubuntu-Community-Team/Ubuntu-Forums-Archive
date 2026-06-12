---
title: "[SOLVED] Soundcard problem...I think..."
date: 2008-08-08
forum: General Help
---

### Post by gjr5017 on 2008-08-08
When I first turn on my laptop I can play music just fine through any player (eg. Rhythmbox, Exaile, Banshee, etc). After my laptop has been on for a while when I try to play a song through any player (including totem by double clicking the song in the file explorer) they don't play at all and I can't play youtube videos or any multimedia content on the internet and I get zero sound from my other programs (pidgin, etc). I'm wondering what exactly the problem might be. Running Hardy (x86) on a compaq laptop. 2 GB RAM, Conexant High-Def audio, nvidia 7000m, amd turion 64x2 @ 1.9 GHz. Thanks in advance.

---

### Post by Ryadt on 2008-08-08
It's probably a problem related to pulse audio.
Try in terminal
```
killall pulseaudio
```
This might solve it.

---

### Post by gjr5017 on 2008-08-08
I did that and I still cant watch youtube videos or anything like that and now rhythmbox wont maximize from the notification area. But I can play music through Banshee...

Edit: I restarted firefox and I can watch youtube videos and I killed the rhythmbox process and reopened it and I can play music from it....

How do I stop the pulseaudio thing from happeneing?

---

### Post by Ryadt on 2008-08-08
> **gjr5017 said:**
> I did that and I still cant watch youtube videos or anything like that and now rhythmbox wont maximize from the notification area. But I can play music through Banshee...

Edit: I restarted firefox and I can watch youtube videos and I killed the rhythmbox process and reopened it and I can play music from it....

How do I stop the pulseaudio thing from happeneing?

Go to System > Preference > Sound and change everything to ALSA.

---

### Post by gjr5017 on 2008-08-08
> **Ryadt said:**
> Go to System > Preference > Sound and change everything to ALSA.

Okay. I did that. Hopefully I wont have anymore problems with it. Thanks a lot for your help.

---

### Post by Ryadt on 2008-08-08
Can you please mark the threat as solved please...:popcorn:

---

### Post by Nepherte on 2008-08-08
If that doesn't work, you can actually try to fix pulseaudio: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

