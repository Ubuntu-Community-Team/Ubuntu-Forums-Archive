---
title: "Proliant1600 hang on reboot"
date: 2005-03-17
forum: Hardware &amp; Laptops
---

### Post by MatsS on 2005-03-17
I have problem with Ubuntu and my Proliant 1600, it hang on reboot.
Everything work perfect until I doing  “shutdown –r” or “reboot” , machine going down and stopping every service, umounting filesystem  sending term, kill signal and last saying  “rebooting” and there it stays for ever.
I have tried a tips from another debian-forum where they have found out that “cpqphp” was the reason and just do an “rmmod” on it and put it on the blacklist and that should do the trick! 
At my office one of the new proliant server running debian and had same problem, there it solved the problem.
In my server at home I have Ubuntu and it seams that “cpqphp” is not loaded and it doesn’t matter if I put it on the blacklist, my server continues to hang on reboot? What to do?

/Mats

---

### Post by MatsS on 2005-03-19
I solved the problem..
I track the problem to the hotplug/pci.rc and i don’t know how to fix that for now, so I load “tlan” and other modules from /etc/modules insted and skiping the hotplug..

/Mats

---

