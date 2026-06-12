---
title: "Desktop Effects won't start"
date: 2008-11-11
forum: General Help
---

### Post by sdpiowa on 2008-11-11
I upgraded from Ubuntu 8.04 to 8.10 yesterday.  Ever since, I haven't been able to enable the Advanced or Normal Desktop effects.  It says, "Could not enable desktop effects."

I'm running off of integrated graphics on a Dell Dimension 2400.

---

### Post by eternalnewbee on 2008-11-11
Try to enable your graphic card from **Main Menu > System > Administration > Hardware Drivers**. Then it should be no problem to start compiz. If your graphic card is activated, press **ALT-F2** and enter ```
compiz --replace
```
That should start up compiz. Hope this helps.

---

### Post by sdpiowa on 2008-11-11
My graphics card doesn't appear in the "Hardware Drivers" page.  I think the computer is looking for a driver that I don't have.  The weird thing is that it worked before I upgraded.

---

