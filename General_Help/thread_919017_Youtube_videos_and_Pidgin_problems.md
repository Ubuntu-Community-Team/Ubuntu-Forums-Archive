---
title: "Youtube videos and Pidgin problems"
date: 2008-09-13
forum: General Help
---

### Post by mew2akuro on 2008-09-13
Whenever I log into Pidgin Instant messenger, it wont let me play youtube videos!  I also have a problem with youtube and movie player, movie player and java chatrooms, and chatrooms and pidgin... its like a big multitasking nightmare!! plz help!!

---

### Post by northern lights on 2008-09-13
Are you certain the simultaneous use of more than one of the problematic apps is the culprit indeed?

What flash player do you use?
What mozilla video plugin?

Run ```
sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install flashplugin-nonfree mozilla-mplayer
```

Any better?

---

### Post by mew2akuro on 2008-09-13
Yes, I'm sure it's whats keeping me from using things simultaneously.

---

### Post by mew2akuro on 2008-09-13
Thanks, it does help.

---

