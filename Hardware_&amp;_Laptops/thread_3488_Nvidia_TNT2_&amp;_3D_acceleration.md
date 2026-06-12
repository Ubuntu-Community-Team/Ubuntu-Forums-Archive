---
title: "Nvidia TNT2 &amp; 3D acceleration"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by jodef on 2004-11-06
How exactly do I get 3D aceleration working for my nvidia card; I installed nvidia-glx drivers what's next?

---

### Post by FLeiXiuS on 2004-11-06
[QUOTE=jodef]How exactly do I get 3D aceleration working for my nvidia card; I installed nvidia-glx drivers what's next?[/QUOTE]

It should automatically be set to 3d Accerleration.

---

### Post by jodef on 2004-11-06
[QUOTE=FLeiXiuS]It should automatically be set to 3d Accerleration.[/QUOTE]

Installed criticalmass which requires 3D acceleration on installing nvidia-glx drivers I now get the following error:
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
*ERROR*: Video Mode: failed #Couldn't find matching GLX visual
``` 

What am I missing?

---

### Post by FLeiXiuS on 2004-11-09
[QUOTE=jodef]Installed criticalmass which requires 3D acceleration on installing nvidia-glx drivers I now get the following error:
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
*ERROR*: Video Mode: failed #Couldn't find matching GLX visual
``` 

What am I missing?[/QUOTE]

Nvidia just updated their linux drivers.  I recommend:
```
sudo apt-get update
sudo apt-get install --reinstall -y -f nvidia-glx
sudo nvidia-glx-config enable

```

Give that a shot.  If you don't feel like upgrading...
```
sudo nvidia-glx-config enable
```
that should fix the problem.

---

### Post by wallijonn on 2004-11-09
SPM -> libglc?

---

### Post by FLeiXiuS on 2004-11-11
[QUOTE=wallijonn]SPM -> libglc?[/QUOTE]

```
sudo apt-get install libgcc
```

That should fix it the dependency problem.

---

