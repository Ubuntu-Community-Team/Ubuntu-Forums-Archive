---
title: "Fan problem with Fujitsu LifeStyle S760 Laptop"
date: 2010-04-29
forum: Hardware
---

### Post by nicolargo on 2010-04-29
Hi all,

i have install Ubuntu 10.04 on my new Laptop (Fujitsu LifeStyle S760). Every think work "out-of-the-box" except the fan... It start working every minute and top after 30 secondes: noise and bad autonomy.

I firts try to have a look on the temperature sensors but unfortunately, i did not success:

```

$ sudo sensors-detect
Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS

$ acpitool
...
Thermal info: <not available>
```The /etc/init.d/fancontrol is not running and do not want to start...

```

$ sudo /etc/init.d/fancontrol status
* fancontrol is not running$ sudo /etc/init.d/fancontrol start
$ sudo /etc/init.d/fancontrol status
* fancontrol is not running

$ sudo pwmconfig
... No sensors found! (modprobe sensor modules?)
```Any idea to solve this issue ?

---

### Post by nicolargo on 2010-05-26
Please up...

---

### Post by nicolargo on 2010-11-20
Hi Gilles,

i have open a bug on the Ubuntu track:

[https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/572173](https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/572173)

Please feel free to add your feedback.

I also try to upgrade the BIOS of the LifeStyle S760 to the latest version... did not solve this issue...

---

