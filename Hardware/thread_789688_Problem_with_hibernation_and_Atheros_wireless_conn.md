---
title: "Problem with hibernation and Atheros wireless connectivity"
date: 2008-05-10
forum: Hardware
---

### Post by Ted_Smith on 2008-05-10
Used Ubuntu on my desktops for years - since Breezy Badger. Eventually pursuaded wife to let me install Ubuntu on her laptop. Installed Hardy Heron on Friday. 

All has gone well except for two things : 

1) Hibernate does not hibernate. It effectively powers off and when it's powered back up it runs through a full boot.

2) Wireless is unreliable and usually requires me to run "/etc/init.d/networking restart" to get it to talk to the router. I have DHCP enabled and I have specified all the correct wireless parameters. It connects after I do the above but often not after a reboot which is no good for the wife when I am not around. 

Both of these are show stoppers and she is calling me to put WindoZe back on it already unless I can get it to reliably hibernate and power back up and reliably connect to the wireless. 

The problem with the wireless is I have the  Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) wireless card which only has a proprietory driver. This may be causing both the hibernate problem and why it's not always reliable following a hibernation effort? 

Can anyone help me before the wife gets WindoZe back on it!!???

Kernel : 2.6.24-17-generic


Thanks

Ted

---

### Post by vyruss on 2008-05-16
> **Ted_Smith said:**
> Used Ubuntu on my desktops for years - since Breezy Badger. Eventually pursuaded wife to let me install Ubuntu on her laptop. Installed Hardy Heron on Friday. 

All has gone well except for two things : 

1) Hibernate does not hibernate. It effectively powers off and when it's powered back up it runs through a full boot.

Are you sure? Hibernation works that way, it looks as if it's booting normally but is much faster. Perhaps your laptop isn't hibernating at all, this usually means you haven't got enough swap for it to work. Make sure your installation's swapfile is twice the size of your physical memory (i.e. for 512 MB ram create a 1024 MB swapfile for your installation).

> 2) Wireless is unreliable and usually requires me to run "/etc/init.d/networking restart" to get it to talk to the router. I have DHCP enabled and I have specified all the correct wireless parameters. It connects after I do the above but often not after a reboot which is no good for the wife when I am not around. 

Both of these are show stoppers and she is calling me to put WindoZe back on it already unless I can get it to reliably hibernate and power back up and reliably connect to the wireless. 

The problem with the wireless is I have the  Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) wireless card which only has a proprietory driver. This may be causing both the hibernate problem and why it's not always reliable following a hibernation effort? 

I have a Netgear pcmcia with an Atheros chipset. No hibernation problems occur. Networkmanager is all you need to configure it, just 2 clicks and a password on the top right hand side of your screen. You are not giving out enough info on what's wrong with your wireless.

---

