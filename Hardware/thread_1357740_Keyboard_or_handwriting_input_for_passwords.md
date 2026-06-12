---
title: "Keyboard or handwriting input for passwords"
date: 2009-12-17
forum: Hardware
---

### Post by cenzorrll on 2009-12-17
Hiya everybody. I have a tablet pc and was wondering if there was anyway to have an on screen keyboard or handwriting input available for logging in, waking up from suspend/hibernate, and for inputing gksu passwords.  As it is, i find it to be really annoying to have to swivel the screen just to input a password.  Any input would be helpful, and I'm more than willing to be a guinea pig for any developers/tweakers as i enjoy trying new features (read as: enjoys breaking the system, trying to repair it, while breaking something else trying to do so)

---

### Post by Favux on 2009-12-17
Hi cenzorrll,

I think Karmic has a new option for an onscreen keyboard at login.  You could look for that.

I do have a mini HOW TO for it, for I guess Ubuntu versions previous to Karmic (if I'm right about the new option).  It's in [post #8]("http://ubuntuforums.org/showpost.php?p=7959338&postcount=8") on billklee's "Re: Fujitsu Stylistic St5010D" thread.

---

### Post by cenzorrll on 2009-12-17
fantastic, after some digging and that post i'm starting to get somewhere.  karmic does have the option, i was just too dumb to see it.  but i personally think onboard is pretty fugly, so thanks for the link.

i've also found a way to get one for waking up from suspend and hibernation.

type:
```
gconf-editor
```

the expand: apps>gnome-screensaver

and for "embedded-keyboard-command" enter "/usr/bin/cellwriter --xid --keyboard-only"

and make sure "embedded-keyboard-enabled" is checked

it adds a giant keyboard to the bottom of the screen, but at least it's something.

I'm marking this as solved, even though i haven't figured out the gksu thing yet (don't think it's all that possible at the moment)

EDIT: i forgot to mention in the first post that i still want gksu to lock out other programs but allow cellwriter or some other OSK to be used.

---

### Post by Favux on 2009-12-17
Hi cenzorrll,

Wow, serious progress!

---

