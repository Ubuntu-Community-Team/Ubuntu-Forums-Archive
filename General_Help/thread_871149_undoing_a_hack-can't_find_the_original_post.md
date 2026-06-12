---
title: "undoing a hack-can't find the original post"
date: 2008-07-26
forum: General Help
---

### Post by kyfho23 on 2008-07-26
Hi, I hope someone with better searching skills, or a better memory can help. There was a post here, that I applied, that loaded Firefox during the boot-up stage-it shows on my screen during boot up as cat: /usr/bin/firefox cat: /usr/lib/firefox and cat: usr/share/firefox. I've spent the last 2 hours trying to find the post-does this ring any bells with anyone?

As I remember, it was added to either an /etc/rc or a /boot/ file.

Thank you. I really have tried to find it on my own.

Chris

---

### Post by sdennie on 2008-07-26
I'm not sure what post you are talking about but, if it was to try to load firefox into the cache by catting it to /dev/null, it was probably done in /etc/rc.local.

---

### Post by kyfho23 on 2008-07-26
Yes, it was. Thank you VERY much.

---

