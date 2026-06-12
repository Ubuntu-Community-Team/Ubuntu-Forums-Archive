---
title: "Wireless Network adapter"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by lawentzel on 2007-02-25
I recently installed Ubuntu vers 6.10 on a Compact laptop.  It is an older laptop but was able to get it up and running with no problem.

My question is, my laptop had no network jack.  Nothing built in.  So, I decided to purchase a PCMCIA card by D-Link.  (Model WNA-2330)  Course now I need to figure out how to get it install.  Any help would be greatly appreciated.  Also, would I have been able to install a USB wireless adapter easier?  Just curious.

Let me know what  other information you might need.  Thanks.

---

### Post by jml on 2007-02-25
My research on the card you purchased suggests that it uses an Atheros chip set.  Don't use the default network utility. (System--->Administration--->Networking)  Instead download and install two applications:  network-manager, and network-manager-gnome.  After you have done than, reboot your computer and you should see a network icon in the right upper corner of your screen.  You access the functions by either right clicking or left clicking on the icon.  Good luck.

Joe

---

### Post by cocoia on 2007-02-26
Also, I can recommend Wifi-Radar from the repositories, from Synaptic. It's a great tool to pick a network.

---

### Post by lawentzel on 2007-02-27
The network card is being partially recognized in Device Manager.  It shows up as "AR5212 802.11abg NIC".  However the Device type is "Unknown".  At this time, I have managed to download the Network Manager per previous suggestions.  What would the next step be to get Ubuntu 6.10 recognizing this card.  Thanks in advance.

---

### Post by fygaren on 2007-03-03
I tried installing the network managers and got the message:
Dependency is not satisfiable: libnl1-pre6 (and libnm-util0 for the gnome)
I have a fresh intall of 6.10
Anybody know what this means?

---

