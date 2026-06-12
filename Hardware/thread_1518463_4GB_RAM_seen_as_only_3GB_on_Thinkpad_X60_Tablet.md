---
title: "4GB RAM seen as only 3GB on Thinkpad X60 Tablet"
date: 2010-06-26
forum: Hardware
---

### Post by buntumaddy on 2010-06-26
Hardware is Thinkpad X60 Tablet. Recently upgraded the RAM from 2GB to 4GB and also upgraded the HDD. Therefore, I have fresh install of Lucid on a fresh new HDD. RAM was installed prior to commencing ubuntu installation, so the installer had 4GB available.

Edit: Processor details, Intel Centrino Duo, L2400, Dual 1.66GHz core, 32 bit.

PAE kernel did not get installed automatically. Installed it from SPM manually. Rebooted. Lucid still sees only 2.9 GB RAM

```

$ uname -a
Linux xxxxxx 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux


$ free -m
             total       used       free     shared    buffers     cached
Mem:          3014        854       2160          0         76        450
-/+ buffers/cache:        327       2687
Swap:            0          0          0

```

When the laptop had 2GB RAM, gnome system monitor showed 2GBs, so I was hoping to see 4GB after adding the new RAM modules, which also includes the RAM allocated to shared Intel graphics.

BIOS shows full 4096MB memory available, so I am pretty sure none of the modules are faulty.

O, and the laptop is plugged in, turned on, I see ubuntu on the screen :).

Any pointers guys?

---

### Post by jflaker on 2010-06-26
32 bit OS's can only address 3GB of RAM

If you want to get the rest, you need to go with the 64 bit version.

---

### Post by cascade9 on 2010-06-26
> **jflaker said:**
> 32 bit OS's can only address 3GB of RAM

If you want to get the rest, you need to go with the 64 bit version.

With PAE, the 3GB barrier isnt there. 

All I can think of is that your motherboard isnt PAE capable, but that doesnt seem right :|

---

### Post by buntumaddy on 2010-06-26
Oh well! I was hoping that the pae kernel would let me address that extra GB of RAM.

BTW, the I have the 1.66GHz Centrino Duo processor, which is a dual core 32 bit processor. I guess I will not be able to install amd64 ubuntu on my laptop then, will I?

---

### Post by buntumaddy on 2010-06-26
> **cascade9 said:**
> With PAE, the 3GB barrier isnt there. 

All I can think of is that your motherboard isnt PAE capable, but that doesnt seem right :|

How do I check?

Well, BIOS shows 4096MB RAM and I checked Lenovo's website and they say that the laptop supports maximum 4GB RAM.

---

### Post by buntumaddy on 2010-07-01
bump. Anyone?

---

### Post by buntumaddy on 2010-07-03
Looks like I'm SOL :(. Should've done little more research before ordering the RAM modules.

[http://forums.lenovo.com/t5/X-Series-Tablet-ThinkPad-Laptops/X60-Tablet-Memory-Question/m-p/23511](http://forums.lenovo.com/t5/X-Series-Tablet-ThinkPad-Laptops/X60-Tablet-Memory-Question/m-p/23511)

[http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/T60p-4gb-but-3-gb-available/td-p/11078](http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/T60p-4gb-but-3-gb-available/td-p/11078)

[http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/Thinkpad-s-and-N100-s-w-945PM-chipset-can-t-address-gt-3G-Ram/m-p/2621](http://forums.lenovo.com/t5/T61-and-prior-T-series-ThinkPad/Thinkpad-s-and-N100-s-w-945PM-chipset-can-t-address-gt-3G-Ram/m-p/2621)

---

### Post by cascade9 on 2010-07-04
Not cool. 

If the chipset will only find 3GB, then the manufacturer shouldnt say '4GB max' even if install 4GB will work. :|

---

### Post by buntumaddy on 2010-07-04
> **cascade9 said:**
> Not cool. 

If the chipset will only find 3GB, then the manufacturer shouldnt say '4GB max' even if install 4GB will work. :|

Tell me about it! It appears to be a problem of integration. BIOS seems to recognize all 4GB RAM, but some other chipset only lets the OS address 3GB. In all honesty, Lenovo should specify 3GB as the limit, that being the weakest link, instead of 4GB :(.

---

