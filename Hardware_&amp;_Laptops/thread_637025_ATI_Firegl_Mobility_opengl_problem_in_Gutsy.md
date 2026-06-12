---
title: "ATI Firegl Mobility opengl problem in Gutsy"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by inf4my on 2007-12-10
Ok I have an ATI firegl mobility in my Lenovo T60p im running gutsy gibbon. I have compizfusion running but I cant seem to get games to work specifically steam games(when I load Team-fortress 2 I hear the opening valve music and then the screen goes black and after about 10 secs im back on my desktop with 640x480 resolution). Wine will not recognize the opengl on the card. Does anyone have any ideas.

---

### Post by bmwman91 on 2007-12-10
Which drivers do you have installed?  Being a FireGL card, are you running XGL, fglrx, the stock Mesa drivers/didn't install anything special, or did you hack some of the newer ones with AIGLX support?

As a forewarning, XGL kinda sucks/can be buggy, and I am assuming you are either using it or the stock mesa drivers since you have Compiz running.

---

### Post by inf4my on 2007-12-10
I think i have fglrx. if i type fglrxinfo i get this
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5250
OpenGL version string: 2.0.6473 (8.37.6)

---

### Post by inf4my on 2007-12-10
here is the end of the output when i run steam and try to install coiunter-strike and it closes.

```
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !
err:wgl:X11DRV_ChoosePixelFormat No libGL on this box - disabling OpenGL support !
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
Shutting down. . .

```

---

### Post by martinje on 2007-12-13
Have you tried Envy and have it installed the lastest ATi drivers for you?

---

### Post by darpan on 2007-12-17
Hi,

Did you get the desktop effects working with your configuration? I just can't get them working on my T60p with ATI mobility V5250
When I run fglrxinfo i get:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5250
OpenGL version string: 2.0.6473 (8.37.6)

Whenever I try to enable the desktop effects, I get an error saying that the desktop effects could not be enabled.

I have enabled the restricted driver also.

Thanks.
-darpan

---

### Post by jonzy350 on 2007-12-20
I have a T60p with Gutsy, same config.  To get the Compiz and Desktop effects to fully work, I had to install XGL-Server, setup a session that used it, and everything seems to work fine (except suspend, sleep, and occasional freek out of the desktop when I load VMware or other mem/cpu intensive apps)

---

### Post by tristan@Ubuntu on 2007-12-20
I would much appreciate if you, inf4my and/or jonzy350, could paste your xorg.conf and any other relevant file... We have the same laptop but it does not work for me.

Thanks!

---

### Post by olmari on 2007-12-23
Indeed here seems to be some problem with Wine and opengl in gutsy... I have IBM t42p with ati firegl t2 and basically any wine program whines about libGL not found..

---

