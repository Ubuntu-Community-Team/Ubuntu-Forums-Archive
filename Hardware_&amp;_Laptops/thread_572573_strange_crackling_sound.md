---
title: "strange crackling sound"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by martbab on 2007-10-10
Hello everyone,

I have problem with strange static-like crackling sound occuring when listening to music in Xubuntu. I have tweaked settings in alsamixer as described in various other threads, set the PCM as low as possible but the crackling sound persists.

At first I thought there might be something with my speakers but the sound is crystal clear in Windows.

I am using laptop with

"Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)" 

as lspci told me

I'm pretty new in Linux so I'd appreciate any help. :)

---

### Post by jongkind on 2007-10-10
With Ubuntu 7.10 beta (Gutsy) the problem was associated too Rhythmbox, and which could be solved by enabling crossfading in the preferences menu:
[http://ubuntuforums.org/showpost.php?p=3469910&postcount=6]("http://ubuntuforums.org/showpost.php?p=3469910&postcount=6")

You don't mention which Xubuntu version and music player you use, though.

---

### Post by martbab on 2007-10-11
I'm using Xubuntu 7.10 and MOC player.

---

### Post by martbab on 2007-10-13
I have compiled MOC player v2.4.3 with ALSA and JACK support and it seems the problem is gone, the sound is OK again. Looks like there is some bug in old version 2.4.1.

---

