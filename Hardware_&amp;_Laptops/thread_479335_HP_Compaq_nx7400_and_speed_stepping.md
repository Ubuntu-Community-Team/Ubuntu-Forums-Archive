---
title: "HP Compaq nx7400 and speed stepping"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by beercz on 2007-06-20
Hello

Apologies if this issue has been raised previously, but I have yet to find a resolution.

Has anyone managed to get speed stepping work on the above laptop?  I have an Intel Centrino Duo processor.

When I run the CPU Frequency Scaling Monitor I get the following message:

> CPU frequency scaling unsupportedWhen I use my laptop on battery my CPU still runs at 100% and I would like it to step down so I can conserve some battery life.

Any pointers anyone?

Thanks

---

### Post by finni on 2007-07-12
Umm, which ubuntu are you running and what is your nx7400 BIOS version? My Core Duo T2400's speed steppings with nx7400 worked nicely out of box with Feisty Fawn, I'm using version 6 bios ( or was it 0.6).

---

### Post by beercz on 2007-07-12
> **finni said:**
> Umm, which ubuntu are you running and what is your nx7400 BIOS version? My Core Duo T2400's speed steppings with nx7400 worked nicely out of box with 
Feisty Fawn, I'm using version 6 bios ( or was it 0.6).
Hi

Thanks for the response.

I'm running Feisty and my BIOS is version is F.08.

I can manually step down using the CPU Frequency Monitor applet.

---

### Post by finni on 2007-07-12
> **beercz said:**
> Hi

Thanks for the response.

I'm running Feisty and my BIOS is version is F.08.

I can manually step down using the CPU Frequency Monitor applet.

I had originally F.07 and I downgraded to F.06, this was when the speedstepping started working with Dapper Drake. Downgrade at your own risk.

EDIT: CPU steppings works automatically on my end.

---

