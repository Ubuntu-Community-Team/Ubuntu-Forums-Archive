---
title: "Where do I put SUSPEND_MODULES in Meerkat"
date: 2010-10-09
forum: Hardware
---

### Post by scarleo on 2010-10-09
Hi, I have a config file in /etc/pm/config.d that I made for Lucid to suspend/resume my network in a nice way, with SUSPEND_MODULES. It doesn't seem to have any effect after updating to 10.10 MaverickMeerkat. I guess something changed (again!) where is that configuration supposed to go now?

It's a x86_64, Ubuntu generic if that matters, updated today to 10.10

---

### Post by scarleo on 2010-10-10
Maybe I should rephrase my question:

I am using ath5k driver and my NIC wouldn't resume properly (stone dead) after a RAM sleep . I found out that if I unloaded some modules at suspend, ath ath5k, it would resume properly and let me connect. I entered these modules in a new file /etc/pm/config.d/config and also in /etc/default/acpi-support SUSPEND_MODULES. After upgrading today to 10.10 MM I cannot resume again, my NIC is stone dead and will only come alive if I shut down my laptop and wait for a couple of minutes. 

So my question is: What has changed that has to do with any of these things above? My configurations seem to have no effect. Thanks in advance.

---

