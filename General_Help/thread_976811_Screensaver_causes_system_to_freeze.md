---
title: "Screensaver causes system to freeze"
date: 2008-11-09
forum: General Help
---

### Post by GregoryMA on 2008-11-09
My screensaver causes the entire system to freeze.  However, I am unable to change my screensaver settings because the preview of the screensaver in use in system-preferences-screensaver also freezes the entire system.

I originally had my screensaver set to go to a blank screen after ten minutes.  But I went and looked through the different screesavers.  When I got to the one with the 3 ants in a ball, everything froze (thus setting my screensaver to that ant thing).  So I tried to go and change it back, but whenever I do everything freezes before I can change it.  And everything freezes when my screensaver turns on.  

Is there a command I can give to turn off the screensaver completely, or to change it back to a blank screen?  

Greg

---

### Post by fooman on 2008-11-09
do you have the visual effects enabled?  if so,  i would try disabling them first and see if you can make the changes to your screensavers.

go to system > preferences > appearance > visual effects tab....put a check next to "none"

---

### Post by GregoryMA on 2008-11-09
No they are off.

---

### Post by fooman on 2008-11-09
open gconf-editor...press alt-f2 keys and in the box type:

```
gconf-editor
```

press "run".  in the editor click apps > gnome-screensaver

on the right side,  scroll down to "themes" and double click on it.

in the box that pops up,  click once on the screensaver entry in the  "values" box,  then click the "edit" button on the right.  delete the entire line in the "edit list value" box and click "ok". click "ok" again on the next screen and then close the gconf-editor.

your screensaver should now be set to "blank screen"

---

### Post by GregoryMA on 2008-11-09
This worked perfectly.  Thanks.

---

