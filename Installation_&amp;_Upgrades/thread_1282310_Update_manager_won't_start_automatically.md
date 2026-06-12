---
title: "Update manager won't start automatically"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Pitboss on 2009-10-04
Hi. I have a strange problem recently. The update manager won't start automatically, despite the fact that the option in settings > updates > check for updates > is set on daily? How can I fix this problem?

---

### Post by Partyboi2 on 2009-10-04
When was the last time you got updates? You can open a terminal (Applications>Accessories>Terminal) and check if there are any updates with
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Pitboss on 2009-10-04
In fact I got updates few minutes before posting here, because I logged in tty1 and I saw that there were many packages ready to be updated (tty1 obviously checks automatically for updates when I log in) so I ran update-manager manually... But this is not the first time I update manually, I've done it two or three times so far and it's beginning to annoy me.

---

