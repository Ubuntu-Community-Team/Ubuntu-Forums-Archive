---
title: "Ubuntu/kubuntu loading bar"
date: 2008-10-02
forum: General Help
---

### Post by hoo2 on 2008-10-02
I have a kubuntu box and i've decide to switch over gnome. I have installed gnome and also gdm for the default desktop manager. The only think is that i don't know how to change the kubuntu loading bar at boot time to the ubuntu loading bar.
I've try to reconfigure gdm and to remove kdm and kdm4 but nothing. I still see the kubuntu loading bar. 
Does any one knoww from where can i configure this?

---

### Post by hoo2 on 2008-10-03
I've found a program called StartUp-Manager and i already change the Usplash theme. 
But the question remains. Where is the configuration file for this....

---

### Post by LowSky on 2008-10-03
if you install ubuntu-desktop it will also autoinstall the boot loader. If you just add gnome it will not

in terminal type

```
sudo apt-get install ubuntu-desktop
```

---

