---
title: "AMD-PRO 16.30 driver is only working with UNITY not with GNOME"
date: 2016-08-25
forum: Hardware
---

### Post by tak21 on 2016-08-25
Dear all,

I installed the AMD-PRO 16.30 driver for my new RX 480 on my ubuntu 16.04 workstation. It did not seem to work (black screen, only mouse cursor visible). Then I realized, that when I use UNITY insead of GNOME 3.18 it actually does work. Is anyone able to tell me what I can do to use my RX 480 with GNOME?

Thanks in advance,
tak21

---

### Post by QIII on 2016-08-25
Just for clarity, I assume you mean the AMDGPU-PRO driver?

I dual boot Ubuntu and Kubuntu and it works on both of those.

If I have time, I'll install Ubuntu Gnome and see what I come up with.

---

### Post by tak21 on 2016-08-25
Hi QIII, yes thanks for the clarification I mean AMDGPU-PRO. And just to mention it I also installed GNOME desktop in a stabdard UBUNTU installation (so UNITY + GNOME) and with UNITY it works well, with GNOME I have the same result as with UBUNTU-GNOME.

---

### Post by Yellow Pasque on 2016-08-26
```
glxinfo | grep string
```

---

### Post by tak21 on 2016-08-28
o.k. I found the fix for my issue: recompile "libcogl.so.20.4.1" with a patch as described in "http://askubuntu.com/questions/794529/amdgpu-pro-install-on-ubuntu-gnome-16-04-with-r9-285".

---

