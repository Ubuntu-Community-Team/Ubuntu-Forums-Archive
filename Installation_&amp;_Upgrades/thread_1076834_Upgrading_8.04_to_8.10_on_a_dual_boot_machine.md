---
title: "Upgrading 8.04 to 8.10 on a dual boot machine"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by EdSquareCat on 2009-02-21
Will upgrading 8.04 to 8.10 on my dual boot machine mess with my menu.lst or change my boot set up in any other way?

---

### Post by Partyboi2 on 2009-02-21
It will add the new kernel entries to your grub menu.lst.

---

### Post by EdSquareCat on 2009-02-21
So all it will do is add things? (It won't take away my Windows installation option or change it?)

---

### Post by Partyboi2 on 2009-02-21
No your option to boot into windows should still show up.

---

### Post by EdSquareCat on 2009-02-21
Okay thanks.

---

### Post by TimDaniels on 2009-02-21
> **Partyboi2 said:**
> No your option to boot into windows should still show up.

And if you have Vista's boot menu edited with an option to boot Ubuntu, that will also remain as valid. I was worried that I'd have go through the hassle to find the Ubuntu global ID for Vista's BCD boot menu and then use Vista's command line tools to re-edit the boot menu when I re-installed Ubuntu 8.04, but the old ID was still good after the Ubuntu installation.

*TimDaniels*

---

