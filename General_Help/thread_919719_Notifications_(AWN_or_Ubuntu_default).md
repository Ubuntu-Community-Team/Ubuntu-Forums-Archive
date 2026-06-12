---
title: "Notifications? (AWN or Ubuntu default)"
date: 2008-09-14
forum: General Help
---

### Post by Grimhound on 2008-09-14
Is there any way to get it so that program activity from things like Pidgin or MUD clients cause the icon/box/whatever to give a notification in some way shape or form to let me know someone has sent me a message or as done something? If not in GNOME as found on Vanilla Ubuntu, then perhaps on AWN or something similar? It's a big thing bugging me. :|

---

### Post by chewearn on 2008-09-14
For pidgin, installing pidgin-libnotify will give you "Libnotify Popups" plugin, where you can specify when you want a popup balloon to appear (e.g. new messages, buddy signon/off).

```
sudo apt-get install pidgin-libnotify
```

---

