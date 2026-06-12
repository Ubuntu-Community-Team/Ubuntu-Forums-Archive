---
title: "graphics and openGL"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by rcshah on 2009-02-02
Hi:
I am slowly progressing...I appreciate the help.

I've an old Toshiba Satellite with NVIDIA graphics card. However I don't know the particular card.  I did receive a driver update suggesting I use the proprietary NVIDIA driver, however after doing that I no longer saw anything on bootup.  I reinstalled the OS.  

Though I'm okay without enhanced desktop, ultimately I need OpenGL functioning.  For the moment when I install an application requiring this, it tells me that it does not find the expected folders for OpenGL.  I understand this isn't a program - but I'm not quite clear on how to have this/activate OpenGL.  

Could anyone help me understand these (seemingly related) graphics issues?
Rahul

---

### Post by taurus on 2009-02-02
Run this command from a terminal to see exactly which graphic card you have.

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```
And I assume you installed the nvidia driver from System -> Administration -> Hardware Drivers?

---

### Post by rcshah on 2009-02-02
Output:
```
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)

```

I installed from the manager as you said (and I am starting to get the impression that this can cause problems?)

---

### Post by taurus on 2009-02-02
Which driver version (nvidia) did you install?

---

### Post by rcshah on 2009-02-03
I installed NVIDIA accelerated graphics driver (vers 96).  This caused my monitor to go blank and not knowing how to resolve this, I reinstalled Ubuntu--thus now I am back to the default Ubuntu driver off the LIVE CD.

---

### Post by rcshah on 2009-02-03
I have resolved the problem by using this post:
[http://ubuntuforums.org/showthread.php?t=880787]("http://ubuntuforums.org/showthread.php?t=880787")

Specifically for my card I needed to go in an modify xorg.conf as detailed in the above link (first post).

Thanks for your help!

---

