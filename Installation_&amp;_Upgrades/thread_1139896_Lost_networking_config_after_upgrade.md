---
title: "Lost networking config after upgrade"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by markjreed on 2009-04-27
After upgrading from 8.10 to 9.04, my system now boots up as 'localhost.localdomain' and with no IP address.  

/etc/hostname and /etc/network/interfaces both look correct, i.e. they didn't change across the upgrade, so something else is amiss.  

The hostname is in /etc/hosts.  

If I manually run /etc/init.d/hostname.sh, it sets the hostname correctly.  That script is linked properly into /etc/rcS.d/, but doesn't appear to be getting executed.  

I see that dhclient3 is running, but it's not configuring the interface.  If I kill and restart it, it works.  (Even with the hostname left at localhost, so that's not interfering.)

Any suggestions on what to look at welcome.  Obviously I can get things functional manually, but I'd like to figure out how to fix the bootup config.

---

