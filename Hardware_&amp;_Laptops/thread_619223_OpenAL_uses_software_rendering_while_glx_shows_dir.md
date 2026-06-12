---
title: "OpenAL uses software rendering while glx shows direct rendering is OK"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by gdzsi on 2007-11-21
I have an HP nx6310 laptop, which has an i945 intel graphics chip in it.

The problem is that I noticed every 3d app runs really slow on it.

I couldn't make the FPS rate go higher than 20 in torcs (when there are other cars around, it is tipically ~10fps which is not playable) even with the worst graphics settings.

Then I noticed in the console output:
OpenAL backend info:
  Vendor: OpenAL Community
  Renderer: Software
  Version: 1.1
  Available sources: 1024 or more
  Available buffers: 1024 or more
  Dynamic Sources: requested: 1003, created: 1003
  #static sources: 21
  #dyn sources   : 1003

(see the line Renderer: Software)

If it uses software rendering, then that's why it is so slow.
But how do I make it use Hardware T&L?

glxinfo |grep rendering shows
direct rendering : yes
glxgears runs with ~1000 fps.

I would really approciate if anyone could help me out.

G

---

### Post by spoilerhead on 2007-11-21
openAL is sound ;)

don't confuse it with openGL

---

### Post by gdzsi on 2007-11-21
coool :)

Then i don't know why torcs listed it under visual properties :D

Then i don't know why the heck it is so slow...

---

