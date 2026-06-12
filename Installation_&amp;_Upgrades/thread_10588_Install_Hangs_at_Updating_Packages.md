---
title: "Install Hangs at Updating Packages"
date: 2005-01-09
forum: Installation &amp; Upgrades
---

### Post by SideShowBob on 2005-01-09
Like many others here, I'm pretty new to this so bear with me.

Install proceeds just fine, computer reboots to my new shiny ubuntu linux install, and the configuration proceeds normally, up until the point where I am given the option to configure apt to download from the internet.

I downloads the packages just fine (fetches 77.4MB) then I see:
```
Extracting templates from packages: 100%
Preconfiguring packages ...
``` 

And it just sits there.  Left it at that point from 10 pm to 8 am, no movement.  I tried reinstalling and telling apt to **NOT** use internet, and it hangs at the same point.    I tried both methods (internet/no internet) with ACPI and APIC disabled, still hangs.

Pulling my hair out, because I've installed other GNU/Linux systems on this computer in the past, but for some reason ubuntu just laughs at me. :sad:  :D

---

### Post by SideShowBob on 2005-01-09
Upon further investigation, it turns out this hang-up was caused by a USB mouse.

Is there a reason why that should cause apt-get to hang?

---

### Post by Dangermouse on 2005-04-02
Hi, im having the same issue on my Acer Travelmate 244 Laptop. I removed my USB mouse and Keyboard and still have the same issue. This is without downloading any updates, just the normal install. :(

Edit: I rebooted into the recovery mode and ran base-config manually. I pressed 'g' to installed packages, goes through same procedure, but this time it asks me for my keyboard country code, and its just after i enter that ( i tried 'uk' and 'us') it hangs, so i gather its something to do with the keyboard. :-?

---

