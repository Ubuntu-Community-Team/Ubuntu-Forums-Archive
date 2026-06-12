---
title: "Slow touchpad"
date: 2011-08-31
forum: Hardware
---

### Post by _simon_ on 2011-08-31
I have a Dell Inspiron Mini 1012. fresh install of Ubuntu 11.04 32bit.

On login the touchpad is very slow, I have to move the sliders in pointing devices to get it working as it should. The problem is that I have to do this every time I login. The settings are remembered in pointing devices but don't take affect unless I move a slider.

If I try launching gpointing-device-settings from terminal it opens but I also see this message "An X error occurred. The error was BadAtom (invalid Atom parameter)."

Can I fix this?

---

### Post by _simon_ on 2011-09-02
Any suggestions?

---

### Post by _simon_ on 2011-09-03
After much searching I've found a workaround for this.
Seems gpointing-device-settings not remembering settings is a known fault.

You can get around this by using synclient.

To list all values enter at terminal:
```

synclient -l

```

For min and max pointer speed which is what I needed this is the kind of thing you want:

```

synclient MinSpeed=7.0 && synclient MaxSpeed=7.0

```

Obviously you can change the values to suit.
Once you find a setting you're happy with then simply add it to your startup applications.

---

