---
title: "Touchpad scroll takes time to initialise?"
date: 2010-01-30
forum: Hardware
---

### Post by AnotherMuggle on 2010-01-30
The scroll section of my synaptics touchpad does not work immediately on boot.  Sometimes it takes a few minutes before the scrolling kicks in.  If I run the command "synclient -l" to check the configuration then this immediately kicks the scrolling into action.

Anyone got any suggestions on what's causing this?

Cheers,
TK

---

### Post by chessnerd on 2010-01-30
> **tomkear2006 said:**
> The scroll section of my synaptics touchpad does not work immediately on boot.  Sometimes it takes a few minutes before the scrolling kicks in.  If I run the command "synclient -l" to check the configuration then this immediately kicks the scrolling into action.

Anyone got any suggestions on what's causing this?

Cheers,
TK

Not sure what's causing that, but if running synclient makes it work you could try adding synclient to your list of startup progarms. System>Preferences>Startup Applications (it used to be called Sessions in older versions).

Might work, but I'm not sure what's causing your problem.

---

### Post by AnotherMuggle on 2010-01-30
Thanks for the speedy assistance. It's a problem I seem to have had with a few different Ubuntu releases I've tried.

I will try adding the line to the startup as suggested.

---

