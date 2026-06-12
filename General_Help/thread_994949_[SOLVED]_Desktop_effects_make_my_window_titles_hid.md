---
title: "[SOLVED] Desktop effects make my window titles hidden"
date: 2008-11-27
forum: General Help
---

### Post by Gharchkhor on 2008-11-27
I just installed my geforce 6200 with NVidia binary X.Org driver ('version 96' driver) and everything works fine and i have 3d rendering but the only problem is when i choose to enable desktop effects it makes my window titles (AKA window borders, that orange (on human theme) title bar) go hidden, and when i revert back to no effects at all the window titles come back.

any ideas?:confused:

---

### Post by abbec on 2008-11-27
Try enabling the window decoration in ccsm (Settings manager for compiz)...

---

### Post by eternalnewbee on 2008-11-27
If you have the compiz fusion icon installed, run it, and right-click on it. Then choose Select Window Decorator and select GTK.
I'm running emerald (you can find it in **Synaptic Package Manager**, under: **Main Menu > System > Administration**). Once emerald is installed, press **ALT-F2** and enter ```
emerald --replace
```
If you want it to start up with the system, go to: **Main Menu > System > Preferences > Sessions > Options** tab, and click on **Remember Currently Running Applications**.

---

### Post by eternalnewbee on 2008-11-27
> Try enabling the window decoration in ccsm (Settings manager for compiz)...
Indeed.

---

### Post by Gharchkhor on 2008-11-27
> **abbec said:**
> Try enabling the window decoration in ccsm (Settings manager for compiz)...
I'm new to compiz and desktop effects, would you explain where's ccsm or how can i have access to it?

---

### Post by eternalnewbee on 2008-11-27
> I'm new to compiz and desktop effects, would you explain where's ccsm or how can i have access to it?
If you are running 8.10, it would be here: **Main Menu > System > Preferences > CompizConfig Settings Manager**. Then scroll down till you see **Window Decoration**, under **Effects**.

---

### Post by Gharchkhor on 2008-11-27
Damn it wasn't even installed! installed "Advanced Desktop Effects Settings (ccsm)" from Add/remove...  and then opened it as you said, but "window decoration" is already enabled itself, what's wrong then?

---

### Post by eternalnewbee on 2008-11-27
OK. try this first: Press **ALT-F2**, and copy & paste ```
compiz --replace
```. Then press ALT-F2 once more and copy & paste ```
emerald --replace
```

---

### Post by Gharchkhor on 2008-11-27
nothing happened :(

---

### Post by Opeth115 on 2008-11-27
try typing this into the terminal and then restart X with ctrl + alt + backspace

> nvidia-xconfig --add-argb-glx-visuals


---

### Post by Gharchkhor on 2008-11-27
> **Opeth115 said:**
> try typing this into the terminal and then restart X with ctrl + alt + backspace
This worked, thank you, i love Ubuntu :popcorn:

---

### Post by eternalnewbee on 2008-11-27
> This worked, thank you, i love Ubuntu
Glad it worked. Now you can mark this thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

### Post by Opeth115 on 2008-11-27
> **Gharchkhor said:**
> This worked, thank you, i love Ubuntu :popcorn:

np :)

---

