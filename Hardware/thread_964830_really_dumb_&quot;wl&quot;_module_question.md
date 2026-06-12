---
title: "really dumb &quot;wl&quot; module question"
date: 2008-10-31
forum: Hardware
---

### Post by frogotronic on 2008-10-31
Hi,

I'm running Hardy Heron (8.04.1) and am using the ndiswrapper for my wireless and it works really well.

If I look at my SYSTEM>Hardware Drivers output, it lists a "wl" module.  After checking the forums, I find that this is actually a broadcom module for my wireless card.  I don't have "wl" listed in /etc/modules, so I'm assuming that its there , but not "loaded".

Q:  If I'm using ndiswrapper, can I blacklist and uninstall the wl module?

Q2:  How do I uninstall it, seeing as I never explicitly installed it?

Thanks,
CH

---

### Post by Ayuthia on 2008-10-31
> **cement_head said:**
> Hi,

I'm running Hardy Heron (8.04.1) and am using the ndiswrapper for my wireless and it works really well.

If I look at my SYSTEM>Hardware Drivers output, it lists a "wl" module.  After checking the forums, I find that this is actually a broadcom module for my wireless card.  I don't have "wl" listed in /etc/modules, so I'm assuming that its there , but not "loaded".

Q:  If I'm using ndiswrapper, can I blacklist and uninstall the wl module?

Q2:  How do I uninstall it, seeing as I never explicitly installed it?

Thanks,
CH
You just need to blacklist the wl module and that should be all that you need to do.  The wl module comes packaged in linux-restricted-modules so it comes with Ubunttu.  I am not for sure if there is an easy way to uninstall the module.

---

### Post by frogotronic on 2008-10-31
> **Ayuthia said:**
> You just need to blacklist the wl module and that should be all that you need to do.  The wl module comes packaged in linux-restricted-modules so it comes with Ubunttu.  I am not for sure if there is an easy way to uninstall the module.

Thanks, will do.

-CH


:guitar:

---

### Post by mempman on 2008-10-31
I was using ndiswrapper to use my laptop's wifi card, BroadCom 4311 (r02).  A soon as the wl driver became available, I started using it. Ndiswrapper is a marvellous tool, don't get me wrong, but I prefer to use the restricted driver "wl" because wl is probably a better/faster way to get connected.

---

