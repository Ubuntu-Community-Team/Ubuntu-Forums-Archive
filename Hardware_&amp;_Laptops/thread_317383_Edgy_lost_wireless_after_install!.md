---
title: "Edgy lost wireless after install!"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by OldGaf on 2006-12-12
Hi All,

My wife has a sony vaio. I managed to talk her into letting me put Dapper (Kubuntu) on it. On install I had to use the cat5 connection as it could not find the wireless. Once install was complete I could find the wireless and it worked fine from then on. The only issue we had was the Fn keys would not work.... not a biggy.

I have now done a clean install of Edgy hoping it would get the Fn keys working. This time the install detected both cards and I installed using the wireless. BUT...... once the install was complete and I rebooted, the wireless has disappeared. Does anyone know of this happening before? Should I reinstall the OS again?

---

### Post by ingo on 2006-12-14
you using a pcmcia card? what is the output when you enter ifconfig? what does iwconfig give you? please post both outputs. it may be as simple as 

sudo ifup your_interface

but post your stuff and we take it from there

---

