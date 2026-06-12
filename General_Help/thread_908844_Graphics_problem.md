---
title: "Graphics problem"
date: 2008-09-02
forum: General Help
---

### Post by slaapp on 2008-09-02
hi im new to ubuntu and i have a problem with my resolution settings i have a GeForce 8400 gs 256mb Graphics card and and it only let me set it at 640x480 not higher i think it the drivers and dunno where to get them or download them to my comp any can anyone help plz ?

---

### Post by falcon61102 on 2008-09-02
There is an app that will autodetect and install the drivers for you for your card, its called Envyng.  You can find it either in the Synaptic Package Manager or install it using the terminal with:
```
sudo apt-get install envyng-gtk
```

It will download and install the drivers for you, then reboot and you should be good to go.

Once installed you can further tweak the settings using the following:
```
sudo nvidia-settings
```

---

