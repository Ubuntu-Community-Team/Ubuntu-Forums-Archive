---
title: "permanently add module parameter for ixgbe"
date: 2014-06-18
forum: Hardware
---

### Post by fransfrans on 2014-06-18
Hello,

I am using a 10 Gb Intel ethernet card (ixgbe) with an unsupported sfp+ module.
For this I need to add the parameter allow_unsupported_sfp=1.
This works:
sudo rmmod ixgbe
sudo modprobe ixgbe allow_unsupported_sfp=1

How do I make this permanently?
I have tried to put the line in /etc/modules, but it doesn't do the job.

Thanks

---

