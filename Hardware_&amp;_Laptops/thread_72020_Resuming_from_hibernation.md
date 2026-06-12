---
title: "Resuming from hibernation"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by emperon on 2005-10-05
Hello, I have configured my computer so that it hibernates when i close the lid. And works fine.
But i have two things to be solved:

1-) My Wireless network card is being disappeared from from the networking menu, so i have to reboot if i want to use internet through it

2-) There should be a way that i could cancel booting from hibernated memory and boot as a normal way without a 2nd time reboot.

Looking forward for your advices

Onur

---

### Post by JLB on 2005-10-05
try adding the module(s) for your network card to the list of modules that get reloaded after a suspend . you can add thses in /etc/default/acpi-support . 

its worth a shot.

---

