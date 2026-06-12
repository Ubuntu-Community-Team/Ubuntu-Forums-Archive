---
title: "Xubuntu upgrade 8.10 -&gt; 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by swordfishRU on 2009-04-25
Hi all!

I've got 64-bit (AMD64) xubuntu 8.10. I've tried to upgrade from 8.10 to 9.04 through Update Manager but I've had no option to upgrade to 9.04. Synaptic manager option "show Normal releases" was checked.

This is a console version of the same commands:

hm@m-art:~$ lsb_release -d
Description:	Ubuntu 8.10
hm@m-art:~$ do-release-upgrade 
Checking for a new ubuntu release
No new release found
hm@m-art:~$ do-release-upgrade -d
Checking for a new ubuntu release
No new release found
hm@m-art:~$ do-release-upgrade -p
Checking for a new ubuntu release
No new release found
hm@m-art:~$ wtf?

Thank you.

Regards, SwordFish.

---

### Post by snowpine on 2009-04-25
Have you tried 'sudo apt-get update' to recharge your package lists?

---

### Post by swordfishRU on 2009-04-26
yes, of course:

hm@m-art:~$ lsb_release -d
Description:	Ubuntu 8.10
hm@m-art:~$ sudo apt-get update
....[cutted]....
hm@m-art:~$ do-release-upgrade 
Checking for a new ubuntu release
No new release found
hm@m-art:~$ do-release-upgrade -d
Checking for a new ubuntu release
No new release found
hm@m-art:~$ do-release-upgrade -p
Checking for a new ubuntu release
No new release found
hm@m-art:~$ wtf?

Upgrade Manager doesn't show new release too ;(

---

### Post by snowpine on 2009-04-26
You need a 'sudo' at the beginning of each line. You can't upgrade the system without super user privileges.

---

### Post by swordfishRU on 2009-04-26
ok, with sudo:

hm@m-art:~$ sudo do-release-upgrade
[sudo] password for hm: 
Checking for a new ubuntu release
No new release found
hm@m-art:~$ sudo do-release-upgrade -d
Checking for a new ubuntu release
No new release found
hm@m-art:~$ sudo do-release-upgrade -p
Checking for a new ubuntu release
No new release found

p.s.
upgrade 8.04 -> 8.10 through Update Manager was fine.

---

### Post by swordfishRU on 2009-04-27
up

---

### Post by swordfishRU on 2009-04-27
Hi all!

A trouble was in update-manager package by infraresource.
#dpkg -l | grep infra6
ii  update-manager 2:0.93.34infra6 
ii  update-manager-core 2:0.93.34infra6

If you've got this packages you can't see new release.
The problem is actual for russian users only.

You can find a solution here:
[http://forum.ubuntu.ru/index.php?topic=55327.30](http://forum.ubuntu.ru/index.php?topic=55327.30)

---

