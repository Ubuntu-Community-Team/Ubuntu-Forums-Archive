---
title: "Toshiba M35X-S109 HAL Initialization Failure in Xubuntu"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by fader on 2008-02-02
Hi,

I have two Satellite M35X-S107 laptops and recently installed Xubuntu 7.10 on them. I get the error message once xubuntu starts: "Failed to initialize HAL"

I believe this has to do with ACPI because it doesn't come up when the laptops are plugged into AC. In fact, it happens only after I've done restarted the computer. On a cold start, HAL works fine. It's really weird.

Anyways, not being able to initialize HAL will not let me shutdown the machines (grayed out). The first time it actually asks for a password to shutdown the computer, but after that the logout menu shutdown and reboot buttons gray out.

From what I can tell, none of this occurs when it's running on AC. The problem only arises when on battery. 

I've tried the trick to rename S12 to S13 for the HAL scripts so that they run after DBUS, but that was to no avail. I've also tried CONCURRENCY=none and CONCURRENCY=shell in the file /etc/init.d/rc 

If some could figure out what to do, that would be great. I just want to be able to shutdown the machine, so I can sleep at night.

Thanks

---

### Post by fader on 2008-02-02
bump

---

### Post by fader on 2008-02-03
bump bump

---

### Post by fader on 2008-02-04
bump bump bump

---

