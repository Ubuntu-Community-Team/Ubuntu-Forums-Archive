---
title: "Driver Conflicts?"
date: 2011-04-27
forum: Hardware
---

### Post by kingary on 2011-04-27
I've a dual boot system: Ubuntu 10.10 on one drive, Windows 7 on another, with a third drive for storage. Recently, my network card stopped working in Windows. It worked fine in Linux, but not Windows. I took it to a computer shop; they plugged everything up; everything of course worked like a charm. 

"It was a driver conflict," one individual stated. "You need to install the Linux driver."

I thought drivers were part of the kernel...

The problem disappeared on its own.

Now the same thing is happening with the two optical drives. Linux sees them and makes use of them beautifully; Windows seems them (via device manager) but they don't show up in a drive listing (i.e., in the My Computer console). Since I had a similar problem with the network card, I thought they might be related.

A little snooping indicated it might be a problem with Grub.

Any thoughts?

---

### Post by Yellow Pasque on 2011-04-27
> Any thoughts?
I think I would find a new computer shop if they really think that installing Linux drivers on Windows would actually work..

---

### Post by lidex on 2011-04-28
> **kingary said:**
> 

Any thoughts?

Yes, escape from microshaft as quickly as you can.

---

### Post by K_45 on 2011-04-28
The computer shop may have deliberately "broken" something to get you to come back or screwed around with windows. Drivers/firmware are part of the kernel (inline or module), unless some are excluded (Debian's libre kernel) which you can then install them at your leisure. I'd clean install Ubuntu or another distro and murder windows unless you really need it.

---

