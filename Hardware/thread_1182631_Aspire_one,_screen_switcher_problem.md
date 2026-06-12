---
title: "Aspire one, screen switcher problem"
date: 2009-06-09
forum: Hardware
---

### Post by GrootBrak on 2009-06-09
On my netbook switching between classic and Netbook screen modes works perfectly. I prefer to work in the "Classic mode." However after a system restart, it boots with the classic screen, but then the screen does not fit. I can't see any taskbars and added a desktop launcher to the "desktop switcher". Then I switch to "Remix mode" and back to "Classic." How can I make the Classic to boot up fitting the screen? Resolution is set to 1024 x 600.

---

### Post by asmoore82 on 2009-06-13
I'm on a full size laptop here - I added netbook stuff and "desktop-switcher"
earlier this week and just rebooted for the first time...

it pretty much b0rked my desktop - I uninstalled and purged and tried to log in again -
gnome session still broken -
this is I had to do to fix it:
```
gconftool-2 --recursive-unset /desktop/gnome/session
```

I believe that the key the "desktop-switcher" fails to set properly is this:
```
**$** gconftool-2 --get /desktop/gnome/session/required_components_list
[filemanager,panel,windowmanager]
```

---

### Post by GrootBrak on 2009-06-17
The netbook has been passed on. I will point the new owner to your post. Hopefully it will sort it out then.

Regards

---

