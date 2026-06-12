---
title: "Compiz is laggy on 2.0 ghz cpu and 128 mb nvidia card"
date: 2008-08-21
forum: General Help
---

### Post by James M on 2008-08-21
I recently bought a Dell Vostro with a 2.0 ghz Celeron processor and a 128 mb nvidia graphics card. I notice that compiz lags when doing something as simple as minimizing a window which is odd seeing as how I can use the Rain Effect. I think its my processor though. It is a single core only... would compiz effects speed up if I install a 2.0 ghz dual core intel processor?

---

### Post by James M on 2008-08-21
Well I enabled loose binding and indirect binding and it helped...but still a little laggy when using GTK-recordmydesktop. I make youtube videos :P

---

### Post by James M on 2008-08-22
Well I guess no one has any answers so I'll make a conclusion myself.

Compiz Fusion will run on about a 80% smoothness rate when using a single core processor. 

------The Perfect Compiz Set Up Minimum------ (Smooth Performance)
2 gb of ram
dual core 1.4 ghz cpu
nvidia with 128 mb on the card ( or an ATI with 128 )

------The Perfect Compiz Set Up Maximum------  (Extreme Performance)
4 gb of ram
quad core 2.5 ghz cpu
nvidia with 1 gb on the card

---

### Post by inigomontoya on 2008-08-22
Those system requirements seem quite a bit overkill.  I've had compiz working smooth on a Pentium 3 and a first generation Radeon Mobile with 16mb of memory.  What type of nvidia video adapter are you using?  What drivers?

---

### Post by armageddon08 on 2008-08-22
> **James M said:**
> Well I enabled loose binding and indirect binding and it helped...but still a little laggy when using GTK-recordmydesktop. I make youtube videos :P

CF always lags a bit while using gtk-recordmydesktop.

> **inigomontoya said:**
> Those system requirements seem quite a bit overkill.  I've had compiz working smooth on a Pentium 3 and a first generation Radeon Mobile with 16mb of memory.  What type of nvidia video adapter are you using?  What drivers?

yeah......I also think it must be video drivers.

---

### Post by xeth_delta on 2008-08-22
Can you please post the output for
```
glxinfo | grep -i rendering
glxinfo | grep -i opengl
```

---

### Post by James M on 2008-09-01
> **xeth_delta said:**
> Can you please post the output for
```
glxinfo | grep -i rendering
glxinfo | grep -i opengl
```

james@Dell-Vostro:~$ glxinfo | grep -i rendering
direct rendering: Yes
james@Dell-Vostro:~$ glxinfo | grep -i opengl
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400M GS/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
james@Dell-Vostro:~$

---

