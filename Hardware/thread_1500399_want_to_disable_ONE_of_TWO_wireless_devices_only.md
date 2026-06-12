---
title: "want to disable ONE of TWO wireless devices only"
date: 2010-06-03
forum: Hardware
---

### Post by ikunat33 on 2010-06-03
I have 2 wireless devices. One is built in. One is USB. I would like to use only one at a time. So I try:

ifconfig wlan1 down

and it goes down... and then pops back up 15 seconds later.

iwconfig wlan1 txpower off

seems to kill both wireless devices (granted they do not pop back up)

How can I either
 - disable one and have it stay off
 - stop whatever is turning them back on from doing so

Thanks.

---

### Post by dino99 on 2010-06-03
[http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html](http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html)

---

### Post by ikunat33 on 2010-06-03
This does not appear to let me disable one of the network cards (turn off completely) and... it seems to be quite flaky on my system. Leaves zombie windows up.

RUNNING LUCID BY THE WAY... Sorry everyone... probably should have mentioned that.

---

### Post by ikunat33 on 2010-06-03
I found a few threads where people were having the same problems. None of the threads had solutions. Here is what I found "works".

sudo apt-get install ethtool

sudo ethtool -i {interface}   # this will show you what driver is used

sudo modprobe -r {driver}     # removes driver and disables interface

sudo modprobe {driver}        # adds driver and enables interface again

Thats it. Unfortunately if you have two interfaces using the same driver then, I imagine, both will go down... but at least they will stay down :-).

A better solution would still be nice.

Thanks.

---

### Post by Ground Loop on 2010-06-26
> **ikunat33 said:**
> I have 2 wireless devices. One is built in. One is USB. I would like to use only one at a time. So I try:

ifconfig wlan1 down
and it goes down... and then pops back up 15 seconds later.

iwconfig wlan1 txpower off
seems to kill both wireless devices (granted they do not pop back up)

How can I either
 - disable one and have it stay off
 - stop whatever is turning them back on from doing so

Thanks.

I have the same question.  I have an internal (Intel) wifi that works great, and I want to keep it enabled and controlled by Network Manager.

I have a second USB wifi that I want to use for kismet/wireshark analysis, and I do *not* want anything in the system to associate with it or use it for local traffic.

If I blacklist the module, well, that disables it altogether.
"txpower off" seems to (incorrectly?) knock out both adapters.

I can't seen to put anything in /etc/network/interfaces that blocks it from associating and getting a DHCP assignment.

I suppose what I'm really looking for is the connection that notifies Network Manager that an interface is present.  I want Ubuntu to load the module automatically, create wlan1, but then leave it entirely alone.

Any ideas?

---

