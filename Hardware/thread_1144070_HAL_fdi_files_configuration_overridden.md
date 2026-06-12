---
title: "HAL fdi files configuration overridden"
date: 2009-04-30
forum: Hardware
---

### Post by bhagwad on 2009-04-30
I have some settings for my touchpad stored in fdi files. They're set up correctly. I have no doubt about that. I'm using Ubuntu 9.0.4 32 bit.

However, some settings (eg: MaxTapTime) are (I think) being overridded by the inbuilt GUI mouse application at startup - even though there is no option to change the parameter in the GUI.

I know it's the GUI that's interfering, because when I enable a parameter like HorizEdgeScroll in HAL, and I *don't* enable it in the GUI, it always resets at startup to the GUI value.

I need my MaxTapTime = 300 and the FDI file reflects that. But it's always getting set to 180 instead. So is there anyway I can politely ask the GUI not to interfere with my manual settings?

As a workaround, I'm currently using synclient as a startup program to automatically change the value each time. Does anyone know of a cleaner way?

---

