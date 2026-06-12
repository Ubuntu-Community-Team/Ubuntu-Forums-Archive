---
title: "Disable fan control - i8kutils"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by matt_b on 2008-04-18
Hi all,

I have a Dell Latitiude D430 laptop and the fan is (almost) permanently on when running Gutsy.

I have installed i8kutils and want to specify that the fan only comes on if the CPU reaches 60'C - which I have done. However, it only has effect for a couple of seconds :(
I can manually execute "i8kfan - 0" to turn the fan off (there's only one), but after a couple of seconds it comes right back on. The same applies if I use i8kfan to turn the fans up to max - they only run high for a couple of seconds, then back down to medium.

I think it's because something else is controlling the fan (ACPI?) - how can I find this out and disable it, so that only i8k governs the fan?

Thanks
Matt

---

