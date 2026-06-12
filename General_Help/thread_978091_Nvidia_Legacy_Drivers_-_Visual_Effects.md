---
title: "Nvidia Legacy Drivers - Visual Effects"
date: 2008-11-10
forum: General Help
---

### Post by migsvill on 2008-11-10
Hi,

I recently installed Ubuntu 8.10 and am loving it. However, I'm having problems with the nvidia driver. I'm using a gforce2 mx 400 and installed the nvidia 96 driver. Whenever I set the visual effect to the maximum setting, the bottom panel disappears as well as the title bar and the control buttons of the windows and applications. I read somewhere that the nvidia-legacy drivers don't work with the x.org in intrepid. Is there any fix to this? Is this also the same with Ubuntu 8.04?

Note: The weird thing is, I can play defense of the ancients through wine. However, I still want to maximize the visual effects intrepid has to offer.

Thanks!

---

### Post by gregphil on 2008-11-10
I had a similar problem with Ti4600 and Ubuntu 8.10 (no restricted driver available, no fancy graphics)

I just gave up and bought a new $49 video card (GeForce 6200) and the problem is totally solved.  Apparentlly the new video drivers required no longer support "old" video cards like the MX400, and 8.10 won't use the old drivers.

---

### Post by migsvill on 2008-11-10
Thanks for the reply. Is this also a problem in 8.04? I'm planning to switch to it if it isn't.

---

### Post by gregphil on 2008-11-11
Not that I know of, the older nvidia Ti4600 video card worked just fine under 8.04.1 and I could use the "restricted" nvidia driver for that distribution.  (but no driver under 8.10 )

---

### Post by lemming465 on 2008-11-22
We're discussing this on launchpad as bug [297836]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836").  The best workaround so far is to disable Compiz effects using System -> Preferences -> Appearance, Visual Effects = none.  It was not a problem in 7.10 or 8.04, but I'm sticking with 8.10 anyway.

---

