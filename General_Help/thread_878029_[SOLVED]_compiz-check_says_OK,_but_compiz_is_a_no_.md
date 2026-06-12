---
title: "[SOLVED] compiz-check says OK, but compiz is a no go?"
date: 2008-08-02
forum: General Help
---

### Post by sir_blargh on 2008-08-02
**** [COLOR="Red"]EDIT:  SOLVED[/COLOR] ****

Found out that I needed to execute this command:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

Now compiz works just fine!


**** [COLOR="Red"]END EDIT[/COLOR] ******

Hi All,

On one machine running Hardy and Gnome with the latest compiz drivers installed (from the ppa.launchpad.net repository) I'm having some trouble getting compiz to run.  I've downloaded the compiz-check script ([http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)) and it gives my system the green light.

```

514 -> ./compiz-check 

Gathering information about your system...

 Distribution:          **Ubuntu 8.04**
 Desktop environment:   **GNOME**
 Graphics chip:         **nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)**
 Driver in use:         **nvidia**
 Rendering method:      **Nvidia**

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for non power of two support...          [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for composite extension...               [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for FBConfig...                          [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for hardware/setup problems...           [ [COLOR="Lime"]OK[/COLOR] ]

```


However, here is the output when I launch compiz:

```

501 -> compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0185 (rev c1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1208x675) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

```

When I do that, the screen goes blank and I must hit ctrl+c and then "metacity --replace &" for things to get back to normal.  Naturally I've checked the initiate_edge value that GConf backend complains about, but it is an empty string and matches exactly the configuration of another machine I have which successfully runs compiz.

Any ideas?

Thanks!

---

### Post by Vadi on 2008-08-02
Thread tools - 'Mark Thread as Solved', thanks :)

---

