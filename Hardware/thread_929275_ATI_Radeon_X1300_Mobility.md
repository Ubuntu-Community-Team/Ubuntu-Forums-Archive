---
title: "ATI Radeon X1300 Mobility"
date: 2008-09-24
forum: Hardware
---

### Post by jlimon on 2008-09-24
I heard rumor that the open source ATI driver included with Ubuntu now supports the Radeon Mobility X1300, and will be included with Intrepid. Is this true?

If so, that's awesome. I've been wanting to keep Ubuntu on my Dell laptop for a while now, but the lack of 3D support is the clincher.

---

### Post by Pulse214 on 2008-11-15
I've been lead to beleive the same thing, Have you upgraded to find out yet? i'm about to take the plunge and go to 8.10 but i'd like to find out if the open source has 3d accelration first.  If i can get 3d support plus hibernate then it's bye bye windows for good.

---

### Post by checkit on 2009-01-09
I just tested my new ATI x1300 card using a Hardy LiveCD and an Intrepid LiveCD.  The Hardy CD cannot use direct rendering (boots with an error in /var/log/Xorg.0.log), and gets ~200 FPS in glxgears.  The Intrepid CD sets up direct rendering correctly on boot, and gets ~1500 FPS in glxgears.

So it looks like something has changed with the ATI open source driver between Hardy and Intrepid.

---

