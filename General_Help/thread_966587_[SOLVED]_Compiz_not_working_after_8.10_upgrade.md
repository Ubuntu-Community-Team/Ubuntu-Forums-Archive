---
title: "[SOLVED] Compiz not working after 8.10 upgrade"
date: 2008-11-01
forum: General Help
---

### Post by walawa on 2008-11-01
I've just upgraded ubuntu to 8.10. But now compiz doesn't start on login and when I try to start it from terminal (compiz start) it prints an error and all the window borders disappear. After that happens, I can't close them or type anything in the terminal so I have to logout. 

Here's the error:```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'start'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

---

### Post by walawa on 2008-11-02
Problem solved. All I had to do was disable the screensaver plugin (which I guess doesn't work with 8.10) and everything works fine!

---

### Post by lolwhites on 2008-11-02
> **walawa said:**
> Problem solved. All I had to do was disable the screensaver plugin (which I guess doesn't work with 8.10) and everything works fine!

How do I do that? I'm having the same problem all of a sudden.

---

### Post by walawa on 2008-11-02
Do you use the CompizConfig settings manager? If you do, do you have any plugins that you compiled or are from the unsupported plugins package? If so, try disabling them.

---

### Post by lolwhites on 2008-11-02
No to both. How do I get into the Settings Manager? I can't find it anywhere in the menus; do I need to install something else, or is there a command I can type in?

---

### Post by Pumalite on 2008-11-02
Synaptic>Search>compiz>Install the compiz manager

---

