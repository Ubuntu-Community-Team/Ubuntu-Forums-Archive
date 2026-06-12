---
title: "Forget Profiling!"
date: 2008-09-21
forum: General Help
---

### Post by solarwind on 2008-09-21
Hey all, I profiled my system with the *profile* boot flag. It's actually making my laptop boot slower. Is there a way to get the system to "forget" the profiling and work like before the profiling was done?

---

### Post by stickmangumby on 2008-09-22
Did you add it as an option in your /boot/grub/menu.lst? Or did you edit it manually in GRUB when you turned your computer on?

It sounds like you did the first one, which is causing it to profile the boot on every bootup. You need to do the second one, which profiles it once, and then uses that profile on later boots.

Does that make sense?

---

### Post by solarwind on 2008-09-22
> **stickmangumby said:**
> Did you add it as an option in your /boot/grub/menu.lst? Or did you edit it manually in GRUB when you turned your computer on?

It sounds like you did the first one, which is causing it to profile the boot on every bootup. You need to do the second one, which profiles it once, and then uses that profile on later boots.

Does that make sense?
No! I'm not that stupid... I profiled it ONCE by editing the menu during boot. I now want it to forget the profiling. How do I do this?

---

### Post by solarwind on 2008-09-24
Bump.

---

