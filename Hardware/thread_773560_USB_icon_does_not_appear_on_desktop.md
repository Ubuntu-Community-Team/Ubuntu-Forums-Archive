---
title: "USB icon does not appear on desktop"
date: 2008-04-28
forum: Hardware
---

### Post by mmasroorali on 2008-04-28
Recently I upgraded to hardy and then suddenly my usb drive icon does not appear on the desktop. It gets mounted, and I can perform read/write from command line, but the icon is not displayed.

Thanks for any suggestion.

---

### Post by breem42 on 2008-04-29
This is a problem for me too.  Using Kubuntu Hardy Heron, but Ubuntu desktop packages also installed.  USB device is vfat Sansa View (though I doubt that matters).  Used to work fine under 7.10.:confused: Will try restarting using Gnome.

Tony

---

### Post by ad_267 on 2008-04-29
```
gconf-editor
```

Then apps - nautilus - desktop and make sure volumes_visible is checked.

---

### Post by mmasroorali on 2008-04-29
Thanks, it works like a charm.

Why is not it made a default. Any user will want the usb drive display as soon as it is inserted, IMHO.

---

### Post by breem42 on 2008-04-29
When I re-logged in under Gnome, the icon appeared.  I checked the Nautilus setting before doing this and that setting _was_ checked.  I unchecked it and re-checked it just to be sure.  Now going to see if icon appears on Kubuntu desktop (though why it should I have no idea -- just testing).

Tony

---

