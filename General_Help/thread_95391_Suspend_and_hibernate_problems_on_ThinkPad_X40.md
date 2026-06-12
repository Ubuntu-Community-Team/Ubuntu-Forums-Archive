---
title: "Suspend and hibernate problems on ThinkPad X40"
date: 2005-11-26
forum: General Help
---

### Post by LeSkip on 2005-11-26
Ubuntu 5.10 works very well on my IBM ThinkPad X40, but I have problems with both suspend and hibernate.

1) Suspend usually works, but when I resume I sometimes just get to type in my password and see the desktop before it returns to suspend. I can then resume once again, and this time I do not have to type in my password. Quite annoying.

2) Hibernate usually does not work. Most of the time it seems to reach the point where it should power off, but instead it immediately resumes the session from disk. Sometimes it does work, though, and I don't know why. As I switch between Linux and Windows, being able to suspend to disk would be incredibly powerful.

Is there some way to solve these problems?

Thanks,
Skip

---

### Post by LeSkip on 2005-11-29
It now appears that the first problem is caused by the lid button.

If I suspend using Fn-F4, the lid button is never trigged since the machine is off when I close the lid. When I open the lid, however, it is trigged, leading ubuntu to believe I want to suspend it again.

This is quite silly and must be very simple to fix. Does anyone know who I should get in touch with about the problem?

---

### Post by ranf on 2005-11-29
[QUOTE=LeSkip]It now appears that the first problem is caused by the lid button.

If I suspend using Fn-F4, the lid button is never trigged since the machine is off when I close the lid. When I open the lid, however, it is trigged, leading ubuntu to believe I want to suspend it again.

This is quite silly and must be very simple to fix. Does anyone know who I should get in touch with about the problem?[/QUOTE]
Look at the files in `/etc/acpi/events'.

---

### Post by LeSkip on 2005-12-11
The hibernation problem has to do with my swap partition being too small.

Case closed.

---

