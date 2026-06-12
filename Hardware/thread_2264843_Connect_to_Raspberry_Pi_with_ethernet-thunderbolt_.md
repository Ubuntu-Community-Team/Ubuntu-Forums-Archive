---
title: "Connect to Raspberry Pi with ethernet-thunderbolt adapter"
date: 2015-02-10
forum: Hardware
---

### Post by hugo24 on 2015-02-10
Hi there! I am having some trouble connecting my Macbook pro retina (which means that i don t have an ethernet connection) to a raspberry pi, i bought a thunderbolt-Ethernet adapter and i was able to configure it to have wired internet in ubuntu 12.04, but i am not being able to connect to raspberry pi, as anyone ever been able to do so?

Thank you in advance.

---

### Post by efflandt on 2015-02-10
I take it that you are running Ubuntu on your Macbook connected to a router and your Pi is also connected to the router and has an IP address? What daemon/service are you trying to connect to on the Raspberry Pi?

You might want to install **avahi-daemon** on the Pi which would allow you to do **avahi-browse** in Ubuntu to find your Pi (as its hostname**.local**). On the Pi:```
sudo apt-get update
sudo apt-get install avahi-daemon
```and install **avahi-browse** if that is not included or installed. Then **avahi-browse -at** from either computer should list hostnames of any computers using avahi-daemon (which Ubuntu has by default) or Apple zeroconfig, or **-atl** options (small L) would skip showing the computer you are on. Then using the hostname of the Pi you should be able to: **ssh** hostname**.local -l** username_on_Pi_if_different_than_Ubuntu_user

---

### Post by hugo24 on 2015-02-10
Sorry for the lack of that information, i am connecting the raspberry pi directly to the Mac (no routers involved). My objective is to make a connection through SSH in order to obtain some information from the raspberry pi and sent other.

---

### Post by hugo24 on 2015-02-12
I made a noob mistake i forgot completly of choosing "Shared to other computers" in IPv4 settings.

---

