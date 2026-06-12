---
title: "New Network Card and Ubuntu Doesnt find it"
date: 2015-03-03
forum: Hardware
---

### Post by aaron50 on 2015-03-03
Hi all,

This is probably an easy question for someone, but I am new to Ubuntu and Linux. I just installed [this]("http://www.intel.com/products/desktop/adapters/pro1000gt/pro1000gt-overview.htm") network card in my computer. I am running Ubuntu 14.04 server with a Light Lubuntu, and when i boot up the machine, it says "waiting for network configuration...", it waits about 2-3 minutes and cannot find a network. When i boot up i run Lubuntu and wait about 5 minutes, then the machine somehow finds the network card and i suddenly have a network connection. How do i get Ubuntu to realize that i am not using the on-board network card, i am using a PCI network card? Is this something that I should change in the BIOS or in Ubuntu?

I have not installed any drivers for this card, I am very new to all of this and am trying to learn. I do not know how to install drivers on Linux and i am not sure if i even need to since Ubuntu is eventually finding my network card.

---

### Post by weatherman2 on 2015-03-03
If you had been using the the on-board network card previously, it would have been assigned ID "eth0."  The new one is probably "eth1."  When you boot, Ubuntu is trying to establish a connection on eth0 because that the device you originally used.

I don't know the cleanest way to solve this.  One way perhaps is to disable the on board network card in your BIOS setup.  Then it would be the only network card detected and could get assigned "eth0."  However, "eth1" will remain until you remove it from the file /etc/udev/rules.d/70-persistent-net.rules .  (You can simply erase this file, then reboot and it will automatically be regenerated next boot.)  Without an onboard network card enabled, at next boot, after you remove that rules file, the new network card should become eth0 and it may just work.

Or, you could try editing the file "/etc/network/interfaces" and change references to "eth0" to "eth1"  then reboot.  However, you should make sure "eth1" really is the device ID of your new network card.  You can verify this by typing "ifconfig" (after you've booted after the long delay and you finally get a network connection) and see what the device ID is in the left column.  You may see both eth0 and eth1 but eth1 should be the only one connected.  It may be something besides eth1 if you have connected other network devices in the past.

---

### Post by aaron50 on 2015-03-04
weatherman,

Thank you very much. I followed your final paragraph and was able to get it to work. As a reference for anyone else, the result of "ifconfig" showed both eth0 and eth1, but the eth1 had an ipaddress next to it. I commented out the lines in the "/etc/network/interfaces" that referenced eth0 and re-wrote them to reference eth1. I knew this was probably an easy fix. Thanks once again.

---

