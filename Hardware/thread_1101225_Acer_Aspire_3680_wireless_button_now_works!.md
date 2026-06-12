---
title: "Acer Aspire 3680: wireless button now works!"
date: 2009-03-20
forum: Hardware
---

### Post by theDaveTheRave on 2009-03-20
Hello to all users of the Acer Aspire 3680:

After a recent upgrade to intrepid, following a wireless access failure, I have descovered that the button on the front of this laptop now functions!

Please post your experience with your acer wireless button, and any "strange" functionality that you have.

here is what I consider "pertinent" info about my wireless;

Wireless chip: taken from the output of lshw -C network...
```

 *-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0a:03.0
       logical name: wifi0
       version: 01
       serial: 00:19:7d:40:b8:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.135 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

Button function, is rather interesting, (see [this]("http://ubuntuforums.org/showpost.php?p=6744389&postcount=204") link for the full post on it's funcion, and other troubleshooting to get the chip to work).

But briefly.

Depending on how many times I "slide" the button, I get different returns from an <iwlist scan> - from getting only the master interfaces, to then getting a list of ALL "visible" the interfaces, and then ALL interfaces (including my "hidden" local network).

If you are having a similar thing please report back what you get (just as a matter of interest of course).

Remeber post you <lshw -C network> details, so as we can make a true comparison.

If anyone out there has problems with this card / system to get it working (allthough it allways worked straight out of the box for my instalations) drop me a line, and I will help were I can, or direct you to one of the various "experts" that are much more knowledgable than me (like the guys that helped me get my chip working again recently (thanks go to pytheas22 and kevdog)

David

---

### Post by dePeatrick on 2009-07-15
Hi, I could do with a bit of help on this, we have the same wireless card.

lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wmaster0
       version: 01
       serial: 00:16:ce:14:b4:ba
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=10.42.43.1 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:f6:ca:ea
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:c7:35:79:43:1d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I am trying to connect woth a MacBok running Tiger for internet usage bit am geting very slow speeds.


I know this is an old thread but maybe.......!

---

### Post by theDaveTheRave on 2009-08-26
dePeatrick

sorry I missed your reply onto this thread.

Unfortunately I'm not going to be of much use to you on the issue of speed via your wireless card.

Unless you are running a dual boot on your mac and are able to demosntrate a considerably different connection speed when using one or the other systems I have no way of knowing how to proove that there is a problem with your wireless card or the connection in general.

However, in my experience whilst using XP-pro, the connection via a wireless card on Ubuntu was much improved in comparison.

There are some things that you may like to note in your situation however.

Walls and other obstacles - I know that it seems obvious, but we have some serious "dead spots" in our house, and I don't completely understand why!

Baby communicators. I know this sounds ridiculous but I read somewhere that the "old fashoined" analogue walkie talkie that people use for listening in on thier little ones can seriously interfere with being able to connect to a wirless network (I have personal experience of this as we use them at home, as do the neighbours!) - in fact that may also explain our "dead spots"

I don't know if that has helped you or not, or if you have found another thread that had a solution, if you have please enter a link to the thread / web page or otherwise explain what you have done.

sorry to not be of much more use.

David

---

