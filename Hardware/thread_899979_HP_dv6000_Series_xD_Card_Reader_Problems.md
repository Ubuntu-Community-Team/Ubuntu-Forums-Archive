---
title: "HP dv6000 Series xD Card Reader Problems"
date: 2008-08-24
forum: Hardware
---

### Post by jazee on 2008-08-24
I seem to be having a problem with just the xD portion of the card reader. All the other sides mount just fine but when I stick an xD card in nothing seems to happen. I don't even get an error log in /var/log/messages. lspci does show the card as existing. Is there something I need to do to enable the card reader?

---

### Post by jazee on 2008-08-27
Just a quick bump to see if anyone has any ideas on how to get the xD card reader to register the media inserted into it.

---

### Post by sergiom99 on 2008-08-27
well, this issue has been covered LOTS of times in the forums, there's no kernel support for built-in multicard readers yet. they only work with SD cards now. Someone has to code drivers for them and built them in the kernel.

USB card readers work just fine though.
Good luck.

---

### Post by Forgotten Path on 2008-08-27
You know, I have a HP dv2000, and I had the same xD card problem while running *Windows*.  Maybe it has something to do with a hardware failure too, because mine originally worked, but then just stopped.   :confused:  Oh well...:(

---

