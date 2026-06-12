---
title: "Help I have no sounds after upgrading to 8.10"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Doulpe on 2008-12-30
After upgrading I am having some trouble with my sound being there is none. I have gone through several commands to reinstall Alsa but when i type in Sudo ./alsa_2.sh it doesn't work, but the first one does whats going on?

---

### Post by stderr on 2008-12-30
If you go System -> Preferences -> Sound you can change what's configured to play sounds for different events. If you try Pulseaudio for instance, and then hit Test, does that work?

In regard to ALSA, maybe restarting it will help?

```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by Doulpe on 2008-12-30
Nah, none of the methods you described works I don't know if this would help but when i try to play Music on XMMs it says please check that your soundcard is configured properly, you have the correct output plugin selected and no other program is blocking the soundcard.

---

