---
title: "upgrade/repair?"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by silverbullet007 on 2009-03-10
Possibly a silly question here but it never hurts to ask right?

Using a boot/live cd, is there a way to "repair" and current installation of Ubuntu?  Reason being, I've got a laptop running 8.10 now for a while.. everything works except the Update manager.  It shows there are important updates pending.. however opening the applet and clicking to Install Updates doesnt actually do anything.

I dont want to blow my install away with a fresh one but I would like to repair this issue if at all possible.

Thanks!

---

### Post by taurus on 2009-03-10
Just boot your Ubuntu (from the harddrive, not the LiveCD).  Log in.  Then, open a terminal and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by silverbullet007 on 2009-03-10
I knew I could get around it.. but the issue still remains.  Also it seems that I cannot start Synaptic from the gui menu option.

---

