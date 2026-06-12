---
title: "Laptop Overheats - Setting processor Power management &gt; Maximum Processor State"
date: 2019-12-23
forum: Hardware
---

### Post by HerzeleidMeister on 2019-12-23
Hello, I have a Lenovo Y40-70 Laptop with 16 GB of Ram. When I was on Windows 10 there was a setting here:

```
*Under 'Processor Power management > Maximum Processor State', set the 'Plugged In' value to 99%*
```

That worked wonders to keep my laptop cool. Is there a way I can replicate this setting using Ubuntu 18.04 LTS 3?

---

### Post by Autodave on 2019-12-24
You may want to take a look at *thinkfan.*  I have no experience with it however.

---

### Post by HerzeleidMeister on 2019-12-27
> **Autodave said:**
> You may want to take a look at *thinkfan.*  I have no experience with it however.

Thanks for the info, but it looks like that is not for my laptop. :(

---

### Post by CatKiller on 2019-12-27
I have no idea which options are available for your particular cpu, but kernel options are exposed through sysfs and you can change them by passing values to the appropriate "file." There are also scripts like those in pm-utils for setting those power management options automatically.

---

### Post by HerzeleidMeister on 2019-12-27
> **CatKiller said:**
> I have no idea which options are available for your particular cpu, but kernel options are exposed through sysfs and you can change them by passing values to the appropriate "file." There are also scripts like those in pm-utils for setting those power management options automatically.

Ok thanks for the info, but that is above my pay grade LOL. Do you know of any GUI interface applications that may allow for this setting.

---

### Post by CatKiller on 2019-12-27
> **HerzeleidMeister said:**
> Do you know of any GUI interface applications that may allow for this setting.
Not in 18.04. 20.04 will get cpupower-gui, which is a more limited version of the cpupower that you already have.

---

### Post by HerzeleidMeister on 2019-12-28
Ok thanks for the info. :) I'm monitoring my temperature with Psenser and so far its fine. I just stop what I'm doing if it gets too hot.

---

### Post by Autodave on 2019-12-28
What temp are you considering "too high"?

---

