---
title: "Upgraded to 9.04 and broke my system"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by brownwrap on 2009-04-29
I received the message that 'updates were available', I went ahead with the upgrade and then after trying to reboot, the system no longer came up. It stopped for a long time at the Hardware Abstraction Layer, then after it proceeded, I got this error:


Couldn't recognize image:

/usr/share/gdm/themes/Human/bottom_bar.svg

I then booted from a rescue cdrom, disabled the startup of X, but ran into another problem, the network no longer worker. 

I'm at home using DHCP, so I don't have a static address. I did notice in dmesg, it didn't like eth0 and then later on in the file replaced it with eth6.

Now the system is more or less useless after the upgrade.

---

