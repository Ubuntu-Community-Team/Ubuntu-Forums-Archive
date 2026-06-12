---
title: "how much memory graphics and RAM does compiz need for desktop cube?"
date: 2008-08-13
forum: General Help
---

### Post by Quarg on 2008-08-13
does anyone know how much RAM and graphics memory you need to have the desktop cube? will it work at all in VirtualBox?

---

### Post by tuxxy on 2008-08-13
It doesnt take much, my system boots up using around 300MB RAM and this is with all effects enabled, 

I can increase with it rain/fire plugins etc but only like a couple of MB for each plugin.

---

### Post by Lexrst on 2008-08-13
AFAIK, the VirtualBox video driver does not have any support for hardware or 3d acceleration.  As a result you cannot enable Advanced Desktop Effects / Compiz in a VM.

Cheers,

Lexrst

---

### Post by mb_webguy on 2008-08-13
VirtualBox issues aside (which I don't know anything about), my System monitor is showing that the compiz processes are taking up about 40MB of memory, and I have Desktop Cube with a skydome, Rotate Cube, Animations, Window Decoration (with Emerald), Wobbly Windows, and Cube Caps enabled.  Emerald uses 10MB of that 40MB.

---

### Post by sdennie on 2008-08-13
> **Quarg said:**
> will it work at all in VirtualBox?

I don't think any VM solutions have reasonable 3D acceleration.  It's generally not something businesses need and, in some cases, may be impossible because the underlying driver is closed source.

---

### Post by KWM987 on 2008-08-13
Generally the more RAM the better, but as long as you have discrete graphics and somewhere around a GB of RAM I would expect everything to run flawlessly.  As has been said I would not expect seamless performance in VM, it's not designed with that type of action in mind.

---

### Post by tuxxy on 2008-08-13
Yes same here 46MB RAM and I have nearly everything enabled :lolflag:

---

