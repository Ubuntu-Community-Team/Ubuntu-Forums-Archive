---
title: "Why only 3 GB on 32-bit Ubuntu?"
date: 2012-01-27
forum: Hardware
---

### Post by Azyx on 2012-01-27
I wonder why Ubuntu 32-bit only can address 3GB memory?
2^32=4294967296 and my 4 GB DDR2 should be visable in the system. I do not use my onboard gfx and I have a PCI-E gfx. I also with help of FREEDOS ugraded BIOS on my P6NGM-FD to the later version because the version before did only report 3GB when  you have 4GB RAM.

Another question about upgrade to 64-bit. Are there any significant problem with 64-bit Ubuntu? Can I  upgrade, or do I need to make a new install?

---

### Post by wolfen69 on 2012-01-27
> **Azyx said:**
> I wonder why Ubuntu 32-bit only can address 3GB memory?
32bit OS's can only address 3.2 gb of ram. It is a built in limitation, unless you install the PAE kernel.

> Another question about upgrade to 64-bit. Are there any significant problem with 64-bit Ubuntu? 
The default ubuntu iso will be 64bit starting with 12.04, so no, there are no problems using 64bit these days. And even if you had some exotic piece of hardware that only has a 32bit driver, you can force the driver to be used in 64bit. You should have no problems. I myself have been using 64bit for 2 years with no issues. 

> Can I  upgrade, or do I need to make a new install?
You will need to do a fresh install.

---

### Post by Azyx on 2012-01-27
> **wolfen69 said:**
> 32bit OS's can only address 3.2 gb of ram. It is a built in limitation, unless you install the PAE kernel.

 
The default ubuntu iso will be 64bit starting with 12.04, so no, there are no problems using 64bit these days. And even if you had some exotic piece of hardware that only has a 32bit driver, you can force the driver to be used in 64bit. You should have no problems. I myself have been using 64bit for 2 years with no issues. 


You will need to do a fresh install.

Thanx :)
Think I will try PAE kernel on my 10.04LTS machine...until 12.04 LTS have been stable. 

/Cheers

---

### Post by Azyx on 2012-01-27
My Ubuntu 10.04 LTS was an upgrade from 8.04LTS and I think I upgraded my motherboad, so PEA was not downloaded during install, so I just check that my cpu hade PEA-support and then:


```
sudo aptitude install linux-generic-pae linux-headers-generic-pae
```

And reboot

Worked fine :)

---

