---
title: "Application install shutsdown laptop? oO"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by ins on 2006-03-02
Hi all,

I've been having some strange problems with the Ubuntu install recently... well actually since install; but I've only now noticed the severity of it as it happens almost all the time now. When I install a new app through the SPM or through the console (apt-get) it often just shuts down the laptop completely. There is no set point at which it does this; either during download or install; sometimes at 25% of download; sometimes near install completion.

The only notable applications I've installed are Wine; Cedega and the Mozilla updates (FF 1.5.1; TB 1.5). Other than that it's basicly a stock install.

**Specs:**
Brand name: EuroCom
CPU: Intel P4 @ 3.2Gigs (HT)
RAM: 1 Gig
HDD: 100 Gig
GPU: Ati Radeon 9600 Mobility (128Meg)
Ubuntu install: 5.10

Any advise would be greatly appreciated.
Thanks in advance =]

---

### Post by florizs on 2006-03-02
have you looked at you processor temperature? it could be your laptop is overheating.
 type in a shell
less /proce/acpi/thermal_zone/THRM/temperature

---

### Post by ins on 2006-03-02
Yep; checked that... definately not overheating =[

---

### Post by nolodude on 2006-09-04
My friend has this same, odd problem. He's got Athlon desktop machine.

If he issues apt-get update, it takes 2 secs and the machine shuts down instantly.

---

