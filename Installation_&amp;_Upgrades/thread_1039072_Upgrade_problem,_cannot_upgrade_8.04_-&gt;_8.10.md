---
title: "Upgrade problem, cannot upgrade 8.04 -&gt; 8.10"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Sprax on 2009-01-14
After having added "normal releases" under software sources the dist upgrade option appeared in the upgrade menu. However, after installing regular upgrades first and rebooting the system, the distro upgrade option disappeared! Still running 8.04 and not 8.10.

What happened? How do I get the button back? (yup, still set to show normal releases under software sources) Or alternatively, is there some terminal command I can use instead?

---

### Post by wizard10000 on 2009-01-14
> **Sprax said:**
> After having added "normal releases" under software sources the dist upgrade option appeared in the upgrade menu. However, after installing regular upgrades first and rebooting the system, the distro upgrade option disappeared! Still running 8.04 and not 8.10.

What happened? How do I get the button back? (yup, still set to show normal releases under software sources) Or alternatively, is there some terminal command I can use instead?

Here's how you get the button back - hit Alt-F2 and put

update-manager -d

in the box.  You don't need to check "Run in terminal".

Good luck -

---

### Post by rocketaholic on 2009-01-14
I tried the Alt F2 upgrade-manager -d and had no success.  I cannot get the earlier version of Ubuntu 8.4 to even recognize the new CD of 8.10.

Please HELP!!!!!!!!!!!!!!!

---

### Post by Sprax on 2009-01-15
Can't try it out right now unfortunately. Will try as soon as I can, thanks!

---

