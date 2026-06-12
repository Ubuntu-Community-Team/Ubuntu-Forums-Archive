---
title: "Cannot Shutdown!!!!"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by leslie on 2005-07-28
Cannot shutdown!

Ubuntu works great on my laptop install reasonably well and after removing the batstat-applet-2 everything works like a dream. 

Expect when it comes to shutting the thing down!!! When I choose system -> log off -> shutdown or log off and shutdown from the login screen the process always hangs.

System ouput is as follows:

---
System is shutting down, please wait 
---

* Switching to run level: 0
* Sending processes the TERM signal
* Stopping GNOME Display Manager…
* GNOME Display manager not running                    [ok]
* Stopping periodic command scheduler…                [fail]
* Stopping Common Unix Printing System: cupsd     [ok]
* Disabling Power Management…


That’s it! It just hangs with a flashing cursor.

Why does “Stopping periodic command scheduler…” fail and why does it just hang when trying to “Disabling Power Management…”

 I just have to remove the battery from the laptop to turn the dam thing off. 

Any help will be greatly appreciated.

---

### Post by ubuntu_demon on 2005-07-28
try $modprobe apm and/or $modprobe acpi before shutting down

If that doesn't work search the forums. There are multiple threads about shutting down.

Please don't post multiple copies of your thread. Be a little patient.

---

### Post by luca_linux on 2005-07-28
Also try to pass "nolapic" as kernel parameter at boot.

---

