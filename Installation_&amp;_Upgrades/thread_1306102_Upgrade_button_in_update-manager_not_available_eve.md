---
title: "Upgrade button in update-manager not available even after several checks"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by phillies on 2009-10-30
when I run "update-manager -d" from console there is no option to upgrade ubuntu jaunty to karmic.
Even when I run "sudo update-manager -d --dist-upgrade" it starts the process but then tells me that there are no upgrades available and terminates.

I removed all third party archives, checked that "Release upgrade" is set to "Normal releases" and hit the "check" button several times. Any ideas where this bug hides?

---

### Post by phillw on 2009-10-30
> **phillies said:**
> when I run "update-manager -d" from console there is no option to upgrade ubuntu jaunty to karmic.
Even when I run "sudo update-manager -d --dist-upgrade" it starts the process but then tells me that there are no upgrades available and terminates.

I removed all third party archives, checked that "Release upgrade" is set to "Normal releases" and hit the "check" button several times. Any ideas where this bug hides?


can you paste back what this gives you from terminal

```
uname -a
```

Thanks,

Phill.

---

### Post by symsym on 2009-10-30
Same problem on my adm64.

$ uname -a
Linux symmetry 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

Ups, this is not my problem. I have not upgrade button in update-manager today, after ubuntu 9.10 release. I have installed all updates.

---

### Post by phillies on 2009-11-02
Sorry for the late reply. I found that I can update using alternate installation CD which worked quite nicely.  

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")

Since karmic is running now, uname -a might not help anymore. But it must have been quite similar to the output of symsym, since I had a x86_64 version of the latest jaunty including every update including backports.

---

