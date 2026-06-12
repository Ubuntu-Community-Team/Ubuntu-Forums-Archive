---
title: "linuxwacom-0.8.0-3 / cintiq 12wx not eorking"
date: 2008-08-04
forum: Hardware
---

### Post by ceti331 on 2008-08-04
attempting to install linuxwacom-0.8.0-3 (wanting cintiq 12wx support) appears to not work for me... xwindows not fully seeing things.

Here´s what I did...
[1] Installed Xubuntu 7
[2] edited xorg.conf... -> INTUOUS TABLET WORKED IN ABSOLUTE MODE, AND WORKED WITH GIMP; Cintiq 12WX was not recognized.
[3] Upgraded to Xubuntu 8 -> INTUOUS TABLET STILL WORKED
[4] Downloaded linuxwacom-0.8.0-3,  went into rebuilt, did ./uninstall, ./install
XWindows can still use the intuos tablet but only in that manky RELATIVE mode; also GIMP no longer sees it (configure extended input devices).
It still doesn recognize the 12wx
I went back through various options in xorg.conf (/dev/input/event0 vs /dev/input/wacom...) to no avail.

Any ideas what i´d done wrong ... what should you do to get the Cintiq working?
Is it worth trying ¨ubuntu studio¨.. is that more likely to come with the right bits out of the box..
I could start again & re-install I guess, getting me back to stage [2] above, which is something.

Very nearly there but not quite. Please help me avoid going back to windows on this laptop :)

---

