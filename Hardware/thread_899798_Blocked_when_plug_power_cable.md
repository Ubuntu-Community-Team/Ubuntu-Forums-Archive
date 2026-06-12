---
title: "Blocked when plug power cable"
date: 2008-08-24
forum: Hardware
---

### Post by yoburtu on 2008-08-24
Hello,

I have a Sony Vaio VGN-SZ2XP laptop with Ubuntu Hardy Heron.

I have the following problem. When I plug the power cord, the system is totally blocked and I have to shut down and turn on the button.

The problem does not occur in Windows, or FreeBSD, or Mac OSx86.

Not if you have something to do with the gnome power manager.

Any ideas?.

Best regards.

---

### Post by yoburtu on 2008-09-03
Hello,

the problem is acpi. When I boot the system with option "acpi=off" I can plug the power cord and the laptop don't block, but don't work many things, with graphic card, mouse, etc, :-(.

What can I do with acpi?, how can I configure acpi correctly?.

Best regards.

---

### Post by yoburtu on 2009-10-08
I've solved this issue. I've configured kernel boot option "idle=poll" and the box don't blocks. 

Greetings.

---

