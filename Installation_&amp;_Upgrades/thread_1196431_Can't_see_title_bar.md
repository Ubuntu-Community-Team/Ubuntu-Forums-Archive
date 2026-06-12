---
title: "Can't see title bar"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by mthalis on 2009-06-24
After enabling desktop effect. I can't see title bar in any window(Firefox, terminal,etc..).If i remove effect then i can see title bar. please help me i want enable desktop effect how can i fix it.

 My monitor is 17, Graphic card 7300GT,1gb ram, Ubuntu 9.04.

---

### Post by mthalis on 2009-06-25
Please help me.

---

### Post by ad_267 on 2009-06-25
Do you have the compiz settings manager installed? If not you can install the compizconfig-settings-manager package. Then open the settings manager and make sure the window decorator plugin is enabled and the command is set to "gtk-window-decorator --replace".

For a temporary fix you can press Alt+F2 and run "gtk-window-decorator --replace".

---

### Post by Divider on 2009-06-25
you can also switch out of compiz until you can debug your issue further using...

[PHP]sudo metacity --replace gdm[/PHP]

---

### Post by ad_267 on 2009-06-25
> **Divider said:**
> [PHP]sudo metacity --replace gdm[/PHP]

Shouldn't that just be "metacity --replace"?. Using sudo to run the window manager as root is a really bad idea, and I don't think the gdm part would do anything except maybe return an error. Anyways, they've already done this by disabling visual effects.

---

### Post by mthalis on 2009-06-25
yes I already installed compiz settings manage. If I enabling visual effect to normal or extra this happen if i select none show all windows titles bars.

---

### Post by ad_267 on 2009-06-25
> **mthalis said:**
> yes I already installed compiz settings manage. If I enabling visual effect to normal or extra this happen if i select none show all windows titles bars.

Did you check that the window decoration plugin is enabled? And did you try running "gtk-window-decorator --replace"?

If that command doesn't do anything then open a terminal from Applications - Accessories - Terminal and run "gtk-window-decorator --replace &" and see what output you get.

---

