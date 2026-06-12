---
title: "Lenovo touchpad has failed, seems to be a configuration issue"
date: 2010-07-26
forum: Hardware
---

### Post by fivebells on 2010-07-26
I have a Lenovo T61 running Ubuntu 10.04.  The cursor is no longer responding to activity on the touchpad, and the buttons below the touchpad also have no effect.  However, touchpad activity results in output from /dev/psaux, which makes me think this is a misconfiguration issue.  Also, I can use the trackpoint (the red nipple in the center of the keyboard), and the buttons below the keyboard result in mouse button events.

The gpointing-device-settings application shows that the touchpad is on, and using that application to turn it off and then back on does not fix the problem.  Rebooting has not fixed the problem.  Is there anything else I should try?

I first noticed the issue when I switched to the sawfish window manager.  That shouldn't be relevant, but I switched the window manager in a rather unconventional way, with "killall metacity && sawfish" so it could have caused a problem(?)

---

### Post by P4man on 2010-07-26
Does the laptop have a FN+function key combination to enable/disable the touchpad? Have you tried that?

---

### Post by fivebells on 2010-07-26
> **P4man said:**
> Does the laptop have a FN+function key combination to enable/disable the touchpad? Have you tried that?

Thanks for the suggestion.  This [appears]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-62714") to be Fn+F8 on the T61.  The key combination results in a touchpad icon appearing briefly in the upper right hand corner of the screen, but no touchpad functionality, even after multiple attempts.

---

