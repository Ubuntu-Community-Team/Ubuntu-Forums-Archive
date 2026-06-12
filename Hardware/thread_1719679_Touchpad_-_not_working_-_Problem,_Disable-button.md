---
title: "Touchpad - not working - Problem, Disable-button"
date: 2011-04-02
forum: Hardware
---

### Post by Kobin on 2011-04-02
Hi

I have an Aspire 5739G laptop, and have had Ubuntu 10.10 64-bit installed for a couple of months. Everything has been working perfectly up to a couple of days ago.

On the laptop there is a button next to the touchpad, which enables/disables the touchpad.
The other day a pressed it, which has not given any problems before. Now Ubuntu shows me that the touchpad is disabled when the button is enabled, and the other way around too. Also the touchpad is never working.

Is there some flag that is set in Ubuntu when enabling og disabling the touchpad?
I could of course reinstall Ubuntu, but I would rather not...
Any ideas?

---

### Post by matt_symes on 2011-04-02
Hi

Open a terminal and type

```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

That may be causing you the issue with the disabled touchpad.

Kind regards

---

### Post by Kobin on 2011-04-02
Thanks!

It's working now.

---

