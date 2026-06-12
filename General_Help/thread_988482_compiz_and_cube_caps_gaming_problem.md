---
title: "compiz and cube caps gaming problem"
date: 2008-11-20
forum: General Help
---

### Post by ontherooftop on 2008-11-20
ok I have the sphere plugin with the cube cap pics, but everytime 
I play a game the cube caps all the sudden disappear and are white, 
any help. Thanks.

---

### Post by klange on 2008-11-20
> **ontherooftop said:**
> ok I have the sphere plugin with the cube cap pics, but everytime 
I play a game the cube caps all the sudden disappear and are white, 
any help. Thanks.
Sounds like an OpenGL buffer loss that's killing off the memory used to store the texture for the cube caps. (Read: Driver problem)

I know this happens for a number of different situations on Intel in Intrepid, with quite a few different textures (stored icons, thumbnail backgrounds, skyboxes, etc.)

---

