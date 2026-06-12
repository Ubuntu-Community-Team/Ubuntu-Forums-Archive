---
title: "ethtool not run"
date: 2005-11-30
forum: General Help
---

### Post by ingrid on 2005-11-30
Hi,
I try to set speed and duplex on my eth0. To do this, I use this command : [COLOR="Teal"]ethtool -s eth0 autoneg off speed 100 duplex full.[/COLOR]
The result is : [COLOR="Teal"]Cannot get current device settings: Operation not supported
                      not setting speed
                      not setting duplex
                      not setting autoneg[/COLOR]
So I try a simple command :[COLOR="Teal"] ethtool eth0[/COLOR] to see the current config of the interface.
The result is : [COLOR="Teal"]Settings for eth0: No data available[/COLOR]
At first I was connected to a HUB and now to a switch. The only thing that I configured, was the ip address with ifconfig. I think that the speed and duplex was configured automatically by the negotiation with the hub in 10Mb half dpx.
The first problem is that ethtool doesn't retrieve any information from the interface. 
Is there someone to help me? Thanks a lot in advance.

---

### Post by ranf on 2005-11-30
[QUOTE=ingrid]Hi,
I try to set speed and duplex on my eth0. To do this, I use this command : [COLOR="Teal"]ethtool -s eth0 autoneg off speed 100 duplex full.[/COLOR]
The result is : [COLOR="Teal"]Cannot get current device settings: Operation not supported
                      not setting speed
                      not setting duplex
                      not setting autoneg[/COLOR]
So I try a simple command :[COLOR="Teal"] ethtool eth0[/COLOR] to see the current config of the interface.
The result is : [COLOR="Teal"]Settings for eth0: No data available[/COLOR]
At first I was connected to a HUB and now to a switch. The only thing that I configured, was the ip address with ifconfig. I think that the speed and duplex was configured automatically by the negotiation with the hub in 10Mb half dpx.
The first problem is that ethtool doesn't retrieve any information from the interface. 
Is there someone to help me? Thanks a lot in advance.[/QUOTE]
I need to put sudo in front of ethtool to produce some valuable output.

---

### Post by ingrid on 2005-12-01
I m root when I put these commands ...
ethtool only run on root

---

