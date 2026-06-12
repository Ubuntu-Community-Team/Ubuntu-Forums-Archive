---
title: "AWN Won't work!"
date: 2008-08-18
forum: General Help
---

### Post by History500 on 2008-08-18
Hey, whenever I try to open Avant-window-navigator, It just flashes a grey box in the side of my screen and never starts..... Could someone HELP?

---

### Post by overdrank on 2008-08-18
> **History500 said:**
> Hey, whenever I try to open Avant-window-navigator, It just flashes a grey box in the side of my screen and never starts..... Could someone HELP?

Hi and welcome, I have moved your thread to a appropriate sub-forum. If you are using AWM you will need to use compiz also. What is the model of the graphics card? You can try and enable compiz under system, preferences, appearance, visual tab and then select there.

---

### Post by History500 on 2008-08-18
> **overdrank said:**
> Hi and welcome, I have moved your thread to a appropriate sub-forum. If you are using AWM you will need to use compiz also. What is the model of the graphics card? You can try and enable compiz under system, preferences, appearance, visual tab and then select there.
I would.... but i'm using ubuntu in virtualbox, any way to get the graphics to work easily from there?

---

### Post by angry_johnnie on 2008-08-18
You won't be able to use compiz in a virtual machine, but you can still use AWN, if you enable metacity's own compositor.

press alt + f2, and type:

```
gconf-editor
```

press enter

find **Apps > Metacity > General**

and check the box next to **compositing_manager**

That should allow you to use AWN, even without compiz.

---

### Post by History500 on 2008-08-18
YES! Thank you!

---

### Post by Stan_1936 on 2008-08-18
Are you able to get a 3D look to the dock without running Compiz Fusion?

---

### Post by angry_johnnie on 2008-08-19
> **Stan_1936 said:**
> Are you able to get a 3D look to the dock without running Compiz Fusion?

Yes. :-)
Sorry about the delay.  Just right click on the dock, and in the window that pops up, go to **General > Bar Appearance > Look**, and choose 3d look.

---

