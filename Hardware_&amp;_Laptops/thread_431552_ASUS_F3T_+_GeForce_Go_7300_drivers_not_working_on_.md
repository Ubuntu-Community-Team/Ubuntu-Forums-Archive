---
title: "ASUS F3T + GeForce Go 7300 drivers not working on Kubuntu"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by tme on 2007-05-03
Hlo!

I bought yesterday new laptop pc, Asus F3TC-AP002M (includes Nvidia GeForce Go 7300 Turbocache 256mb).
I installed Windows XP for games, such as Half-Life.
Then I installed Kubuntu 6.10, what i upgraded to 7.04 Feisty.

Operations at this point was succesfully completed.

When I tried to install Nvidia's Linux drivers (from [http://www.nvidia.com)](http://www.nvidia.com)), KDE won't start.
Everything looks perfect so far, Nvidia's logo displays at the screen for ~two seconds when i start X.
Loading enviroment looks also good, but KDE won't start, damn.

I've read from somewhere forum, that its rather better to use 7667-version drives because its the most stable. Well, i've tried the newest, 7667 and about ten other version, without results.

At login screen, i switch to console login.
Then i log in, and again with root privileges.
I switched to runlevel 3, installed that driver, used modprobe and started X.
What's wrong?

Thanks!

---

### Post by nebbe on 2007-09-06
Although ive only been using my new Asus F3Tc for 2days, and using 7.04, i thought using the standard nvidia-glx from synaptics worked alright.

However as usual u might have to add or remove some settings in xorg.conf.

Have a look at this site and read from this guys xorg.conf-file and maybe you can find some helpful things or 2:

[http://personal.inet.fi/koti/vjankala/sf/asus.html](http://personal.inet.fi/koti/vjankala/sf/asus.html)


Good Luck!

---

