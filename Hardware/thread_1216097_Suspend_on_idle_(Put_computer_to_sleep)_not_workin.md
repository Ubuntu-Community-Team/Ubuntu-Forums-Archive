---
title: "Suspend on idle (Put computer to sleep) not working; Jaunty"
date: 2009-07-17
forum: Hardware
---

### Post by nimajiman on 2009-07-17
Hi there,

I am running Ubuntu 9.04 on a Toshiba laptop and having trouble getting it to suspend when idle. 

In system -> preferences -> power management, under the 'battery power' tab I have set it to 'put computer to sleep when inactive for 11 minutes'. 

Now suspend/resume works fine if I close the lid, or when the battery power is critically low. However unless I suspend it manually when I walk away, it will continue running until the battery drains itself completely, rather than going to sleep after 11 minutes as specified.

Does anyone know why this might be or how to fix it?

---

### Post by utnubuuser on 2009-07-17
have you tried: Alt+F2 >> gconf-editor >> apps >> gnome-power-manager >> actions

---

### Post by nimajiman on 2009-07-22
Aha... excellent thanks for that.

Although does not make any sense to me why this option is hidden in configuration settings and not in a more obvious place (i.e. within the power management dialogue).

Anyway, it is working now. Thanks

---

