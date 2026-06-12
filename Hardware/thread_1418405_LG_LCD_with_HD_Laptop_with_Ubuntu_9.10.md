---
title: "LG LCD with HD Laptop with Ubuntu 9.10"
date: 2010-02-28
forum: Hardware
---

### Post by jjacobus on 2010-02-28
Hi,

I am using Ubuntu 9.10 on my HP DV2000 laptop, and also have an LG 21.5 external LCD and have created an extended desktop scenerio. When I full screen a streaming news site on the left hand side on the LG screen it looks great, but if I move the mouse back to my notebook to view another application, the full screen news stream on the left on the LCD is no longer full screen, it goes to a small playback size in my chrome web browser. This only happens when I move the mouse back to the notebook screen.

Any ideas ?

Thanks,

 - JJACOBUS

---

### Post by jshein on 2010-03-02
Flash full screen mode always releases focus when an alternate application or desktop gains the focus.

Flash will:

- Always close when it loses focus
- Always close full screen when ESC is pressed
- Always show the ESC key notice when entering full screen
- The user needs to initialize - full screen pop-ups will not work

Jason

---

