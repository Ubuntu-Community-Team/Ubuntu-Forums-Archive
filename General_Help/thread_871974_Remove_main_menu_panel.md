---
title: "Remove main menu panel"
date: 2008-07-27
forum: General Help
---

### Post by roccivic on 2008-07-27
Hi,
I'd like to hide/remove the main menu. I have ubuntu, gnome 2.22.2 and avant-window-navigator. AWN has everything that I need, but I can't remove the main menu.

Here's a screenshot:
[http://www.placella.com/random/screenshot.jpg](http://www.placella.com/random/screenshot.jpg)

Many thanks, Rouslan

---

### Post by scragar on 2008-07-27
can't you just right click it and choose "delete this panel"?

---

### Post by chunchengch on 2008-07-27
You can try this.

Press Alt+F2 and input command [COLOR="Red"]gconf-editor[/COLOR] to open Configuration Editor, go to [COLOR="Blue"]app > panel > general[/COLOR] and open [COLOR="Blue"]toplevel_id_list[/COLOR] , then remove the value [COLOR="Blue"]top_panel_screen0[/COLOR], that is it.

---

### Post by Shazaam on 2008-07-27
Enable "Widget Layer" in ccsm. Go to Widget Layer>Behavior>Widget Windows and type in
```
name=gnome-panel
```
Click F9 to hide and unhide the panel.

---

### Post by roccivic on 2008-07-29
> **scragar said:**
> can't you just right click it and choose "delete this panel"?

No

---

### Post by roccivic on 2008-07-29
> **chunchengch said:**
> You can try this.

Press Alt+F2 and input command [COLOR="Red"]gconf-editor[/COLOR] to open Configuration Editor, go to [COLOR="Blue"]app > panel > general[/COLOR] and open [COLOR="Blue"]toplevel_id_list[/COLOR] , then remove the value [COLOR="Blue"]top_panel_screen0[/COLOR], that is it.

I've done this and it worked, but after I rebooted the computer the panel reappeared again, with all the default settings, as if it was just installed. Any way around this?

---

