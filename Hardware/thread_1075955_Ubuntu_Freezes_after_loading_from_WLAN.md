---
title: "Ubuntu Freezes after loading from WLAN"
date: 2009-02-20
forum: Hardware
---

### Post by The Hammer on 2009-02-20
I'm new to Linux, however I don't think my question would get answered in the newbie forums. I have an old COMPAQ Deskpro:
[INDENT]1GHz processor
320 MB RAM[/INDENT]
I just got a TP-LINK 54M Wireless PCI Adapter M/O:TL-WN353GD.
When it is in the computer, right after the Ubuntu is done loading (before the peach screen)the whole thing freezes and the keyboard doesn't work. It works fine when it's not in. I installed the driver using NDISWrapper.

After I installed the driver, when I restarted (with or without the card in)I got an error that said:
[INDENT]Buffer I/O error on device sr0, logical block ...[/INDENT]
I turned ACPI off and the error went away, however it still froze after loading. But I'm pretty stumped and any help would be great. Thanks

---

### Post by cariboo on 2009-02-20
The error you are gettng has nothing to with you wireless device, it is usually caused by a cd that is not readable, or one that is improperly burned.

The freezing problem sounds like an irq conflict, can you start in recovery mode and at the prompt type:

```
cat /proc/interrupts
```  

to see if it is using the same irq as anything else?

Jim

---

