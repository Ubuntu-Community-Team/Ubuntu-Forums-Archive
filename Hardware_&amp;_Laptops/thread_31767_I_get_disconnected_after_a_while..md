---
title: "I get disconnected after a while."
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by Kizo on 2005-05-04
Hi.
Yesterday I installed Ubuntu on my Amilo M1425 Laptop. It is my first time ever installing or using Linux.
But I have a problem (Well, actually I have a bunch of problem, but just one that I'll focus on now.) and that's that I get disconnected after a while, about 15 minutes.
I'm connecting with my WLAN to my AP. If I are to reboot the computer, it will go online and stay online for about 15 minutes, then it disconnects and doesn't connect again. And due to my lack of experience with Linux systems, I have no idea what to do.

Anyone got some bright ideas?

---

### Post by 23meg on 2005-05-04
i have a kind of similar problem with my laptop: when i leave it on, connected to the network (not wireless), for extended periods, i usually find that it has disconnected when i'm back. when i check the network connection system/administration/networking i see that it's activated, and deactivating and reactivating it won't help. i wonder if DPMS, ACPI or locking the screen might be to blame.

---

### Post by ManLord on 2005-05-04
Same problem here. Does anyone know how to fix this permanently, or to restart network without restarting system?

---

### Post by Kizo on 2005-05-06
[QUOTE=23meg]when i check the network connection system/administration/networking i see that it's activated, [/QUOTE]
Exactly!
It says it's activated, but disconnected.

We really need some help on this one.

---

### Post by eClaW on 2005-10-18
I've got the same problem: checking into WLAN network via vpnclient and after about 10 minutes or so the connection dies. Network is not configurable anymore (when i click the button nothing happens) and when rebooting it hangs at "deconfiguring network devices" for hours.

To me it looks like a driver problem of the wlan card...

Specs: IBM T20 with WLAN card Netgear WG511T, also running 5.10 Breezy Badger.

---

### Post by FireSoul on 2008-05-29
same thing here

i use ndiswarrper for netgear wg11t

and i have the same problem here

---

### Post by Turd Flop Down M'leg on 2008-06-05
Has anyone had any success with this?  I'm using 8.04 with DHCP over a simple linksys router and still have this problem.  When my connection dies, I cant get anything to work. `sudo ifdown eht0 && sudo ifup eth0` just gives DHCPOFFER errors and restarting the network with /etc/init.d/networking restart doesnt do anything either.  Ping cant find yahoo.com and pings to 192.168.1.1 says host unreachable.

I'll be watching a video on youtube and then go to surf off somewhere else and my connection is dead.  The only thing that fixes it is rebooting...

---

### Post by Turd Flop Down M'leg on 2008-06-07
Bit more info, I'm using a VIA vt6102 Rhine-II with kernel 2.6.22.17.  On boot up the network is there and running, but after the screen saver comes up, the network is gone forever..

---

