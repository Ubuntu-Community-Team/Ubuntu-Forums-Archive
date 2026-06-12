---
title: "64-bit jaunty and missing ram"
date: 2009-04-24
forum: Hardware
---

### Post by linux_paul on 2009-04-24
I had read that I needed 64-bit Ubuntu to access all 4 gigs of RAM.  But the system monitor only shows 3.3 gigs. I am using the on-board video card and have allocated 512MB for it, is this the cause?

Thanks for your reply.

---

### Post by Barry Carroll on 2009-04-24
In short, yes.  Sometimes you'll also lose a bit of RAM here and there with memory mapped i/o depending on your devices.

Do you game or work with 3d media? If you mostly work with 2D with a bit of compiz you could back off on the shared memory as it is probably more useful to the system than to the gpu.

---

### Post by linux_paul on 2009-04-24
Barry, no gaming or 3D, just use it with my media center. I figured I'd set it high to avoid choppy video playback with HD content. Video playback was choppy with compiz enabled but is fine without. Does this seem normal for 512MB? 

The board has AMD 790GX chipset with ATI Radeon HD 3300 Graphics

---

### Post by Barry Carroll on 2009-04-25
I'm not as familiar with ATI hardware as I am with Nvidia hardware unfortunately.  Do you use the proprietary ATI driver?  I don't think 512MB is needed to playback HD content, 256MB should be fine really.

What application are you using to play the video also?  I know some apps have various options for video output and I usually use OpenGL when I play videos in VLC.

It might be worth googling for general advise about "choppy video compiz ati" as there seem to a a lot of people out there with the same issue as you and some threads have fixes.

---

