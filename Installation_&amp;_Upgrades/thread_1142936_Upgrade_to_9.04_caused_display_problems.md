---
title: "Upgrade to 9.04 caused display problems"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by SomethingFishy on 2009-04-29
Hi.  Upgraded to 9.04 this morning and now my display is all shifted horizontally to the left.  Please can anyone suggest how to fix it?

If it helps to have more info:
1. My monitor is "ASUS LCD MONITOR 22" WIDE MW221C DVI"
2. If I click System... Preferences... Display I get the message "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" and if I say Yes it takes me to a dialogue entitled NVidia X Server Settings.

Thanks :)

---

### Post by iconfat on 2009-05-01
I'm having the same problem.

Setting Dynamic Twinview to True in Xorg.conf opened up the X Server Display Confirmation settings in the Xserver Settings app.

However.  The Ubuntu display settings under preferences gives me the same error.

This occured after upgrading to 9.04 from 8.10.

---

### Post by abn91c on 2009-05-01
does the lcd have a reset button? my dell widescreen resets if i press the button next to the power button

---

