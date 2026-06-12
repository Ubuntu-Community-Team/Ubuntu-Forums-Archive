---
title: "problem using devilspie"
date: 2008-07-11
forum: General Help
---

### Post by coreofreeality on 2008-07-11
hi, i'm trying to get a terminal, on all workspaces by default.
i read on this forum to use devilspie, so i installed that and created a terminal.ds file inside of my ~/.devilspie/ directory which reads:

(if (is (window_name) "Terminal") (pin))

before that i tried:

(if (is (application_name) "gnome-terminal") (pin))

 but i cant seem to get it to work when i start up terminal (after starting devilspie).

what am i doing wrong?

---

### Post by hal8000 on 2008-07-11
> **coreofreeality said:**
> hi, i'm trying to get a terminal, on all workspaces by default.
i read on this forum to use devilspie, so i installed that and created a terminal.ds file inside of my ~/.devilspie/ directory which reads:

(if (is (window_name) "Terminal") (pin))

before that i tried:

(if (is (application_name) "gnome-terminal") (pin))

 but i cant seem to get it to work when i start up terminal (after starting devilspie).

what am i doing wrong?


With devils pie the command is set workspace so:

(if (is (application_name) "gnome-terminal") (begin (set_workspace 1))
starts the terminal in workspace 1.
Repeat the line for all other workspaces.

You also need to make sure devils pie is running before gnome starts so you may want to add it to your startup.
System - Prefereces - Startup and add devilspie if you have not done so already. Hope that helps

---

### Post by coreofreeality on 2008-07-11
i've already added it to the sessions in the preferences menu

does that start a separate terminal in all workspaces, or the same one?

---

### Post by Penguin Guy on 2009-03-28
"You also need to make sure devils pie is running..." Ahh... Thanks, I've been searching for why it wasn't working for ages. :P

---

