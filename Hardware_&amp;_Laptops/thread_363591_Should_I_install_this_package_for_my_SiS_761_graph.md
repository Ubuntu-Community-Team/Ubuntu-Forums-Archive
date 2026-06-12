---
title: "Should I install this package for my SiS 761 graphics chip?"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by jordi_rc on 2007-02-17
Hello

I have a barebone with Xubuntu Linux installed. Runs fine. It is XCCube EX761 and has a SiS 761 graphics chip.
I know that SiS chips have not 3d acceleration support for 3d. When I use the glxinfo command I see that "direct Rendering: no" message. 

But I need 3d acceleration for some programs, not games. For Xj3d: X3D and VRML Java browser.

But as my computer runs very fast with Xubuntu (faster than Windows XP), I wonder if this is possible this solution: to install a driver that provides 3d acceleration via software rendering.

I looked at packages for this at Synaptic.
I saw I have opengl, and mesa, and SiS drivers installed, but they don't give 3d acceleration.
I saw a package named:

> 
libgl1-mesa-swrast


The description says this:

> 
This library provides a pure software rasteriser; it does not provide
a direct rendering-capable library, or one which uses GLX.  For that,
please see libgl1-mesa.

On Linux, this library is also known as libGL or libGL.so.1.


I wonder if I can install this and get programs that require 3d acceleration work, even if they go to a slow framerate.

Would it be dangerous to my system to install this?
Will this fix the problem?
May this be incompatible with my other graphics drivers?

Thanks for any advice or info.

Jordi R. Cardona.

---

