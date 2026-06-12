---
title: "Cairo-Dock config question"
date: 2008-07-27
forum: General Help
---

### Post by ddarsow on 2008-07-27
I have recently installed Cairo-Dock and find it to be very good. I was attempting to add a sub dock (with no success) and somehow managed to add a new launcher to the main dock with no icon or target.

When hovering over the newly created blank spot on the dock, the blank icon expands and the words "new launcher" appear. I can not right click on it to modify or remove it.

Any suggestions on removing the new launcher with n o icon or purpose as well as any input on adding sub-docks would be appreciated.

What I originally wanted to do was add an "Open Office" icon with a sub dock.

---

### Post by Mgiacchetti on 2008-07-27
try this, click on the launcher and hold, then drag it off the dock....  should disappear.

---

### Post by ddarsow on 2008-07-27
> **Mgiacchetti said:**
> try this, click on the launcher and hold, then drag it off the dock....  should disappear.

Nope. That does not work either.

---

### Post by fabounet on 2008-07-28
you added a launcher without any command ?
it's not expected, I suggest you go into ~/.cairo-dock/current_theme/launchers, and delete the .desktop file that contain a line like "Exec="

To add a launcher : drag'n'drop from the Menu
To add a sub-dock : right click->add a sub-dock, then populate it with launchers or applets.

---

### Post by ddarsow on 2008-07-28
That did it. Thanks.

---

