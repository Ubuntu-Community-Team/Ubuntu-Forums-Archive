---
title: "What is the command for a Keybinding"
date: 2008-11-25
forum: General Help
---

### Post by t4ggs on 2008-11-25
I use Ctrl+W for the Scale plugin of compiz... but i want to have an applet in the gnome bar for it...so i want to make a launcher in the bar but if i wrote in the command line <Control>w, nothings happen..what should i write???

---

### Post by sdennie on 2008-11-25
You'd have to use make a dbus call to the scale plugin.  An easier way to accomplish something similar to what you want would be to use a screen corner + click.  First install ccsm

```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop Settings->Scale Plugin->Bindings.  From there you should be able to setup the screen corner + click (should be the 3rd binding).

---

### Post by t4ggs on 2008-11-25
Thank you i already have ccsm and i know about the screen edges, but i want an applet/button in the gnome bar.. i just don't know how to do that.. i thought that maybe it will be possible by making a launcher and that the command will be they key combination (Ctrl+w) that i use for Scale.

Anybody knows how to do that?

---

### Post by sdennie on 2008-11-25
Making a launcher with the following command will do what you want:

```

sh -c "dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/scale/allscreens/initiate_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`"

```

---

### Post by t4ggs on 2008-11-25
Muchas gracias ché
q genio
pq no hay un applet asi q venga con ubuntu? me parece muy util

Thank u so much, it worked.

---

### Post by sdennie on 2008-11-25
> **t4ggs said:**
> Muchas gracias ché


;)

> 
pq no hay un applet asi q venga con ubuntu? me parece muy util

Thank u so much, it worked.

Well, much of compiz can be controlled or configured via dbus-send or gconftool-2.  It's probably not very common to do it though so, there hasn't been a need to add specific GUI tools to do what you wanted to do.  It's good to know there is a way to do it though.  :)

---

