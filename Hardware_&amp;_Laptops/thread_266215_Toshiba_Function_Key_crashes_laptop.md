---
title: "Toshiba Function Key crashes laptop"
date: 2006-09-27
forum: Hardware &amp; Laptops
---

### Post by illfingaz on 2006-09-27
Hey guys,

I have a Toshiba 2410 running dapper (gnome). I installed fnfxd and the client to control my function keys. My main goal was to use FN-F9 and FN-F8 to toggle the touchpad on/off. I created a .fnfxrc file in my home folder as outlined in the man pages, setting FN-F9 to turn touchpad off and FN-F8 to turn it back on. It worked like a charm with one major problem, whenever I pressed FN-F8, my wireless connection dropped. What's worse is that trying things like 
> ifconfig ath0 down would actually crash my computer.

I thought it might be a problem with the package so I uninstalled it. However, even without the package, FN-F8 disables my wireless and causes the laptop to crash. Is there a way I can find out what is causing this?

---

