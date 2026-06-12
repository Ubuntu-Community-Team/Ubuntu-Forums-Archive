---
title: "Hibernate when battery at critical level"
date: 2009-07-05
forum: Hardware
---

### Post by AnotherMuggle on 2009-07-05
I enabled the "Hibernate" option for "When battery power is critically low" on my laptop with Ubuntu 9.04.  I like this option because I can keep working till the battery has no juice left and if I've not saved then all is not lost and I can cary on where I was when I next boot.

I enabled this option when I first installed Ubuntu and for the first few times it worked flawlessly.  Last time the battery ran low, I got the warning that it was getting critically low, but the laptop just lost power instead of doing a graceful hibernate/shutdown routine.

I think the issue is because the hibernate is kicking off once the battery is already too low.  Is there any way for me to make the laptop hibernate sooner, so there is enough power left in the battery for it to take place?

Cheers,
Tom

---

### Post by bigfootsbigfoot on 2009-08-12
Run gconf-editor, edit /apps/gnome-power-manager/thresholds/time_action (and probably also time_critical), probably read the short/long descriptions of the keys to be sure what you're doing. The mentioned "use_time_for_policy" flag can be found under /apps/gnome-power-manager/general/.

---

### Post by kraymore on 2009-08-12
i'm looking at /apps/gnome-power-manager/threshold and i do not understand the values time_action 120 time_critical 300 and time_low 1200.  the other 3 are in percentages  percentage_action 2 percentage_critical 3 and percentage_low 10   and could use a little explaining the difference between action and critical.   

i actually want my laptop to take action at 15%, however, i literally was hoping for a shutdown.  i'm not sure if hibernation works for me, or how to bring it back to life, once its hibernated.  also, it might continue to drain the battery i assume in hibernation mode ?

anyway i can adjust these values for a laptop shutdown at 15% battery life ?

---

### Post by bigfootsbigfoot on 2009-08-12
> **kraymore said:**
> i'm looking at /apps/gnome-power-manager/threshold and i do not understand the values time_action 120 time_critical 300 and time_low 1200.  the other 3 are in percentages  percentage_action 2 percentage_critical 3 and percentage_low 10   and could use a little explaining the difference between action and critical.I didn't invent these values, but an educated guess would be that _critical is the time when a "your battery level is critical!" warning is issued, and _action is the time when *whatever action was defined* is carried out, e.g. shutdown or hibernate.
> **kraymore said:**
> i actually want my laptop to take action at 15%, however, i literally was hoping for a shutdown.Don't hope. Configure it in the normal Power Management Preferences, "On Battery Power", "When battery power is critically low", or under /apps/gnome-power-manager/actions/ (the keys have short and long descriptions which want to be read).
> **kraymore said:**
> i'm not sure if hibernation works for me, Just ... test it? Click on that button in the far right upper corner (or wherever you moved that in your Gnome), click "Hibernate" ...
> **kraymore said:**
> ... or how to bring it back to life, once its hibernated.Just switch your laptop on as usual. Probably just opening the lid already does that job, this is true for my Dell Latitude E6400.
> **kraymore said:**
> ... also, it might continue to drain the battery i assume in hibernation mode ?No, hibernation is defined not to utilize any power. It saves the current state on the hard disk and powers off completely. "Suspend" is the mode where power is utilized for keeping the state in RAM, but this has the advantage of a faster startup. Of course, "suspend" is not such a good idea for a "battery critically low" action.
> **kraymore said:**
> anyway i can adjust these values for a laptop shutdown at 15% battery life ?Yes, as I said: Read the descriptions in the /apps/gnome-power-manager/thresholds/* keys. The time_* keys ("so and so many seconds before battery is empty") are valid when /apps/gnome-power-manager/general/use_time_for_policy is *true*, the percentage_* keys ("that many percent battery life left") are valid when /apps/gnome-power-manager/general/use_time_for_policy is *false*.

---

