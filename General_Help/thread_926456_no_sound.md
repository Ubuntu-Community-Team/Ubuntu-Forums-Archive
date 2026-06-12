---
title: "no sound"
date: 2008-09-21
forum: General Help
---

### Post by xmunk on 2008-09-21
Hi Im running hardy and suddenly my sound just died.  was watching youtube then stopped to eat came back no sound in firefox, vlc, mplayer, audacious, or anything else.  i've switched my sound settings to alsa to pulse, to oss, and still nothing.  I'm at a bit of a loss. tried [http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem]("http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem") didn't work tried switching sound servers after all that and still doesn't work.

any help will be appreciated ;)

---

### Post by gukina on 2008-09-22
Open terminal then paste this in.

```
sudo /etc/init.d/alsa-utils restart
```

Are you using headphones? right click on the speaker in the panel than 'open volume control panel' click on the switch tab for headphones off then back on.

---

### Post by xmunk on 2008-09-22
nope didnt work and no im not using head phones speakers work plug them into another comp. and worked just fine

---

### Post by xmunk on 2008-09-22
anyone got any more suggestions?

---

