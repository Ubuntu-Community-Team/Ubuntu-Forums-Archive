---
title: "proprietary drivers for radeon r9 270x"
date: 2020-10-06
forum: Hardware
---

### Post by dome78 on 2020-10-06
Hello,
The ubuntu 20.04 open drivers give problems with radeon r9 270x video card. I searched for proprietary drivers on the amd site and the newest ones don't support my card (I also tried to install them without success). 
The last ones that support it date back to 2015 and support up to ubuntu 15. Can I install them? I have seen guides for installing these with ubuntu 16.04: with 20.04 I will risk something?
I also tried the oibaf / graphics-drivers, which works well, but are testing / unstable drivers, right? Or are the oibafs reliable?
Thank you

---

### Post by Yellow Pasque on 2020-10-06
> **dome78 said:**
> The last ones that support it date back to 2015 and support up to ubuntu 15. Can I install them? I have seen guides for installing these with ubuntu 16.04: with 20.04 I will risk something?

No. DO NOT try to install fglrx/Catalyst/Crimson on Ubuntu 20.04. It will not work (Xserver version is too new). 

If oibaf works for you, then use it. Perhaps you can switch to Ubuntu's 20.04.2 kernel/X/mesa HWE stack when Canonicall rolls that out, if you don't want to update so frequently.

---

### Post by dome78 on 2020-10-07
Thanks. I will risk something with oibaf? I don't want to wait for 20.04.2 (early 2021).

---

### Post by CelticWarrior on 2020-10-07
You can try (almost) risk free if you previously install 'ppa-purge'.
If it doesn't work then use ppa-purge against the Oibaf PPA and it should 1) get back everything installed from the PPA to their original versions and 2) remove the PPA.

---

### Post by dome78 on 2020-10-07
Ok thanks

---

