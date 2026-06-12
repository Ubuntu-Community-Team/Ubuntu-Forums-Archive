---
title: "Compiz -&gt; Window Rules - Firefox stays fullscreen"
date: 2008-11-01
forum: General Help
---

### Post by Forseti on 2008-11-01
Hello!

I've got a problem with Compiz.  
I turned on the Window Rules plugin and entered "class=Firefox" into "Fullscreen mode". As expected, Firefox began to open in fullscreen mode.

But later I 've changed my mind and cleared the "Fullcrteen mode" line. Despite it, the effect persist. I've even turned the plugin off - to no avail. I've looked info GConf - registry key for fullscreen mode is cleared.

The problem is on the Compiz side - after switching to Metacity it disappars and Firefox opens normally.

So, do you have any Idea how to finally disable this effect. I'd be gratefull for help.

Regards,
Forseti

---

### Post by salingova on 2008-11-01
maybe I am way off, but try to press F11

---

### Post by Forseti on 2008-11-02
Tried that and to no avail. Firefox switched between GNOME fullscreen mode (no panels, no window decoration) and Firefox one ( + without menubars).

But meanwhile I upgraded Compiz from Ubuntu's 0.7.8 to Launchpad's newest version. It helped somewhat.  When I opened CompizConfig the line "class=Firefox" reappeared and I had to delete it again. Now Firefox still opens at fullscreen but two "F11" keystrokes return it to old good maximized state.

But this still is sidestepping the problem and I'm looking for a final solution.

Regards,
Forseti

---

### Post by loomsen on 2008-11-02
Export your profile to sth like ~/backup/compiz/default.profile

You don't want to skip default values.
Then open it with gedit for example:

```
gedit default.profile
```

Search for [winrules], Ctrl+F will give you a searchbox.

And there, just hardcode it, delete it, do whatever you want.

Then save your File again. close it and try importin it back into compiz.


[quote]But meanwhile I upgraded Compiz from Ubuntu's 0.7.8 to Launchpad's newest version[/code]

Which actually is the same version ^^
[[img]http://img243.imageshack.us/img243/2752/screenshot20ep1.th.png[/img]](http://img243.imageshack.us/img243/2752/screenshot20ep1.png)

Btw, you most likely will have to reload your window manager for window hints/placement/rules to take effect... Just rightclick on fusion icon and chose reload window manager

---

### Post by octavianus on 2009-02-17
Take the following two steps :

 1. system > preference > Compiz config settings manager > general options > tab general > undirect fullscreen windows  ( uncheck it ).

The above should solve the issue. If still the problem persists ,

2. Remove Firefox including all the relevant Mozilla configuration files and reinstall Firefox.


This is how I have solved the full screen issue.

---

