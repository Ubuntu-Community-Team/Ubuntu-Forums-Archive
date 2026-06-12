---
title: "problem with ATI radeon xpress 200m with open drivers"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by 0p3nSou?c3 on 2007-03-12
Im relatively new to ubuntu, right now i have edgy installed with beryl and everything was working with the ati propietary drivers. Only problem was beryl was a little unstable and sometimes crashed. I looked around and some say that setting up xorg with the radeon drivers would make beryl stable, but unfortunately my ATI radeon xpress 200M is not supported. Is there any way to setup xorg with the radeon driver and AIGLX?

---

### Post by hizaguchi on 2007-03-12
The 200m isn't supported by the open source driver.  You can get basic 2D functionality, but no acceleration and no OpenGL, so no Beryl without fglrx.  Problem is that fglrx doesn't support some of the OpenGL extensions needed for AIGLX, so you're stuck with XGL until ATI gets around to fixing the driver.  I've been waiting on that for about a year.

Does XGL crash during any specific activity for you?  It's not the Shift+Backspace "feature" is it?

---

### Post by 0p3nSou?c3 on 2007-03-12
I just as figured that was the case, but it didn't hurt to ask. Beryl crashes when i try to unmaximize a window, i just have to avoid doing that, but just thinking about that bug existing makes me uncomfortable :( , also video is very choppy when i try to view it fullscreen, what could be causing that problem?

---

