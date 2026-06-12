---
title: "wireless stoped working after update"
date: 2009-12-23
forum: Hardware
---

### Post by TheHimself on 2009-12-23
Lenovo s10 with ubuntu 9.04. Wireless was working fine until I let update manager to install some updates (which were about Firefox, xlrunner and ubuntu one client as far as I can remember.) Now my wireless card is not detected and at boot-up one of the steps (loading hardware drivers or something like that) fails. 

Hardware Drivers application show no proprietary drivers in use. What's happened?

---

### Post by theDaveTheRave on 2009-12-23
TheHimself,

it sounds as though you have lost your hardware settings, which is strange (and exceedingly annoying, I had this happen when I upgraded to hardy herron!).

first off check to see if you hardware is all found correctly

```

lshw -C network

```

will show all the network interfaces that are recognised by your system. Hopefully the wifi card is being found but 'unclaimed' or something.

You will then have a "device name"

here is the output when I run the command..

> 

 *-network
       description: Wireless interface
       product: [COLOR="Green"]AR2413[/COLOR] 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:40:b8:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.135 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg


I've highlighted in green the important detail for the 'name' of the card.

try googling the equivalent for yours, and you should find some help to get it working. If not the forum members will do our best to help you out.

Either way if it leads you to a solution, document it here and how you solved the problem.

good luck

David

---

### Post by TheHimself on 2009-12-23
It seemed to be related to linux restricted modules. I had a problem with linux kernel upgrades not being configures automatically as mentioned here: 

[http://ubuntuforums.org/showthread.php?p=8546708#post8546708](http://ubuntuforums.org/showthread.php?p=8546708#post8546708)

I resolved the problem as mentioned there and now wireless works!

But still I have a question. How can one install a new hardware driver in Ubuntu?

---

### Post by theDaveTheRave on 2009-12-23
TheHimself,

4 and half hours to a successful resolution.

not bad for a forum!

Congrats on getting it working.

If you need a specific hardware driver, you will need to install a 'module' into the linux kernel.

You would have to search for your particular piece of hardware, then add the module into /etc/modules/ ~~ somewhere and it will load on boot.

If you can't find a 'native' linux module you will often find a 'wrapper' for the windoze version (it translates the information into something our linux kernel can understand). This is quite common with wifi cards and is normally done using NDISwrapper, for example.

David

---

