---
title: "No Network Device Found!"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by anshumanoz on 2005-12-27
Hello,

I installed Ubuntu for the first time ever on my Dell Inspiron laptop. When I go to network settings, ubuntu detects the network identified by its ESSID in the drop-down list. I've also put in the correct WEP Key and all. But, when I click on the nrtwork icon in the tray, it says "No Network Device Found". I am using an Intel Centrino to connect to my wireless cable modem. 

Any clues on how best to resolve this? Do I need to install certain drivers? If so then where can I get those and how best to install them?

Thanks
Anshuman

---

### Post by fordfan753 on 2005-12-27
Intel Centrino? That's a processor....

If you have a Centrino, I'm going to take a stab in the dark and say you probably have a ipw2200, because they seem to be pretty common. What type of laptop do you have?

---

### Post by anshumanoz on 2005-12-27
Hi,

Thanks for your reply...

When I meant a centrino, I meant I am using "Intel Pro Wireless" to connect to my cable wireless modem and not a 3rd party network card. I've been using this on my Windows XP to connect to it.

I have  DELL Inspiron 8600. 

Can you please explain what is a "ipw2200". I don't know most of the linux specific terms. Again - if I need to download and install a driver - how should I do it?

Thanks
Anshuman

---

### Post by fordfan753 on 2005-12-28
ipw2200 is the chipset of the wireless card I'm assuming you have. The drivers for ipw2200 are in the kernel, so it should work without much trouble at all.

---

### Post by noeluylee on 2005-12-28
Centrino is not the Processor or a Wireless brand or model, its simply mean your notebook pc is capable of doing a wifi thing, its a marketing strategy of Intel. 

For you network problem, I didnt encounter it on my notebook pc, I am using Dell Inspiron 700m too.

Double click the icon on the system tray, and just choose the name of your wireless either eth0 or eth1, mine is eth0 = wireless eth1 = 10/100based-t.

Go to your /etc/network/ vi the interfaces. mine look like this.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface

iface eth1 inet dhcp

"interfaces" [readonly] 47L, 499C                             1,1           Top

I am using unsecured network hehehehe, I used wep and it worked as well. 

Hope this helps :)

Good luck.

---

