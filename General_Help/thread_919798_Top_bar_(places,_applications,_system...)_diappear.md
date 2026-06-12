---
title: "Top bar (places, applications, system...) diappeared"
date: 2008-09-14
forum: General Help
---

### Post by ziiiphyr on 2008-09-14
After enabling Chinese language support the language support tool and installing the appropriate packages through synaptic, the top bar disappeared upon restarting the machine. Basically I can't launch any program now except for the Nautilus. 

I tried to create a launcher on the Desktop and that failed too!

Has anyone had similar experience? 

Thanks a lot.

---

### Post by zvacet on 2008-09-14
**Right click on panel>add to panel**>scroll down and you will see Ubuntu logo (not main menu ; I don´t know real name because I don´t use English version) and add it to panel.That should be it.

---

### Post by Raffles10 on 2008-09-14
I would suggest complete removal & re-installation of the Gnome panel:

```
sudo apt-get remove --purge gnome-panel
```

&

```
sudo apt-get install gnome-panel
```

---

### Post by ziiiphyr on 2008-09-15
Hey guys
Thank you for the responses. I noticed that the gnome-panel was removed somehow, maybe because I was messing with something else that I didnt noticed. 

After re-installing the gnome-panel, everything worked out fine. 

Thanks a lot.

---

