---
title: "Quick tutorial - Turn off aggressive HD power management"
date: 2011-04-09
forum: Hardware
---

### Post by wieman01 on 2011-04-09
Hi, 

One annoying feature of Ubuntu is it's power management can be too aggressive resulting in the hard drive spinning up & down with an audible clicking noise. This is how you turn it off:

[LIST]
**Open command line.**
[/LIST]
[LIST]
**Issue (and enter root password):**
[/LIST]
> echo 'hdparm -B 255 /dev/sda' | sudo tee -a /etc/hdparm.conf

[LIST]
**Reboot.**
[/LIST]

That's it. I hope this helps some of you out there.

---

