---
title: "Raid partitions not found during installation"
date: 2005-04-02
forum: Hardware &amp; Laptops
---

### Post by octothorpe on 2005-04-02
trying to install to my laptop.  works great till i get to my hd config.  i have a raid 0 config.  yes a raid in a laptop, anyway i have partitions set up but it doesnt seem to find them, can anyone help?

---

### Post by Juergen on 2005-04-04
You probably have a controller that needs a 'driver' module. 
So IMHO you'll have a chicken-eg problem: to boot, the driver needs to be already loaded... (and the installer also probably doesn't load this module)

But since a module-driven raid is a software-raid essencially, you could use the linux raid as well.

A HOWTO for raid 1 is here:
[http://www.tldp.org/HOWTO/Boot+Root+Raid+LILO-8.html](http://www.tldp.org/HOWTO/Boot+Root+Raid+LILO-8.html)

Maybe you can get this to work with raid0 (although I believe you'd have to have kernel and driver in one stripe for this). 

I'd probably use a non-raided /boot partition at least.

---

