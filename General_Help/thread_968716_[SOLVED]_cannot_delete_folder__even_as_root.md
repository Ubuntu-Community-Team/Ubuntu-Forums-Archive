---
title: "[SOLVED] cannot delete folder ??? even as root"
date: 2008-11-02
forum: General Help
---

### Post by markg48 on 2008-11-02
trying to delete a folder on my desktop  but it wont let me tried running krusader file manager as root  but that did work as well any ideas how to delete folder ?? -.-

---

### Post by lollylegs on 2008-11-03
Hi Mark
I'm a newbie to ubuntu, but the thread below may help.


ph.ubuntuforums.com/showthread.php?t=916303

---

### Post by aysiu on 2008-11-03
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R $USER:$USER $HOME/Desktop
``` and then try again to delete it.

---

### Post by markg48 on 2008-11-03
thank you ! the terminal command work now i can delete  the unwanted files
thanks for replying so fast :)

---

