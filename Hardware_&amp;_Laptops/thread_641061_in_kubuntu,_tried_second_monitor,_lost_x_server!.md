---
title: "in kubuntu, tried second monitor, lost x server!"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by code-breaker on 2007-12-14
Running kubuntu feisty. Decided to dig out my older 19" for a second monitor. Plugged it in, and in kubuntu system settings, checked 'second monitor' box. Selected 'dual screen'. It said I must restart x-server. OK, do that. But now I have no x-server, only a command prompt! 

How do I get my desktop back again?! Please help!

---

### Post by code-breaker on 2007-12-15
Sorry, but...bump.

I'm a little desperate. Anyone?

---

### Post by code-breaker on 2007-12-16
Well, I was lucky. I had just previously installed a new HD, and hadn't gotten around to wiping the old one yet. So I attached the old one again, logged in, and copied down the relevant sections of xorg.conf. Then rebooted into the new install, and from the command line, I edited xorg.conf to look like the old version, and it worked! I got lucky.

---

### Post by code-breaker on 2008-01-01
Follow up...I recently installed the nvidia restricted drivers without a problem, so I thought I'd try the dual monitor setup again. This time, it worked like a charm. 

And yes, I know I should have backed up xorg.conf the first time around. It was an impulse decision and I learned my lesson! :)

---

