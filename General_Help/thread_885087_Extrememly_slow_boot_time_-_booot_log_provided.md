---
title: "Extrememly slow boot time - booot log provided"
date: 2008-08-09
forum: General Help
---

### Post by mr. Twitch on 2008-08-09
Hi All,

im running Hardy on the following system

Core2Quad Q6600
4gig OCZ ram
Abit IP35Pro Motherboard
8800GTX 768meg

The boot time is extremely slow.

can someone hvae a look at this and try and help me with it?

The file is too big to upload with the file uploader, so here is a link to it

[http://thelab.guidesigns.net/bootuplog.txt](http://thelab.guidesigns.net/bootuplog.txt)

Thanks

- twitch

---

### Post by Diabolis on 2008-08-09
If we were tracking a specific problem, the log would help, but we don't know yet what is the problem.

While booting press the "esc" key and the grub menu will show up. Press "e" to enter edit mode. Then you'll see 3 lines of text, select the one that says "kernel". At the end of the line remove "quiet splash", save the changes and reboot.

Now you'll be  able to see at which point the boot up is hanging.

---

### Post by spiderbatdad on 2008-08-09
It looks like there might be some issue configuring the wireless.

I see you have added irqpoll as a kernel boot option.
```
Kernel command line: root=UUID=(#'s) ro splash irqpoll

```
You might try pci=routeirq instead...not sure. There are other options that might work as well like noapic irqpoll. Regardless, perhaps you could delete the splash option.
You should be able to see, with a verbose boot, where the system configuration is hanging.

---

### Post by mr. Twitch on 2008-08-09
i dont have wirelesss on my PC :S

but yeah, ill try some of those and get back to you

---

