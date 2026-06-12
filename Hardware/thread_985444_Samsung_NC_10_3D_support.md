---
title: "Samsung NC 10 3D support"
date: 2008-11-17
forum: Hardware
---

### Post by Simaryp on 2008-11-17
Ive got a Samsung NC10 and got a Problem with the Graphiccard.
I have no 3d Support so Programs like Googleearth dont work.
The graphicchip is a intel 945 and im using Ubuntu 8.10.
Excuse me for my bad english.

---

### Post by Jon Bradbury on 2008-11-18
Try running glxgears first. With no resizing you should get around 600fps. If it is flickering, it is because you have the compiz-fusion desktop effects on, and you should turn them off for best 3d performance.

---

### Post by Simaryp on 2008-11-18
Ah thx now it works. Even the command glxinfo | grep rendering  tells me now that 3d rendering is running. But i think i will try the .04 Version because ive got some more Problems for example with the Sound.

---

