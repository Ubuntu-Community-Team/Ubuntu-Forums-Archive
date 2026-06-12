---
title: "Disable password-request after Suspend?"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by schmolch on 2007-11-23
Hi there,

Im running Ubuntu on a Tablet-PC so a keyboard is not always available.
Is there any way to disable the password-request when you wake-up the Laptop?

Thx!

---

### Post by Linicks on 2007-11-23
Have a look in:

```
/etc/default/acpi-support
```

...

```
# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true
```

Nick

---

### Post by schmolch on 2007-11-23
Thanks!

---

### Post by schmolch on 2007-11-25
It doesn't work.
I tried commenting it and setting it to false and both times i rebooted but it still asks for the password.

---

### Post by Linicks on 2007-11-25
Well, I guess that is a bug - if you tell it to not ask for a password as per the remarks, it should work.

File a report on launchpad.

Nick

---

### Post by schmolch on 2007-11-25
Ok, done.

---

### Post by awahlig on 2007-12-07
For me it worked after I disabled screen locking in screen saver settings and then:
1. Started "gconf-editor" from Terminal.
2. Checked "/apps/gnome-power-manager/lock/use_screensaver_settings" option.

I'm using Ubuntu 7.10 on a Thinkpad T41.

---

### Post by zikkut on 2007-12-08
awahlig's method posted above (and here again) worked for me too :)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1. Started "gconf-editor" from Terminal.
2. Checked "/apps/gnome-power-manager/lock/use_screensaver_settings" option.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I'm using Ubuntu 7.10 on an HP desktop.

Thanks for the helpful posting awahlig!

---

