---
title: "Brightness Control on Sony Vaio PCG-K415B"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by edal on 2005-10-11
It's a lovely screen on this machine, but run under Ubuntu it's so bright that you'll get a suntan (especially as the hotkeys don't work too well). Here's a way to turn down the brightness:

Pick a number between 1 and 8 and start up the root terminal

**echo "1" > /proc/acpi/sony/brt** sets the lowest screen brightness
**echo "8" > /proc/acpi/sony/brt** sets the highest screen brightness

Ed Almos

---

### Post by kairu0 on 2005-10-11
That works for mine as well.

Have you had any luck with the volume keys on the keyboard?

---

### Post by edal on 2005-10-12
None of the special function keys work for me but now that I have control over the brightness level I'm not too bothered about volume control and LCD/VGA switching. I'm more concerned about:

1) The poor battery life under Ubuntu. In XP the battery lasts 2 hours, in Ubuntu it lasts an hour and ten minutes.

2) The battery indicator only works if I remove the pack then reinsert it with the mains power applied.

3) I can put the laptop into standby or hybernation but cannot resume properly, X crashes on resume.

In short, Ubuntu is a nice distro but (like all distros) the power management sucks.

Ed Almos

---

### Post by szdavid on 2005-10-14
Hi,

it worked with my hoary but since i upgraded, it doesn't anymore...

Any idea ?

---

### Post by edal on 2005-10-16
Those of you running Ubuntu 5.10 'Breezy Badger' the command is:

echo "*n*" > /proc/acpi/sony/brightness where *n* is a number between 1 and 8. Note that the quotes around the numeric value are required.

edal

---

### Post by aev on 2005-10-29
Too many threads about the same topic. 
My laptop is Toshiba Satellite P15-S479 and I have problems with the brightness keys on Breezy. Basically, if I want to decrease the brightness the comp shuts down badly and I have to restart twice to get it working. It was fine on Hoary. :???:

---

