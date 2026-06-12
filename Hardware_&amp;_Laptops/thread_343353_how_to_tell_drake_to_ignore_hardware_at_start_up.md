---
title: "how to tell drake to ignore hardware at start up"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by popformula on 2007-01-21
hi,

i posted in the networking / wireless about a problem with a pci wireless card, but i haven't had a satisfactory response yet.

the os fails to start if the card is in, and boots up normally without it.

so in the meanwhile, its there a way to tell ubuntu to ignore a particular pci card during startup, so i don't have to open my box and physically pull out the network card whenever i want to boot into linux?

thanks!

joe

---

### Post by lswb on 2007-01-21
Does the card work with other OS? How far into boot does the system go when the card is installed?
Can you go back through your /var/log/syslog and find some error messages related to the boot failure?

---

### Post by popformula on 2007-01-21
card works perfectly in windows (it's what i'm using now). see this thread for full details of the problem: [http://www.ubuntuforums.org/showthread.php?p=2042415](http://www.ubuntuforums.org/showthread.php?p=2042415)

thanks!

---

