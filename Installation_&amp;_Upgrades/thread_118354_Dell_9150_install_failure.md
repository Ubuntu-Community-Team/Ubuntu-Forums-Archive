---
title: "Dell 9150 install failure"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by waldick on 2006-01-16
i tried to install 5.10 on a Dell 9150, 3.2Mhz, 512Meg, 160 GigHd, on-board nic...for some reason it does not detect the on-board nic card, instead if finds a firewire card, whch it gives me the option of configuring as a nic...i even installed a pci nic card, disabled the on=board one, and it still did not find the pci nic card....if i install without netwok support, it hangs on boot at the "check battery state" entry...if i by-pass with Ctrl-F6, ican get to the prompt, but when i try to start x, i get all kinds of error messages...

any ideas...


thanks,

j

---

### Post by Sef on 2006-01-16
What error messages are you getting? If you could post them, it could help us to diagnose your problem.

---

### Post by LarsBjerregaard on 2006-10-23
I have the same machine and ran into the exact same problem when I installed Breezy. If it's any comfort it's solved in Dapper :-)

Ok, now onto the solution. As is mostly the case other people have had your problem, and have solved it, and this is no exception. The problem is that the e1000 (Intel gigabit) driver that comes with breezy is broken - it doesn't work. I found the solution here: [http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/]("http://blog.dataloss.nl/perma/ubuntu-510-breezy-on-dell-dimension-9150/")

You download the e1000.ko file from the link, and then you open a terminal and run the following commands:

1) cd /lib/modules/2.6.12-9-386/kernel/drivers/net/e1000
2) sudo mv e1000.ko e1000.ko.broken
3) sudo cp <path-to-where-you-downloaded>/e1000.ko ./

That's it! Reboot and enjoy the wild wild Internet... ;-)

---

