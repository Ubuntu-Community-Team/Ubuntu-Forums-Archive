---
title: "[SOLVED] No Cube no effects!"
date: 2008-11-05
forum: General Help
---

### Post by ellitsas on 2008-11-05
Hello everyone! I just installed Ubuntu 8.10 fresh without Windows. I don't seem to manage to activate the cube and other effects. I have compiz but it doesn't work. Also under the "Appearance" menu "custom" doesn't appear. I have an Nvidia card, i don't know exactly the model, but it used to work with 3D acceleration. I'm sorry i'm not providing enough but i'm new to this so i don't know much. I just wanna  "plug & play". I hope somebody will give some help! Thanks...Ellitsas!

---

### Post by tuxxy on 2008-11-05
Did you activate the recommended video driver first at **system > admin > hardware drivers**

---

### Post by ellitsas on 2008-11-05
yes i did activate it, though after a long time of installing and reinstalling stuff, it only came up once on the list!

---

### Post by magnus0 on 2008-11-05
Install the compiz settings manager (in synaptic) and from there enable the cube.  Now press alt + F2 and run ```
compiz --replace
```

Now compiz has custom settings and everytime you start your computer it starts with theses settings. You can change effects in Compiz settings manager

---

### Post by Kevbert on 2008-11-05
If you have problems running it (and it fails) you may need to run [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") as it may help in resolving any driver issues.

---

### Post by ellitsas on 2008-11-05
so this is what comes out after a checkup! 

Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card.

---

### Post by Kevbert on 2008-11-05
You may need to enable backports under software source updates. Then do an update and see if you get the driver to appear under System-Administration-Hardware drivers. If you get some drivers to appear there you'll need to enable them and a file should download (it may take a while). You'll then need to reboot your PC.

---

### Post by ellitsas on 2008-11-05
now nvidia appears in my drivers and it's enabled but still compiz doesn't really work!

---

### Post by ellitsas on 2008-11-05
hey everything works now...thanks a lot! sometimes things r so much easier than the seem! thanks again!

---

### Post by Kevbert on 2008-11-05
That's good. Please mark your thread as solved by going to Thread Tools at the top of your first post and select Mark as solved. Thanks.

---

