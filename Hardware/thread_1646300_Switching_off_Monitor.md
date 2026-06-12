---
title: "Switching off Monitor"
date: 2010-12-15
forum: Hardware
---

### Post by cropr on 2010-12-15
I have a laptop with a broken screen. I currently us it as a fixed PC with an external monitor.  This works fine but I cannot get Ubuntu (or any other linux) to configure this correctly.

Apparently I cannot tell xorg.conf that it should not use the internal screen of the laptop.  As a consequence it selects the highest common resolution of the internal and external monitor when launching X.  Once logged in, I can manually switch off the internal monitor and select the best resolution of the external monitor, however these changes are not reflected in the xorg.conf file.

Is there a way to disable my internal monitor when X starts and to immediately select the right resolution of the external screen.  I have an intel graphic card.

Just for the information: I can get this done in Windows very easily

---

