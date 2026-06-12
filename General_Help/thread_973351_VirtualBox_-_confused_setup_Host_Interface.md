---
title: "VirtualBox - confused setup Host Interface"
date: 2008-11-06
forum: General Help
---

### Post by joel@parke.ods.org on 2008-11-06
Hi,

I am attempting to setup networking on VirtualBox using Host Interface.
All works, but I loose by connection to my apache web server when I setup my tap by doing:
sudo tunctl -t tap1 -u joel
sudo brctl addbr br0
sudo ifconfig eth1 0.0.0.0 promisc
So far so good.
But then when I execute:
sudo brctl addif br0 eth1
I immediately see:
sudo: unable to resolve host parke.ods.org

And after that, I no longer can see my home server which is parke.ods.org

If someone could explain to this newbie why this is so, it would be greatly appreciated.  

After this to then complete the setup of tap1 I then execute:
sudo dhclient br0
which says... bound to 192.168.1.106 -- renewal in 40325 seconds.
then I execute:
sudo brctl addif br0 tap1
sudo ifconfig tap1 up
sudo chmod 0666 /dev/net/tun
THEN At the VirtualBox startup panel, choose “Host Interface” and add “tap1&#8243; to “Interface Name”
And all is good as related to having the VirtualBox networking... but I can never see my web server again...

What gives?

Thanks,
Joel Parke

---

