---
title: "Video Flicker"
date: 2008-05-01
forum: Hardware
---

### Post by Icemanyurt on 2008-05-01
I am using a Dell Inspiron 1521 and whenever I use anything with OpenGL I am getting a flicker to black on the screen.

In some applications, it is bearable, but it has rendered things like blender unusable.

I am using the hardware device driver for an ATI card, any help would be great

---

### Post by rabideau on 2008-05-02
Hi iceman...

You might try reading the following.  It could fix the problem.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153204](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153204)

---

### Post by Cygoku on 2008-05-02
What rabideau link you to is useless in your case.  ATI has problem with OpenGL.  Try disabling Compiz before running your OpenGL application.  This cannot not be fixed until DRI2 and the support for DRI2 from ATI.  

Don't hold your breath.  

Cygoku

---

