---
title: "Help! Black screen at bootup"
date: 2008-08-02
forum: General Help
---

### Post by weweboom on 2008-08-02
when i boot up ubuntu, it shows the tty screen, and i can't get out of it, i tried repairing the x server in recovery mode, but nothing happened, I think i screwed up my xorg.conf but i'm not sure. help please

---

### Post by freebeer on 2008-08-02
Are you logged in?

at the command prompt try:

```

sudo dpkg-reconfigure xserver-xorg

```

---

