---
title: "network config from kcontrol not working?"
date: 2005-11-11
forum: General Help
---

### Post by hastour on 2005-11-11
I needed to set a static ip for a net connection. Opened kcontrol, put the right numbers in network config, eth0 was marked as enabled, just the net didn't work. I put the numbers in again several times, and noticed that it didn't remember the gateway ip, after closing kcontrol and opening again the field was blank. Then I had the idea ( brilliant, for a newbie like me ;) ) to put the gateway ip manually in /etc/network/interfaces, this enabled the network. But what was wrong with the gui way to do it? Another issue: dhcp network didn't work for me at all :(. I've searched in this forum about it and found an advise to use dhclient eth0 command. It works now, but needs repeating sometimes, which is annoying.

---

### Post by mlomker on 2005-11-12
A lot of the applets in Kubuntu are broken.  In my opinion they shouldn't have released it at the same time as the gnome version...it clearly isn't ready yet.

DHCP should take care of itself when the lease expires.  If you continue to have trouble then I'd recommend a post on the Networking forum.

---

