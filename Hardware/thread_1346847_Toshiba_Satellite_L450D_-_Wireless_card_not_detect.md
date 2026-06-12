---
title: "Toshiba Satellite L450D - Wireless card not detected."
date: 2009-12-05
forum: Hardware
---

### Post by Gazhole on 2009-12-05
Hi everybody,

I know wireless networking hardware/driver problems are pretty common, but i was wondering if anybody could help me out with this.

I recently bought a new laptop (Toshiba Satellite L450D) as my old Toshiba finally bit the dust after a good four years (i say bit the dust - it actually exploded, but thats besides the point :P).

The wireless card in my old laptop worked great with Jaunty, but this new one isn't even showing up as being there under Karmic. I don't know whether this is an issue between upgrades, or that my current wireless card isn't supported in either.

According to the spec provided by Toshiba, the card is a Realtek 8187B.

According to lspci the only Realtek hardware showing up is a 8172, and a RTL8101E/RTL8102E.

I've tried all the windows drivers for these using ndiswrapper, including trying to force the driver on the device i think is the wireless card in lspci (probably a bad idea!).

Past that, being a relative newbie i'm not really sure where to go from here. I've seen some stuff on google about compiling drivers into the kernel but that went way over my head, haha.

Any help you guys can give me would be excellent. If you need any other info just let me know!

Thanks a lot in advance :)

---

### Post by HappyFeet on 2009-12-05
There's usually a switch on the laptop to turn wireless on, and sometimes a Fn+key to control wireless. Have you checked those things?

---

### Post by IcarusR on 2009-12-05
8172 is your wireless card.

This thread @ novatech forum explains howto install driver from Realtek. 
They talk about 8192Se, but from reading elsewhere this driver works for 8172 as well.

Read post 1 through carefully as it also describes stuff for wired network as well. Ignore the ndiswrapper stuff.

You need to do no 2, then jump to no 5 & 'follow the yellow brick road'
There also should be a readme file in the driver tarball.

Any probs post back here.

[http://forum.novatech.co.uk/showthread.php?p=197789]("http://forum.novatech.co.uk/showthread.php?p=197789")

---

### Post by Gazhole on 2009-12-05
> **HappyFeet said:**
> There's usually a switch on the laptop to turn wireless on, and sometimes a Fn+key to control wireless. Have you checked those things?

Yeah, that was my first port of call, i've done stuff like that before and wasted hours, haha :)

---

### Post by Gazhole on 2009-12-05
> **IcarusR said:**
> 8172 is your wireless card.

This thread @ novatech forum explains howto install driver from Realtek. 
They talk about 8192Se, but from reading elsewhere this driver works for 8172 as well.

Read post 1 through carefully as it also describes stuff for wired network as well. Ignore the ndiswrapper stuff.

You need to do no 2, then jump to no 5 & 'follow the yellow brick road'
There also should be a readme file in the driver tarball.

Any probs post back here.

[http://forum.novatech.co.uk/showthread.php?p=197789]("http://forum.novatech.co.uk/showthread.php?p=197789")

Mate you're a legend, that worked like a charm! Currently posting without the need for an ethernet cable.

Thanks a lot, thats fantastic :)

---

