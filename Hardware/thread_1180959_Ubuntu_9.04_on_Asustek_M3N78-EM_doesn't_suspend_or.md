---
title: "Ubuntu 9.04 on Asustek M3N78-EM doesn't suspend or hybernate"
date: 2009-06-07
forum: Hardware
---

### Post by Rick01 on 2009-06-07
I just build my new pc on a Asustek M3N78-Em I installed Jaunty i386  on it. Everything seems to work fine, but the suspend and hybernation mode. In both mode the pc just switch off. Is not possible to wake up by ps/2 events even if is setted in the bios. The only yhing to do is to press the power button once get a black blank screen and do a reset. What's your experience?

---

### Post by ruben106 on 2009-06-08
Follow this :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/354462](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/354462)

---

### Post by ruben106 on 2009-06-08
Follow this :

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/354462](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/354462)

---

### Post by Rick01 on 2009-06-09
Thanks for the link!
It works now, but it wakes up only only from the power switch.
Ps2 wake up events is active in bios, I checked with windows7 and works. Anyway we almost there!:)

---

