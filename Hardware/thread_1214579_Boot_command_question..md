---
title: "Boot command question."
date: 2009-07-16
forum: Hardware
---

### Post by Azuu on 2009-07-16
I am one of the unlucky people effected by the double clocking speed bug ([http://http://ubuntuforums.org/showthread.php?t=75281]("http://http://ubuntuforums.org/showthread.php?t=75281"))

I did fix it (after upgrading my GRUB to 1.95 which is easy to modify) but I am not sure if the fix will cause problems of it's own. the commands that work are:
> noapic nolapic(single core, not acceptable)
noapic acpi=off(one i am using)
and the other commands most of which I did not use are:
> noapic acpi=noirq (doesnt work)
noapictimer (doesnt work)
noapictimer irqpoll
noapic acpi=noirq nolapic

what exactly do these commands do, and could they cause any outstanding issues in?

---

