---
title: "Kernel &amp; ACPI"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by Spear on 2005-08-04
Hi !

After i upgraded from Warty to Hoary, with the new 2.6.10 kernel, the sound started to work on my laptop (a HP Pavilion ZV 5000).

But i want to know and find out, if possible, a solution to make it work, with sound, with the 2.6.8.3 kernel, the default delivered with the Warty.

To try, i started the 2.6.8.3 with the " pci=noacpi " parameter.
So, sound works (in fact, noise :) ... it starts with an uninterrupting noise, but i see the little speaker on the desk, and i can lower it ... so let' s say it works :))

So !
The fact the soundcard isn' t loaded seems to come from ACPI. 
II just started to read the ACPI information on it' s sourceforge page, but i don' t really understand yet what more it brings and how it works (and more, if it' s so necessary or if most can just remove it), but i' m just reading the beginning  :grin: 

Remaining with a 2.6.8 kernel :
Can one just upgrade that program/module (i guess ACPI is a module) with the same kernel ?
Is it just a matter of configuration (if it can be configured) and, if so, how does one configure the ACPI ?
Is there just no other solution than upgrading to a newer kernel (or maybe patching with the 2.6.10 patch the existing one ?) ?

Thanks !

---

### Post by scoon on 2005-08-04
Hey there, 

With each new kernel, things that didn't work well start to.  As far as using an older kernel, I'd read the change log for the new kernel and see what is different in the new kerne from the old kernel.  Finding those differences will prolly make doing what you want a bit easier. 

regards, 

scoon

---

### Post by nocturn on 2005-08-04
[QUOTE=Spear]Hi !

After i upgraded from Warty to Hoary, with the new 2.6.10 kernel, the sound started to work on my laptop (a HP Pavilion ZV 5000).
[/quote]

Hi

I also own a zv5000 series laptop (zv5474EA).
Just one thing that struck me, why would you want to run Warty on it when Hoary supports it better?

---

### Post by Spear on 2005-08-04
Hi !

Thanks, i' ll check the changelogs, it's a good idea ...

Why do i want to know why the sound (with  the old kernel) doesn' t work ? Maybe that if we all start to look a little why things don' t work well in our linux distribution, instead of waiting for the next upgrade, we' ll be many more who' ll find solutions ;)
It' s interesting to know where things don' t work and how you can fix these !

---

### Post by scoon on 2005-08-04
Hey there, 

Bugzilla's and forums are a great place to start to find out about the broken stuff and a great way to not duplicate efforts. 

regards, 

scoon

---

