---
title: "Slow boot, pause on init-bottom, maybe AHCI related"
date: 2011-12-09
forum: Hardware
---

### Post by dwigyit on 2011-12-09
Hiya :)

I have an MSI GX660R laptop running Ubuntu 11.10. It boots (significantly) and loads applications (noticeably) slower than three-year-old entry level laptops running the same OS and I was trying to find out why. I disabled graphical boot and found that it spends at least ten seconds running scripts/init-bottom - throughout most of which there is no HDD activity.

 I looked it up here and someone with the same problem said that switching from AHCI to compatibility-mode in BIOS sped up their whole system by a huge amount, but my BIOS has no compatibility mode option (tried IDE and it's the same as AHCI). I was wondering if anyone could offer me any other advice as to what to try? It's dual-booted with Windows 7 which shows no performance problems during boot.

---

### Post by dwigyit on 2011-12-12
My laptop takes over 40 seconds to boot whilst my auntie's three year old mobile centrino laptop takes less that 30 (same OS). I just don't see why that could happen unless something was going a bit wrong during my boot sequence?

---

### Post by JRV on 2011-12-12
Is it slow to boot, or slow to POST?
My laptop can boot to the login screen in less time than it takes my desktop to POST.

---

### Post by dwigyit on 2011-12-12
No - the little less than fourty seconds is to the login screen, from there its usually less than 5 seconds to Gnome shell or Unity.

---

### Post by dwigyit on 2011-12-13
-edit- posted on wrong topic so ignore this <<<

---

### Post by dwigyit on 2011-12-17
I just did another non-graphical boot and recorded that the longest processes were running scripts/init-bottom which takes about ten seconds and there was also a really long gap after something to do with USB HID core driver. It says done after it and a new line with a blinking cursor just stays there for probably more than ten seconds. There's also a brief pause with something like "failed to get i915 symbols, graphics turbo disabled", but I've read around and I don't think that last one's too serious.

I noticed also that everything using the HDD is quite slow - loading firefox takes a good few seconds when loaded for the first time and other programs take a similar amount of time.

---

### Post by dwigyit on 2011-12-19
Wow I'm double posting a lot... anyway I think it's justified in this case...

I made a bootchart - hopefully someone here will be able to understand where the problems lie from it :)

[http://img407.imageshack.us/img407/9237/samuelcalpellaplatformo.png](http://img407.imageshack.us/img407/9237/samuelcalpellaplatformo.png)

---

