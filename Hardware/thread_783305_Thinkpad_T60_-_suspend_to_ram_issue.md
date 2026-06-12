---
title: "Thinkpad T60 - suspend to ram issue"
date: 2008-05-05
forum: Hardware
---

### Post by gemidjy on 2008-05-05
Hello, I am using the default, pm-suspend way to suspend my Thinkpad T60 to RAM. Hibernation (suspend to disk) works fine with uswsusp. After I enabled the tp_smapi module (loaded it together with hdaps-ec and thinkpad-ec), I am getting strange situation.

after I come back from Suspend to RAM, one of the Cores of the laptop (Intel CoreDuo (CentrinoDuo)) is hotter than the other...

```
     Thermal 1: ok, 47.0 degrees C
     Thermal 2: ok, 56.0 degrees C
```

I couldn't figure out how this happens. If I suspend the computer again, the issue might get fixed, or the situation swaps, so that Core1 is the hotter and Core2 is the cooler core :/ 

The hardware specification goes here: [http://gemidjy.info/files/hardwarespecs.html](http://gemidjy.info/files/hardwarespecs.html)
Using: Kubuntu 8.04 (with all updates), with the default kernel (2.6.24-16), manually compiled only tp_smapi-0.32 so that I get HDAPS support.
 
Thanks

---

