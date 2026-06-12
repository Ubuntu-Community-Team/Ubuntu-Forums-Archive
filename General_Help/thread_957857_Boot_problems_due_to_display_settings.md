---
title: "Boot problems due to display settings"
date: 2008-10-24
forum: General Help
---

### Post by wildmanne39 on 2008-10-24
Hi I have a nvidia card in my hp laptop, it was working fine until I started changing my display settings. After boot I get a white screen. I am using kubuntu 8.10 can anyone tell me how to change my display settings when my computer is booting up? Thanks in advance.

---

### Post by ddrichardson on 2008-10-25
Can you get another tty by pressing <CTRL>+<ALT>+<F1>?

If so, login and type:
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

