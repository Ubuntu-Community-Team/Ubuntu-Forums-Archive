---
title: "Acer Aspire 7551 wifi problem"
date: 2011-03-09
forum: Hardware
---

### Post by tony987456 on 2011-03-09
O.K. Kinda new here and i also couldnt find this anywhere so hopefully someone can help with this weird problem. I have Ubuntu 10.10 64 bit on my Acer Aspire 7551 and i can connect to my home network while AC is plugged in. Once i run on battery power i cannot connect to my home network but i can connect to anything else i.e. my Android device. Plug the laptop back in, i can connect again to my home. Any ideas?

---

### Post by Yellow Pasque on 2011-03-10
What chipset do you have?
```
sudo lshw -C network
```
Do you see any messages on the end of dmesg when you try to connect to your home network on battery?
```
dmesg
```

---

### Post by tony987456 on 2011-03-10
NetLink BCM57780 Gigabit Ethernet PCIe



87.810217] eth1: no IPv6 routers present    << This is the last message after running dmesg

---

### Post by airper on 2011-05-14
Having the same issues on installing 11.04. on the same machine.

This is the closest I could find having searched the forum and Goggled the problem.

It worked fine on 10.10, but no wireless functionality at all right now, even if wireless checkbox is ticked, wireless is still grayed out in connection manager and no connections are showing the list.

Screenshot attached having:

sudo lshw -C network
to see what is going on. Would appear wireless is disabled in the setup somewhere, but how to turn this on. The Ctrl F3 function on the keyboard does not work.

Any help or pointers in a direction to look gratefully received.

---

### Post by Yellow Pasque on 2011-05-14
@airper: wireless driver is loaded, so check rfkill:
```
rfkill list
```

---

### Post by airper on 2011-05-14
RFKILL produced this. Seems the driver is loaded okay, but soft-blocked so how to release this???

---

