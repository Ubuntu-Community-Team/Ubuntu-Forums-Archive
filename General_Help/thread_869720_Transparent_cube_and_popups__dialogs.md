---
title: "Transparent cube and popups / dialogs"
date: 2008-07-25
forum: General Help
---

### Post by esdaniel on 2008-07-25
Hi,

When I have the transparent option of the compiz cube plugin enabled I notice that dialog and popup menus are duplicated on other viewports.

Has anyone discovered or knows how to just have these windows appear on the viewport in which they were activated?  Same for tooltips on the taskbar etc...

Ed.

---

### Post by AmericanYellow on 2008-07-25
I think that's just the way compiz is designed to work. You can probably go to compiz forums and double-check. You can also post a request in the Compiz forums a suggested improvement/feature.

---

### Post by Darkshade on 2008-07-25
Well most people use transparency on the cube only when it's rotating, that's probably why the issue was not fixed (or even reported) yet. Check the compiz forums as suggested above, maybe you can find some tips there.

---

### Post by esdaniel on 2008-07-28
> **AmericanYellow said:**
> I think that's just the way compiz is designed to work. You can probably go to compiz forums and double-check. You can also post a request in the Compiz forums a suggested improvement/feature.

[Done]("http://forum.compiz-fusion.org/showthread.php?p=63677#post63677").

---

### Post by esdaniel on 2008-07-29
Solution [here]("http://www.efaref.net/compiz/plugins/static.html").

**Params:**

***Window Match***

Dock | Tooltip | Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog |( state=Sticky & !Desktop ) | class=Notification-daemon

---

