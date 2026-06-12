---
title: "minimized windows dont show up in lower panel"
date: 2008-11-06
forum: General Help
---

### Post by sdowney717 on 2008-11-06
They are just gone, but still running.

We have a computer doing this, my inlaws. I think he changed something.
The lower panel should have the minimized window titles but it is just blank when minimized.
Also, when the windows are minimizing, the outline heads down towards the extreme bottom right corner.
I added a panel widget that will show the windows when clicked.
The real problem is you dont know how many windows are open, and they pile up on him till his computer bogs down.

---

### Post by Tamlynmac on 2008-11-06
Right click on the panel and select "Add to Panel"
Left click on "Window List" applet then click on the "Add" button on the bottom
Close "Add to Panel"

This should solve your problem.

---

### Post by sdowney717 on 2008-11-06
great, I will try it out. I just tried it on my own PC and now have a double set.
So, how do you remove the window list?

I got it, you have to right click on the forward edge and select remove from panel

---

### Post by zvacet on 2008-11-07
If that doesn´t help delete all your gnome settings to get back to the default 

```
sudo /etc/init.d/gdm stop

rm -rf .gconf* .gnome* .nautilus*

sudo reboot
```

---

