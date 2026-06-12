---
title: "dhcdbd: unrequested down ?:3"
date: 2009-10-26
forum: Hardware
---

### Post by Winterhart on 2009-10-26
This is already solved, but I am posting it in case it helps someone else in the future.

On my computer the 12-in-one card reader did not arrive plugged in to the motherboard.  I didn't worry about it for months, but finally decided to see why it wasn't working, and when I discovered it, I plugged it in.

On rebooting, I initially had an internet connection and began a software update.  In the middle of the update my computer seized up and when I rebooted again, eth0 refused to come up.

I saw this in /var/log/syslog:

Oct 26 17:08:51 cleopatra NetworkManager: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 26 17:08:51 cleopatra dhcdbd: Unrequested down ?:3
Oct 26 17:08:51 cleopatra NetworkManager: <info> DHCP daemon state is now 14 (normal exit) for interface eth0
Oct 26 17:08:51 cleopatra ntpdate[6566]: can't find host ntp.ubuntu.com

I tried everything that I read; adding 'irqpoll' to my boot options, resetting my router/modem, changing out network cables.  Turns out, there was a conflict between the card reader and the onboard NIC.  When I unplugged the card reader everything went back to normal.  

:popcorn:

---

