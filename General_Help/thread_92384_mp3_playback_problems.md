---
title: "mp3 playback problems"
date: 2005-11-19
forum: General Help
---

### Post by Bachstelze on 2005-11-19
Not so long ago, when I still was a you-know-which-OS user, I used iTunes to read my mp3, which I enjoyed quite much. After switching to linux, I was told that amaroK or Rythmbox would be nice replacements. Indeed they are, except for one point : they won't read my mp3s, which is quite annoying :p All other players (Mplayer, Totem, VLC, XMMS) read them fine but amaroK tells me "non readable file" and Rythmbox "not an audio stream". Any ideas ?

---

### Post by gapplewagen on 2005-11-19
gstreamer0.8-mad is required to get Rhythmbox to play mp3's.  Get it from either Synaptic or via:

sudo apt-get install gstreamer0.8-mad

---

### Post by Bachstelze on 2005-11-19
Thanks dude, it works fine :)

---

### Post by gapplewagen on 2005-11-19
No problem.  I've been trying to get version 0.9.1 from the backports but they seem to not be working (for me?).  Take a look at the changelog and you'll see why I want it (mostly iTunes music sharing).

Changelog:  [http://ubuntuforums.org/showthread.php?t=78720](http://ubuntuforums.org/showthread.php?t=78720)

---

