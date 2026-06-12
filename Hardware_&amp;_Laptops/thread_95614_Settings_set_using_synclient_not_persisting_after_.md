---
title: "Settings set using synclient not persisting after restart"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by ispiked on 2005-11-26
I have found that synclient can be used to set a lot of the settings that all the GUIs to control touchpad settings don't cover. The only problem is that when I set stuff it doesn't stay when I restart my PC.

Something to ponder:
```

aguthrie@lappy:/$ synclient -h
Hardware properties:
    No touchpad found
    Do you use a newer kernel than 2.4?
    Then browse the messages or boot.msg for the hardware info
aguthrie@lappy:/$

```
Now how I can change settings and have them apply when no touchpad is found is still a mystery to me. 

Oh yeah, synclient should still be able to control an ALPS Touchpad, right? ;)

---

### Post by 23meg on 2005-11-27
I get the same message with synclient and my ALPS touchpad, but in any case, AFAIK synclient is meant for adjusting parameters on the fly. You should prefer putting the parameters in your xorg.conf file if you want them to persist.

---

### Post by jojacob on 2007-04-27
a quick and easy work around i've been using is to add synclient with whatever settings you want to set as parameters to your window manager autostartup menu. your settings will take a second to take effect, but at least you won't have to set them every login. they won't be set for the login screen though. my touchpad has been really slow since i upgraded to edgy unless i use synclient to set AccelFactor to about 0.3. the gui settings won't let it go that high.

---

