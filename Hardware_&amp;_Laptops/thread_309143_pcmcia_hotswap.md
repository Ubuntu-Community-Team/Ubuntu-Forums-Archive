---
title: "pcmcia hotswap"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by abaybas on 2006-11-29
Hello everyone,
I have two pcmcia cards, one orinico wireless card and one usb2.0 pcmcia adapter. I only have one pcmcia slot. Both cards work if they are inserted during boot, but hotswapping doesn't work.

Do I have to do anything extra to enable hotswapping? Is there a manual way to get ubuntu to mount/umount pcmcia cards?

Thanks for the help.

---

### Post by Fabratas on 2006-11-29
Hello,

I suppose you're on Edgy - in that case the command to use is

[FONT="Courier New"]pccardctl eject 0[/FONT]

where 0 is your slot number (one single pcmcia slot).

'man pccardctl' will give you more commands.

Cheers,

fab

---

### Post by abaybas on 2006-11-29
> **Fabratas said:**
> Hello,

I suppose you're on Edgy - in that case the command to use is

[FONT="Courier New"]pccardctl eject 0[/FONT]

where 0 is your slot number (one single pcmcia slot).

'man pccardctl' will give you more commands.

Cheers,

fab

That's exactly what I was looking for. Thanks!

---

