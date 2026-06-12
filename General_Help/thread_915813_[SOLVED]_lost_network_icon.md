---
title: "[SOLVED] lost network icon"
date: 2008-09-10
forum: General Help
---

### Post by verbal.kint on 2008-09-10
this is kinda retarded but i deleted an icon from my panel in the top right hand corner( beside the time and date), it was the network icon that allowed me to choose a wired connection or wireless connection, does anyone know how i can get it back???

---

### Post by iaculallad on 2008-09-10
> **verbal.kint said:**
> this is kinda retarded but i deleted an icon from my panel in the top right hand corner( beside the time and date), it was the network icon that allowed me to choose a wired connection or wireless connection, does anyone know how i can get it back???

You could just reinstall the GNOME applets:

```
sudo apt-get install --reinstall gnome-applets
```

---

### Post by WRDN on 2008-09-10
Right click on the panel, and select Add to Panel, then find the applet in the list. Alternatively, if you are referring to the network manager (nm-applet), then press Alt and F2, then type "nm-applet" in the text box. To start this automatically, click System > Preferences > Sessions, and check the tick-box for "Network Manager" from the "Startup Programs" list. If it is not listed, click Add and use the command "nm-applet --sm-disable".

---

### Post by Elfy on 2008-09-10
It's notification area I believe - add it as WRDN has said.

---

### Post by verbal.kint on 2008-09-10
thanks i got it working, i think it was the notification area that i actually got rid of

---

