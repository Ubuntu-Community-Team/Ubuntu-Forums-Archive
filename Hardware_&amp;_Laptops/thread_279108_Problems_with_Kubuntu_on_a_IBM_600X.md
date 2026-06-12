---
title: "Problems with Kubuntu on a IBM 600X"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by linuxuser28 on 2006-10-17
I'm running Ubuntu 6.06 on a IBM ThinkPad 600X. I installed Kubuntu using Synaptic but when I switch over to it there are vertical lines running through some of the menus and buttons. Any solution for this?

---

### Post by KHatfull on 2007-01-04
Finally, I can answer one!

You need to change your default color depth in xorg.conf to 16 from 24.   Even though the neomagic xorg driver is supposed to support 24 bit, it doesn't...properly at least.

I don't have my Ubuntu machine in front of me or I'd give you the exact line...search for "24"...you'll find it, and it will be obvious that it's referring to color depth.

-Keith

---

