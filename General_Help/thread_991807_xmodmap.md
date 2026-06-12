---
title: "xmodmap"
date: 2008-11-24
forum: General Help
---

### Post by Ofloo on 2008-11-24
What I have noticed is that after upgrading to the latest ubuntu my shortcuts don't work properly anymore for example I defined keycode 170 to F13, then I created a custom bind using gconf-editor, but those key bindings do not work anymore anyone know why that is.

---

### Post by Favux on 2008-11-26
Me too.  I'm looking into it, no luck so far.  Hope I'll get lucky or someone helps us out.

---

### Post by Favux on 2008-11-27
Alright Ofloo,

Looks like I solved it, at least for me.  I hope this works for you.  Basically with Intrepid Ubuntu is shifting to the HAL model of device input, which eventually will be a significant advance giving us hot plugging etc.  Unfortunately in the meantime it breaks a lot of stuff.  Including single key key bindings.

So I did what I did on other stuff Intrepid broke.  I went into my xorg.conf and uncommented out the keyboard section that Intrepid commented out on install.  Reboot.  Presto my key bindings reappeared!  I knew the keycodes were there through xev, which also showed the .Xmodmap was binding.  So why the failure in Compiz?  Oh, sure, HAL.

Eventually there are suppose to be more modern ways to handle this.  Some people are reporting that by going to the System>Preferences>Keyboard and selecting in Generic Ev-dev Managed Keyboard they got things working.  But it didn't work for me.  This would have been a more "proper" way to handle this rather regressing to xorg.conf.  But if it works it works.

Let me know if it works.

---

