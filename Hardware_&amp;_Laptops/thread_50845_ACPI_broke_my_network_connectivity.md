---
title: "ACPI broke my network connectivity"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by aburda on 2005-07-21
Hello,

      I just moved over to Kubuntu and I think I managed to completely destroy my network connectivity when setting up ACPI.  Here is what I did,  I was trying to setup an icon that would use the /etc/acpi/sleep.sh script from the desktop.  I created my own sleep.sh that did sudo and called sleep.sh.  It would work ok from the command line but when I ran it from the desktop nothing would happen.  I tried different things, probably clicking on the desktop icon a total of 10 times (over about a half an hour) with no response.  Then all of a sudden it kicked in and my system would go to sleep, and then wake up and immediately go back to sleep.  It just kept repeating this so I just pulled the power plug to make it stop as I was getting nervous that this was bad for my hardware after about the 8th awakening.  
       When I rebooted everything was fine except networking.  When I try to configure with ifup or ifdown the command just hangs with a blinking cursor.  Using ifconfig I can assign eth0 an IP address and can ping nearby computer (don't know how to get route going but assume that if I did everything would work fine so long as I do it statically and not with DHCP).  I think the system still thinks its about to go into sleep mode and won't let the network come up and I can't figure out how to get it untangled (except completely reinstalling which isn't the preferred option).  The system also hangs when I reboot and occasionally it would drop into sleep mode halfway through shutting down and then re-awaken, although it only does this sometimes on reboot.

     Any help before I reinstall is appreciated.

              Aaron

---

