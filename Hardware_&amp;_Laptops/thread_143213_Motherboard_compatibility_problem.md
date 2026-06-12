---
title: "Motherboard compatibility problem?"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by mcfoolbert on 2006-03-12
I installed Ubuntu 5.10 on my system last week and so far I have been unable to get it to detect and properly identify my motherboard chipset or my onboard audio.  I also cannot get USB to work and I suspect this is also an issue with ubuntu being unable to detect my mobo chipset.

My system was built from a Shuttle barebones system ([http://global.shuttle.com/Product/Barebone/brb_OverView.asp?B_id=28](http://global.shuttle.com/Product/Barebone/brb_OverView.asp?B_id=28))

The chipset is ATI RS300+IXP150 and the onboard sound is Realtek 650F

Any suggestions as to how I might resolve this issue would be appreciated

---

### Post by knalle on 2006-03-12
i think ubuntu breezy comes with a too old kernel for this particular mobo, you got just to new hardware man! try getting the latest kernel source and compile a new kernel and modules, or try the dapper flight 5

---

### Post by mcfoolbert on 2006-03-12
I believe my kernel is the latest, i updated it this week, guess maybe I'll try Dapper if nobody else has any suggestions.

/cringe @ reloading everything again

---

### Post by bluevoodoo1 on 2006-03-12
[QUOTE=mcfoolbert]I believe my kernel is the latest, i updated it this week/QUOTE]

Which are you using? The 2.6.15.6? 

```
uname -r
```

will tell you your kernel. uname -a will tell you some more info.

---

