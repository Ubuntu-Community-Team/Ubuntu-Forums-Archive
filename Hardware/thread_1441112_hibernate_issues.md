---
title: "hibernate issues"
date: 2010-03-28
forum: Hardware
---

### Post by fidelandche on 2010-03-28
Hi,

  My partner is running 9.10 as her only OS on a Toshiba satellite L300. She would like to enable hibernation when the lid is closed. I have gone into the power management and enabled it there on battery and AC, but when the lid is closed the laptop does not go into hibernation. Does anyone have any ideas of what I can do to resolve this please.

---

### Post by hugin0 on 2010-03-28
Have you tried forcing it to hibernate on command?  You could try doing this with the option from the logout widget in the taskbar (where the username is.)  This might narrow down the issue from it not working when you want it to, to not working at all.  This is probably the first step.

-hugin0-

---

### Post by fidelandche on 2010-03-28
Have tried that, and that works but not via the power management option.

---

### Post by hugin0 on 2010-03-28
ok, the next step is to figure out if the proper events are firing when the lid is closed and opened.  you can do this buy firing up a console (hope this isn't a dirty word for you) and running the comand 'acpi_listen' and then closing the lid.  end the program with 

If the events are firing properly, and it works properly when you select the option from menu... i'm sort of at a loss.  you could look into the scripts in /etc/acpi/events and make sure the event is linked to the right script... but i'm not sure if that is how gnome makes that work or not, i normally run lighter systems than gnome.

-hugin0-

---

