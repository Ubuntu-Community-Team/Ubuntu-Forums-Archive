---
title: "lowest brightness setting after boot"
date: 2009-06-11
forum: Hardware
---

### Post by give.away on 2009-06-11
Hai!

Every time I boot the brightness is set to its lowest setting.
This was not the case in the versions previous to Jaunty, which I use now.
Furthermore it is only dimmed if I had booted to Windows Vista before.
(I. e. consecutive Ubuntu boots preserve the brightness.)

I already modified a script containing
echo "12" > /proc/acpi/video/VGA/LCDD/brightness
to /etc/init.d/ which successfully restores the brightness.
(Fn+brightness up/down work fine too, but this is just annoying.)

BUT now I have an ugly flickering from bright to dark to bright.
So my question is: How do I turn off the dimming of the brightness in the first place!

Thanks in advance,
GA

---

### Post by give.away on 2009-06-14
Hai!

I thought it might have to do with the kernel, but after an update to .30, the brightness reset remains.

Anyone an idea?

Please help!
GA

---

### Post by PatrickVogeli on 2009-06-14
the solution is quite easy: don't boot Windows :D

Nah, really, you could try going into the gnome-power-manager settings and unchecking everything which has to do with dimming.

Also, in gconf-editor under apps->gnome-power-manager->backlight has some stuff in it.

If that doesn't work, maybe the problem lies somewhere else.

---

### Post by give.away on 2009-06-15
Hai and thank you!

Not booting Windows - it can't be that easy ;)
But seriously, changing the gnome-power-management settings doesn't work.

BUT it seems that the backlight is only dimmed if an external monitor is plugged in ...

What causes this behavior? How can I change it?

Thanks in advance,
GA

---

