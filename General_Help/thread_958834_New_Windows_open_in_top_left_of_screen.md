---
title: "New Windows open in top left of screen"
date: 2008-10-25
forum: General Help
---

### Post by AurolacKid on 2008-10-25
All of my windows open in the top left of the screen. Terminals, new pidgin conversations, nautilus. It's pretty annoying. I can move them but next time I open them they're in the top left of the screen again.

any ideas?

---

### Post by ciscosurfer on 2008-10-25
Save your open work.  Log out and then log back in.  What happens?

---

### Post by ww711 on 2008-10-25
Maybe you have a saved session?

---

### Post by AurolacKid on 2008-10-25
> **ciscosurfer said:**
> Save your open work.  Log out and then log back in.  What happens?

The problem persists.

---

### Post by AurolacKid on 2008-10-25
> **ww711 said:**
> Maybe you have a saved session?

Nope

---

### Post by Yashiro on 2008-10-25
Are you running Compiz/Fancy desktop effects?

Look at the Place Windows plugin.

---

### Post by AurolacKid on 2008-10-26
> **Yashiro said:**
> Are you running Compiz/Fancy desktop effects?

Look at the Place Windows plugin.

I don't know. how would I go about finding out?

---

### Post by Yashiro on 2008-10-27
Run [COLOR="Green"]gnome-appearance-properties[/COLOR] from a terminal window or an alt+f2 box.
On the visual effects tab, select None. Open some windows and move them around.
Log out and back in. Does this fix your bug?

---

### Post by AurolacKid on 2008-10-27
> **Yashiro said:**
> Run [COLOR="Green"]gnome-appearance-properties[/COLOR] from a terminal window or an alt+f2 box.
On the visual effects tab, select None. Open some windows and move them around.
Log out and back in. Does this fix your bug?

Nopers.

---

### Post by brandon88tube on 2008-10-27
To fix this go to System>Preferences>Advanced Desktop Effects Settings. Once that is open go down to Window Management and then select Place Windows. There should be an option called placement mode. I set mine to center so all new windows pop up in the center.

On a side note if you don't have Advanced Desktop Effects Settings under Preferences then you need to add it. I don't remember how to do this off the top of my head, but you can probably search it up.

---

### Post by sdennie on 2008-10-27
> **brandon88tube said:**
> To fix this go to System>Preferences>Advanced Desktop Effects Settings. Once that is open go down to Window Management and then select Place Windows. There should be an option called placement mode. I set mine to center so all new windows pop up in the center.

On a side note if you don't have Advanced Desktop Effects Settings under Preferences then you need to add it. I don't remember how to do this off the top of my head, but you can probably search it up.

This sounds like the right solution.  To get Advanced Desktop Effects use:

```

sudo apt-get install compizconfig-settings-manager

```

---

### Post by AurolacKid on 2008-10-27
I installed it and made sure it was enabled and set to center, same problem still.
It only seems to affect terminal windows and pidgin conversations now. and if I have something like opera open that takes up most of the screen the windows will stack up like this [http://www.ubuntu-pics.de/bild/4916/screenshot_01_J048cm.png](http://www.ubuntu-pics.de/bild/4916/screenshot_01_J048cm.png)
but if there's nothing else open taking up the screen they'll take a new position in the top left slightly off like this [http://www.ubuntu-pics.de/bild/4917/screenshot_02_492c32.png](http://www.ubuntu-pics.de/bild/4917/screenshot_02_492c32.png)

*shrug*
it looks like they snap and stack up to the titlebars

---

