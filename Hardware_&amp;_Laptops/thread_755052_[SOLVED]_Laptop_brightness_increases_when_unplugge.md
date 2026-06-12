---
title: "[SOLVED] Laptop brightness increases when unplugged?"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by jimv on 2008-04-14
I'm running Hardy beta, and recently my laptop started dimming when I plug the power in, and getting brighter when on battery.  You know, the opposite of what should happen.

Any ideas why this could be?  (I'm getting updates now just in case.)

---

### Post by Gen2ly on 2008-04-14
This is a gnome power manager bug and will probably take a bit to fix.  The good news, laptop brightness is adjusted with acpi in newer pcs.  This can be adjusted manually like this:

```
cat /proc/acpi/video/(Laptop dependent)/LCD/brightness
```

This will give the current value.  To adjust it:

```
echo # > /proc/acpi/video/(Laptop dependent)/LCD/brightness
```

Will adjust it to the # level.  Of course there are applications that do this too :)

---

### Post by jimv on 2008-04-14
I installed today's updates and one of them was for ACPI.  I rebooted and all seems well now.

On another note, the brightness keys on my keyboard don't work, and there's nothing in /proc/acpi/video.  Unsupported ACPI or soemthing?

---

