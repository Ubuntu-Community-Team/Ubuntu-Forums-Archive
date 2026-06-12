---
title: "completely deactivate mousepad on dell"
date: 2008-06-10
forum: Hardware
---

### Post by melser.anton on 2008-06-10
Hi all,
I am trying to remotely (and when I mean remotely - I'm in France and the machine is in New Zealand!) *completely* deactivate my mum's mousepad. She has been very happily running 7.04 since last September and a couple of weeks ago things started to go awry. The cursor/pointer has started to go AWAL. She describes it as random but then that's my aging mum so I can't guarantee it... In any case, she is reduced to waiting for it to appear over firefox to get the web and then trying to click in time :-(.
In any case, she won't be doing any admin work, so it's me, but I do have ssh access to the machine.
So I'm pretty sure it's a hardware problem. It's about a 5-6 year old top range dell laptop (I don't have the exact model but can get it if necessary). We have managed to get it updated to 8.04 but it has changed nothing. It seems to periodically be ok for a few hours and then go back to random movement.
I tried deactivating everything but a ps2/usb mouse in xorg.conf but it hasn't had any effect. Does anyone have any suggestions? Is it for the rubbish dump?
Any help most appreciated!
Cheers
Anton

---

### Post by sdennie on 2008-06-10
If you are using gnome, you could try the following:

```

gconftool-2 --type bool --set /desktop/gnome/peripherals/mouse/touchpad_enabled false

```

Edit:
That's a user specific solution so, you'd need to be logged in as whatever user you want to disable the touchpad for.

---

### Post by melser.anton on 2008-06-10
> **vor said:**
> If you are using gnome, you could try the following:

```

gconftool-2 --type bool --set /desktop/gnome/peripherals/mouse/touchpad_enabled false

```

Edit:
That's a user specific solution so, you'd need to be logged in as whatever user you want to disable the touchpad for.

So su - mother should do the trick? (I'm sshing... though if necessary I could probably set up X forwarding...)

---

### Post by sdennie on 2008-06-10
That should do it, yes.

---

