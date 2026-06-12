---
title: "power setting with iwl3945 and lucid totally broken"
date: 2010-04-24
forum: Hardware
---

### Post by Axx83 on 2010-04-24
Hi guys. Since Karmic kernel I can't set iwl3945 power anymore

/sys/bus/pci/drivers/iwl3945/0000\:??\:00.0/power_level
does not exist anymore

iwconfig wlan0 power on
gives me
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

Do you know how to set the power of this wifi driver ?

thanks

---

### Post by Axx83 on 2010-04-29
I'm bumping the thread since lucid has just come out

---

### Post by mweinelt on 2010-05-06
and what you meant to say was that it is still broken:

```
$ sudo iwconfig wlan1 power on
[sudo] password for martin: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan1 ; Operation not supported.
```

I think we should open a Launchpad Bug in case this has ever worked. I really don't have a clue, but I suppose the iwl3945 _should_ have powersaving.

---

### Post by ShadowDragon on 2010-05-13
Powersaving has been disabled for iwl3945 since it was creating access-point association issues.

Kernel 2.6.32.y commit: [iwl3945: disable power save](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.32.y.git;a=commit;h=66c9e44e5740fe9024e3ed02fd66ad6e0e57408f)

---

### Post by Axx83 on 2010-05-14
that clarifies everything. thank you a lot

---

