---
title: "battery (not dead) not detected"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by iimess on 2005-10-14
In hoary only the battery remaining time didn't show; just upgraded to breezy and now the applet doesn't detect the battery.

I can run without AC plugged.


(Toshiba Satellite M35X-S329)

---

### Post by grinias on 2005-10-14
See this 

[https://wiki.ubuntu.com/ACPIBattery]("https://wiki.ubuntu.com/ACPIBattery")

I hope it helps

---

### Post by iimess on 2005-10-14
[http://acpi.sourceforge.net/dsdt/view.php?manufacturer=Toshiba](http://acpi.sourceforge.net/dsdt/view.php?manufacturer=Toshiba)
doesn't have my model, will read further once I got home.

(But in Hoary it could detect my battery %, just not remaining time. So I suppose my DSDT was OK? Does Breezy use a different way to check battery?)

---

### Post by soro2005 on 2005-10-15
I had that problem, or a similar one, on a Toshiba Satellite M35X-S349. Battery wouldn't be recognized after upgrade to Breezy. In the end, the BIOS update did it for me. Now, it seems to be working like a charm, at least with the battery, only "No support for device type: thermal". Is that a problem? The vent spins up and down, sounds pretty normal.

---

