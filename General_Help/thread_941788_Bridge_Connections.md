---
title: "Bridge Connections"
date: 2008-10-08
forum: General Help
---

### Post by G3XOI on 2008-10-08
I want to bridge my wireless connection with my LAN connection which is connected to my Xbox 360 but I have no idea how to do it using Ubuntu!

Any help would be greatly appreciated!

---

### Post by bodhi.zazen on 2008-10-08
[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

Not all wireless cards support bridging ...

---

### Post by G3XOI on 2008-10-08
> **bodhi.zazen said:**
> [https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

Not all wireless cards support bridging ...

I'm afraid this does not make any sense to me :| (I'm a linux newbie you see).

---

### Post by bodhi.zazen on 2008-10-08
Networking is not so easy to grasp and you have posted only general information on what you are trying to do exactly.

Here is another walk through :

[https://help.ubuntu.com/community/KVM#Bridged%20Networking]("https://help.ubuntu.com/community/KVM#Bridged%20Networking")

[https://help.ubuntu.com/community/KVM#Creating%20a%20network%20bridge%20on%20the%20host](https://help.ubuntu.com/community/KVM#Creating%20a%20network%20bridge%20on%20the%20host)

Basically you will need to install. by any method, "uml-utilities"

Then, by any method, edit your configuration files, ie /etc/network/interfaces to first add a bridge and then add your interfaces (eth0 , wlan0, or what have you).

First make a backup of the file, then bring your network down, edit /etc/network/interfaces with:

```
gksu gedit /etc/network/interfaces
```Then bring you network (and hopefully bridge) back up.

To show your interfaces use :

```
sudo ifconfig
sudo iwconfig
```

---

