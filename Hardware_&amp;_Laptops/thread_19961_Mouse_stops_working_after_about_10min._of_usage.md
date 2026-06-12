---
title: "Mouse stops working after about 10min. of usage"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by johnnymokes on 2005-03-14
[COLOR=**Blue]Mouse stops working after about 10min. of usage**[/COLOR]

After a fresh install of Ubuntu last night, my Logitech MX1000 (wireless) mouse works, but stops working after about 10 minutes of usage.  Being new to any Linux distro, I do not know any keyboard shortcut/commands to power down my system, so I am manually doing it.

After restarting my system, my mouse will work again - but stop working again after about 10 minutes.  Has anybody else experienced this?  During the install, I was never prompted to manually detect my mouse, so I don't know if there is an incorrect mouse configuration or anything of that nature.

Due to my inexperience w/ Linux - any help is highly appreciated!!

John

---

### Post by alastair on 2005-03-14
Log in, and the mouse is working.

Open a shell (terminal) and leave it open - run in the shell :

sudo tail -f /var/log/syslog

Hit enter a few times - then let the shell sit there as you work away. This shell will "tail" the system log and let you see every message printed in the log as it happens.

When the mouse stops working - see if anything strange is written in the shell from the kernel.

Remember - you can switch windows using ALT-TAB usually (like NT).

---

