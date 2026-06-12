---
title: "Is it my hardware that's broken or is it Ubuntu that's broken?"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2006-11-06
I can only boot my system if I specify 'irqpoll' or acpi_os_name="Microsoft Windows XP" in the kernel boot options.

When I boot using 'irqpoll', the system boots quickly, all drives are available, but it is not performing at its optimum level (irq polling hurts performance).

When I boot using acpi_os_name="Microsoft Windows XP", it boots slowly and I missing all (3) CD/DVD drives in my system... In addition, I am greeted by an error saying "Failed to init HAL".

In both cases, I am getting lots of errors of the following in my dmesg:

>  hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

What's wrong here? Is it my hardware or Ubuntu?

If it's my hardware, how come **this system works perectly and its maximum performance when using Windows 2000**?

I am attaching a copy of my dmesg output for your review and inspection.

Thanks!
Alex

---

