---
title: "Sound issues"
date: 2011-02-28
forum: Hardware
---

### Post by livecdobsessed on 2011-02-28
After attempting to repair my soundcard drivers as suggested in another thread, my card doesn't show up in ALSA at all. Full output of the wget command for alsa:
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.7sAq2W0pC5/alsactl.tmp: No such file or directory
 [http://www.alsa-project.org/db/?f=239b6983b706be994758af0fca85f1ed23863539](http://www.alsa-project.org/db/?f=239b6983b706be994758af0fca85f1ed23863539)
Help, please? I really want my sound back.

---

