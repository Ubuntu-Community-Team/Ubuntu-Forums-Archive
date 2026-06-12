---
title: "Does new motherboard = fresh install?"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by graabein on 2005-09-08
Hi, I managed to break my motherboard last week. I think dimm slot #1 is broken so the damn thing won't start. 

If I buy a new motherboard do I have to reinstall Ubuntu and loose all my settings and data? Or will it boot like it used to? I have not tinkered with the kernel or anything like that.

I know I can probably reach my data with a live CD to back them up but...

---

### Post by MrCheese on 2005-09-08
[QUOTE=graabein]Hi, I managed to break my motherboard last week. I think dimm slot #1 is broken so the damn thing won't start. 

If I buy a new motherboard do I have to reinstall Ubuntu and loose all my settings and data? Or will it boot like it used to? I have not tinkered with the kernel or anything like that.

I know I can probably reach my data with a live CD to back them up but...[/QUOTE]

Probably not - thanks to the kernel's module system it should detect & set up all your hardware automatically. Your only problem will be if you use an onboard winmodem. I presume your graphics card is still the same so X should still play.

Note - make sure that your disks/cds are hooked up to the same IDE ports as now since the system relies on /etc/fstab to tell it where everything lives, which in turn is defined by the boot loader definitions.

---

### Post by codejunkie on 2005-09-08
[QUOTE=graabein]Hi, I managed to break my motherboard last week. I think dimm slot #1 is broken so the damn thing won't start. 

If I buy a new motherboard do I have to reinstall Ubuntu and loose all my settings and data? Or will it boot like it used to? I have not tinkered with the kernel or anything like that.

I know I can probably reach my data with a live CD to back them up but...[/QUOTE]
just my opinion but i've found that with any os the answer is usually yes you run into so many configuration problems that the fastest and easiest thing to do is reinstall the os when you replace the motherboard but it's worth a shot you never know it just might work.

---

### Post by graabein on 2005-09-08
Maybe this is my chance to do a clean Breezy install and get rid of my Windows partition at the same time!

If I buy a couple huge hard drives along with the new motherboard and later mount my old drives for extracting data and application settings...

How long till October!?!

 ;-)

---

