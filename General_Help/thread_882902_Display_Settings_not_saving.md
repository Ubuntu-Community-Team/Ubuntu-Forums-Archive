---
title: "Display Settings not saving"
date: 2008-08-07
forum: General Help
---

### Post by lsutiger on 2008-08-07
I can not access the display settings as normal (System-->Preferences-->Screen Resolution). When I do I get the following:```
The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
```

I have googled that quite a bit and searched here for an answer to no avail.

I have found a temporary work around.```
 sudo displayconfig-gtk

```

The only problem with that is that when I restart X or the computer, the Htz for the refresh rate does not save.

Any ideas?

---

### Post by lsutiger on 2008-08-08
Anybody?

---

### Post by lsutiger on 2008-09-11
Ok it hit me again. Everytime I have to shutdown (monodevelop crashed the system), my display settings are not correct. 
Now I don't even have the correct ones to choose. I have edited the xorg.config file, but it still does not show up.

Any ideas?

---

### Post by lsutiger on 2008-09-11
OK - here is what I have done in order to get it back:
Uninstalled the Nvidia driver, reboot, installed Nvidia driver, reboot, ran  displayconfig-gtk, selected widescreen monitor, logged out, logged back in, ran  displayconfig-gtk again and the options were listed.

---

### Post by lsutiger on 2008-09-15
I would really like to know how to stop this form happening. Any ideas?

---

### Post by lsutiger on 2008-10-07
Bump...
Every reboot, restart, I have to set the Htz for the refresh rate back to the correct setting. Why wouldn't this be saving?

---

