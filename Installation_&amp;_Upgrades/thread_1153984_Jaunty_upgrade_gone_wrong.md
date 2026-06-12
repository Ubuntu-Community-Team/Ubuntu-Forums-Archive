---
title: "Jaunty upgrade gone wrong"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by frigginacky on 2009-05-09
I tried upgrading from Intrepid to Jaunty last night.  I started the upgrade from the update manager and left it to do its thing (no use watching your computer download files for hours, right?).  When I returned, the upgrade window was nowhere to be seen, and the desktop was frozen.  

I rebooted, and got as far as the login screen.  I had no mouse movement, though the keyboard worked.  Logging in was unsuccessful (no reaction after entering password).  I rebooted in recovery mode and tried running dpkg (didn't help) and apt-get update && apt-get upgrade (doesn't work; can't resolve any of the servers).

Can anyone help me figure out what's gone wrong and how to fix it?  I've had to boot into Vista to post this, and I don't know how much more Windows I can take. ;)

---

### Post by Triptol on 2009-05-09
The easy answer: if you don't have a lot of extra programs installed AND you have your home directory mounted on a second partition, you could start all over again with a new installation. In this case you should wipe out your root partition (format) and reinstall Jaunty. 

If this is not an option the first thing you would need to do is get the machine online again. This can be achieved by playing around with a file called /etc/network/interfaces. This all depends on what kinda of network adapter you have. If you have a normal wired card you should have something like this in that file:

```
auto eth0
iface eth0 inet dhcp
```

If you have wireless things will be harder. 

As soon as you are connected again you can resume with "aptitude update" and "aptitude dist-upgrade" (I prefer aptitude to apt-get), the dist-upgrade is important as well since you are moving from one version of your distribution to the next.

Good luck!

---

### Post by frigginacky on 2009-05-09
Well, I'll be darned!  I went to check my /etc/network/interfaces, and was able to boot up ubuntu normally. Power of posting, I guess. :D  The upgrade is still a half-done mess, but I should be able to fix it now.  Thanks for your help!

---

