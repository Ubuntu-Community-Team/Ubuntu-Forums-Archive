---
title: "no plug-n-play/cpuscaling"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by robostang 548 on 2007-09-14
I’m having a bit of a problem with ubuntu.  I just loaded it onto my new Compaq presario F572US.  I had to add noapic (advanced programmable interrupt controller) to my menu.lst file to get it to work but now its up and working great.  After installing I noticed that something was wrong with my plug-n-play.  If I pluged in my flash disk a few minutes after login, it worked just fine.  But if I worked in firefox or open office for a while I wouldn’t get anything after plugging it in.  I browsed the forums for people with the same notebook as me.  One post said to put pnpbios=off to my menu.lst file.  I did that but the problem was exactly the same.  Then I tried adding "irqpoll pnpbios=off" and the problem was solved.  The only problem was that irqpoll somehow disabled my cpu frequency scaling.  Before I added irqpoll my cpu speed would go to 800 mhz when I was on batery and 1.7 ghz when I was on AC power but with the irqpoll I go between battery and AC and the cpu frequency doesn’t change.  Is there a way to get my usb plug-n-play working without compromising my cpu frequency scaling?

---

