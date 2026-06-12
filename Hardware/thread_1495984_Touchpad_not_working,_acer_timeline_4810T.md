---
title: "Touchpad not working, acer timeline 4810T"
date: 2010-05-28
forum: Hardware
---

### Post by Sashin on 2010-05-28
Part way through the day, my touchpad seems to have stopped working. I don't remember changing any setting or upgrading.

It works in KDE, and on the log in screen but not in gnome.

anyone know how this could be solved?

---

### Post by Sashin on 2010-05-28
Bump!

---

### Post by Sashin on 2010-05-29
bump again

---

### Post by Sashin on 2010-05-29
bump

---

### Post by lidex on 2010-05-30
Something changed...did you reboot?

---

### Post by Sonador on 2010-05-30
What is your ubuntu version? I have similar problem, but on a *new* installation of 10.04, the solution for me was to tick in gconf-editor desktop/gnome/peripherals/touchpad/touchpad_enabled

---

### Post by Sashin on 2010-05-30
I'm using 10.04 and it wasn't on new install, it broke randomly. I'll restart and check now.

---

### Post by Sashin on 2010-05-30
It worked... Awesome! Thanks.

---

### Post by pwaugh on 2010-06-01
> **Sonador said:**
> What is your ubuntu version? I have similar problem, but on a *new* installation of 10.04, the solution for me was to tick in gconf-editor desktop/gnome/peripherals/touchpad/touchpad_enabled

Worked for me too!  Thanks.  Not sure how that got disabled though.

patrick

---

### Post by toyman90 on 2010-06-08
> **Sonador said:**
> What is your ubuntu version? I have similar problem, but on a *new* installation of 10.04, the solution for me was to tick in gconf-editor desktop/gnome/peripherals/touchpad/touchpad_enabled

for me it doesn't work.. it is already ticked on enabled. :(

---

### Post by lordmax10 on 2010-09-29
> **Sonador said:**
> What is your ubuntu version? I have similar problem, but on a *new* installation of 10.04, the solution for me was to tick in gconf-editor desktop/gnome/peripherals/touchpad/touchpad_enabled

=D> =D> =D> =D> =D>
 Thanks, really.
I know nothing 'bout gconf-editor and you saved my live.

:popcorn:

---

