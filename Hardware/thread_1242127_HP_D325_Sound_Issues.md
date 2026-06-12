---
title: "HP D325 Sound Issues"
date: 2009-08-16
forum: Hardware
---

### Post by sliggy on 2009-08-16
Hey everone,

I just recently installed Ubuntu on my HPD325, and I've manged to get all the drivers up and running just fine, except for sound. I've done a bit of research and found out from [this]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/12454-64287-89301-321881-f9-352427.html") page that my D325 has the "Integrated Soundmax AC97" soundcard, so after some more googling, I came across [this]("http://ubuntuforums.org/showthread.php?t=179322") thread, which claims to have fixed the problem.

I tried to do the [fix that he suggested]("http://ubuntuforums.org/showpost.php?p=1261847&postcount=9") by editing my alsa-base.conf and rebooting, but that did nothing. Does anyone have any ideas as to how I could get my sound working?

---

### Post by sliggy on 2009-08-17
Bump, I really need a solution for this.

---

### Post by sliggy on 2009-08-17
Bump again, come on guys, nobody has an answer?

---

### Post by sliggy on 2009-08-17
Just an update, I've also figured out that my output device for some reason is set to "Null Output (PulseAudio mixer)", and the only other option is "Monitor of Null Output". I'm pretty sure that this is what's the problem, since I think this should be set to Alsamixer. Does *anyone* have any clue as to how I could fix this?

---

