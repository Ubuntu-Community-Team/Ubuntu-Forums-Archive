---
title: "IS hibernate/sleep on lid close connected to unity?"
date: 2012-04-03
forum: Hardware
---

### Post by xmorg on 2012-04-03
That's my question.  When im in unity and i close the lid, the laptop goes to sleep.  However, when I am in pekwm and I close the lid, the laptop stays on.

I am not really familiar with how linux handles sleeping and hibernation on lid close, is there some way to have non-unity window managers hibernate on lid close?

---

### Post by urukrama on 2012-05-21
> **xmorg said:**
> That's my question.  When im in unity and i close the lid, the laptop goes to sleep.  However, when I am in pekwm and I close the lid, the laptop stays on.

I am not really familiar with how linux handles sleeping and hibernation on lid close, is there some way to have non-unity window managers hibernate on lid close?

I'm not sure what Unity uses (as I don't use it myself), but you could do like I do, and use xfce4-power-manager in pekwm. Add it to your start file (as *xfce4-power-manager &*. You can change the settings by running xfce4-power-manager-settings. You can configure it to hibernate or sleep when you close the lid.

---

