---
title: "Nvidia drivers not recognized..."
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by apocalypse2012 on 2007-11-02
I installed the latest Nvidia drivers for my Quadro FX 2000 board using Envy (Could not get the restricted driver system to work). Ubuntu does not recognize that I am using them. It will not let me use any desktop effects. Also, Compiz will not work. The Nvidia Settings panel shows everything it should, but Ubuntu still says that 'nvidia drivers must be installed to use 3D' when I try to enable desktop effects...

---

### Post by dabl on 2007-11-02
Do you see the Nvidia green and black splash screen immediately before the login screen?  If "YES", then you do have the Nvidia driver installed, but lack the glx and compositing features.  If "NO", then something went wrong with the Envy installer.

So, if it's a "YES", open a console and do this:

```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

This will overwrite xorg.conf with the glx and compositing options.  After you restart the X server you will be able to run the "advanced desktop effects".


If it's a "NO", then open the console window and do this:

```
sudo envy -t 
```

and run Envy in text mode.

HTH:)

---

