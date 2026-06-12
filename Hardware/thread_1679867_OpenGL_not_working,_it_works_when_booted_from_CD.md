---
title: "OpenGL not working, it works when booted from CD"
date: 2011-02-01
forum: Hardware
---

### Post by HavierPB on 2011-02-01
Hello. I have recently installed Kubuntu 10.10 and I run into an odd problem.

When I boot from the Kubuntu CD, glxgears functions well, OpenGL composition also works.
When I boot the freshly installed Kubuntu, glxgears draws 1 frame, then it stop. When I resize the window it gets black. When OpenGL composition is enabled, then the same thing happens after logging in: the screen freezes, but after a while I can hear the login sound.

I have tried to install Xfce. There it is the same.
I have tried to reinstall twice.

Graphics: ATI X1270  (RS690M)
Proc.: AMD Turion 64 X2

What do you think, what might be the problem?

---

### Post by HavierPB on 2011-02-08
I fount out the following, when I insall the Broadcom STA wireless driver via Additional drivers, glxgears and all OpenGL apps stops working. When I remove the driver they do work again.

---

