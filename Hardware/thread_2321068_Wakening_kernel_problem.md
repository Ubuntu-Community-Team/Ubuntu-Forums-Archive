---
title: "Wakening kernel problem"
date: 2016-04-20
forum: Hardware
---

### Post by romiras-users on 2016-04-20
I experience issue with wakening PC: after I press a key (usually Ctrl or Space), a hardware turns on then **stuck** so _no keyboard an no mouse movement possible_. Usually I suspend PC but yesterday it left turned on, with same result. I have to perform cold restart to PC every time it stuck.

PC responds to opening SSH connections but keyboard and mouse are unresponsive. When I reboot remotely via SSH, then graphic system stuck too and system stops respond totally, even via network. See log below.

Parameters of system:
Ubuntu 14.04 LTS

Attached devices:
Microsoft Wireless Keyboard 3000 v2.0 (including wireless mouse)
Web-camera Logitech E3500

I have this issue on both kernels: 3.13 (trusty - now) and 3.16 (utopic).

```
Linux romiras-desktop 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:41 UTC 2016 i686 i686 i686 GNU/Linux
```

Here is snippet from /var/log/kern.log (interesting part starts at Apr 20 10:05:28):
[http://pastie.org/10804953](http://pastie.org/10804953)

What should cause this issue: hardware problem or bug in kernel?

---

### Post by romiras-users on 2016-04-20
Not sure, may be this bug relates somehow to issue described above: [khubd/usbhid deadlock(?) creates processes in state D]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1557172")

---

### Post by romiras-users on 2016-04-22
I believe I found the failing component: when I disconnected USB hub [*Eutuxia EL-UDON-77151*]("https://www.google.com/search?name=f&hl=en&q=Eutuxia+EL-UDON-77151") , all related problems disappeared!

---

