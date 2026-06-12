---
title: "moblock whitelisting gamer servers"
date: 2008-11-01
forum: General Help
---

### Post by lionheartxxi on 2008-11-01
Hi Ppl, i just installed moblock and was wondering how the gamers whitelist ips to their gamer servers.  Having problems connecting to steam on virtual os xp, Seems good else where just need to configure it a bit.  If no advice can be given i will just have to contact steam themselves.  Thanks in advance!!

---

### Post by lovinglinux on 2008-11-01
You can get a Steam ip list from i-Blocklist at [http://iblocklist.com/list.php?list=steam](http://iblocklist.com/list.php?list=steam)

Then you have to add those IP's from this list to /etc/moblock/allow.p2p

If you don't want to allow Steam IP's all the time you could save a default allow.p2p list without them and one with them, then replace /etc/moblock/allow.p2p with the corresponding list and reload moblock every time you need to allow or deny the IP's. IS easy to create a script to do that.

For example, you could save the default and steam lists to an "allowlist" folder in your user directory, then use the following scripts to replace "allow.p2p" based on what you want to allow:

```
#!/bin/bash

sudo moblock-control stop
sudo cp ~/allowlists/allow-steam.p2p /etc/moblock/allow.p2p
sudo moblock-control reload
sudo moblock-control start
```

This script will copy the allow-steam.p2p from "/home/you/allowlists" and save it as /etc/moblock/allow.p2p then reload and start moblock.

When you are finished playing you can run this script to remove steam IP's from allow.p2p:

```
#!/bin/bash

sudo moblock-control stop
sudo cp ~/allowlists/allow-default.p2p /etc/moblock/allow.p2p
sudo moblock-control reload
sudo moblock-control start
```

Please notice that allow-deafult.p2p should have only those IP's that you want to allow, which does not include the Steam IP's in this case. 

You can create similar scripts and allow lists for other games or network activity. If you want more complex rules, you can modify /etc/moblcok/moblock.conf to use different allow lists for input, forward and output traffic.

I suggest you visit the "[[COLOR="Red"]**General Moblock Thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=803183")". If you have interest, I go even further with this kind of moblock customization as I explain on [[COLOR="Red"]**this post**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5984806&postcount=112"). I'm using not only different allow lists, but also different blocklists, configurations and iptables scripts depending on what I'm doing on the net.

---

