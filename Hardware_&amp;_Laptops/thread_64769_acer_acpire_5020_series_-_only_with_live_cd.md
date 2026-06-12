---
title: "acer acpire 5020 series - only with live cd?"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by bdaw on 2005-09-12
I have a problem with acpi (battery status and hibernation) on acer 5024.
I tryied to play with my dsdt and available kernel patches for 2 days but all failed, so I'm now waiting for some other users to post their feedback somewhere as I can't make it work.... :(

But could someone explain me one thing? How it is possible that when booting the hoary live cd battery status works fine while there are such big problems to make it work after install? Different kernel patch? huh... it's great to use the best hardware rocognizing live distro in the world but I'd like to have it on my hdd...

All in all... it seems that battery status is the only thing not fixed (on forums) related to my laptop.

---

### Post by TimT on 2005-09-20
I have the same problem on my 5024: everything works, but no battery status,

Battery status is visible with the stock ubuntu 2.6.10 kernel, which contains rather a lot of stuff I don't need
and I've seen it work with a 2.6.12.5 debian kernel, but I've been unable to reproduce the kernel.
(Even with the correct config)

I don't even see a corrected dsdt in the initrd included with 2.6.10; very frustrating  ](*,) 

Suggestions on how to proceed are welcome

TimT.

---

### Post by bdaw on 2005-09-20
[QUOTE=TimT]
Battery status is visible with the stock ubuntu 2.6.10 kernel, which contains rather a lot of stuff I don't need
[/QUOTE]

The first thing after hoary install was to update kernel to 2.6.11 from universe. At 2.6.10 udma was not working and installation took over an hour.... Frustrating that on  old kernel battery was fine and on newer it's wrong.....

---

### Post by bdaw on 2005-09-23
Ok. dist-upgrade with breezy yeasterday and with kernel 2.6.12-9-amd64-k8 battery status works fine!
Hibernation still hangs....

---

