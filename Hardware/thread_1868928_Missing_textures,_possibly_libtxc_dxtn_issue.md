---
title: "Missing textures, possibly libtxc_dxtn issue"
date: 2011-10-24
forum: Hardware
---

### Post by Kisbey on 2011-10-24
Having some issues with Eve Online (via Wine); Running 11.10 64-bit on a Radeon HD6000-series card, with the default Gallium drivers, the game loads and runs but there are no textures applied to rendered objects (black objects).

The problem doesn't exist with the blob drivers on the same pc/install, only when running the mesa/gallium drivers.  This suggests it's not a Wine issue and is rather a fault with the graphics drivers that Wine is using.

Further research indicates that this may in fact be a problem with 32-bit support in the drivers, possibly related to libtxc_dxtn (see xorg-edgers).

Anyone have or know of an easy method to validate whether this is the case?  I'm at the edge of my technical depth here.

Thread not posted in the Wine subforum due to probability the issue is not specific to Wine.

---

### Post by Perfect Storm on 2011-10-25
Moved to Hardware.

---

### Post by Kisbey on 2011-10-25
> **Kisbey said:**
> no textures applied to rendered objects (black objects)
 
Solved. 
 
Apparently s3tc is not enabled by default in the mesa drivers. You need to add "force_s3tc_enable=true" to force the environment to support the compressed s3 textures before running the game. So, for example, in my case I'd type "force_s3tc_enable=true wine eve.exe" This forces the mesa drivers to load the copyright-protected s3tc lib support and render textures properly.

---

