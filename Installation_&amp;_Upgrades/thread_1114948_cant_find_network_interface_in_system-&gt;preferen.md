---
title: "cant find network interface in system-&gt;preference-&gt;network configuration"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by elcid007 on 2009-04-03
Hi guys
I am using ubuntu 8.10 (intrepid) and use static ip settings for realtac lan card 
I upgraded from ubuntu 8.04 about 1 month before and applying updates reguraly 
My lan and internet is working after upgrade but their is no entry of my lan card and no gui way for changing ip settings also their is no gui way for disabling lan if needed for this i have to go to command line and use /etc/network/interfaces file 
is this is only my problem or anyone else is facing the same problem 
i don't like going to command line everytime i want to disbable or enable my lan card .

---

### Post by sukhhari on 2009-04-03
Need to be re-configure you network card

---

### Post by elcid007 on 2009-04-11
And how would i reconfigure my network card 
my network card is infact running fine only the problem seems to be in 
gnome utilite "network configuration"

---

### Post by xtremethegreat1 on 2009-04-11
> **elcid007 said:**
> And how would i reconfigure my network card 
my network card is infact running fine only the problem seems to be in 
gnome utilite "network configuration"

Could you give a screenshot of the 'Network Configuration' Window? Then I could probably find a way out.

:guitar:

---

### Post by elcid007 on 2009-04-11
[ATTACH]109454[/ATTACH]


additional information that may be useful for determining the problem
$cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 172.22.28.57
netmask 255.255.254.0
gateway 172.22.28.254

auto eth0




$ sudo lshw -C network
[sudo] password for user: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:16:76:d5:b5:db
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=172.22.28.57 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:12:ce:42:9a:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by xtremethegreat1 on 2009-04-11
Okay this should do it:

Go to terminal and type:

ifconfig

Then from the record displaying eth0, copy the MAC address.

1. Click add on the network preferences dialog
2. Name your connection name as "auto eth0" (without the quotes of course).
3. Then enter the MAC address you got from the command line.
4. Let MTU be Automatic.
5. leave the 802.1x Security as it is.
6. Then in the IPv4 Settings tab, Select Manual in 'Method'.
7. Click Add and enter your IP, subnet mask and Gateway IP.
8. Then enter the addresses of your DNS server(s) separated by comma.
9. Click OK.

That should do it. If it works, please tell.
:lolflag:

---

### Post by elcid007 on 2009-04-11
> **xtremethegreat1 said:**
> Okay this should do it:

Go to terminal and type:

ifconfig

Then from the record displaying eth0, copy the MAC address.

1. Click add on the network preferences dialog
2. Name your connection name as "auto eth0" (without the quotes of course).
3. Then enter the MAC address you got from the command line.
4. Let MTU be Automatic.
5. leave the 802.1x Security as it is.
6. Then in the IPv4 Settings tab, Select Manual in 'Method'.
7. Click Add and enter your IP, subnet mask and Gateway IP.
8. Then enter the addresses of your DNS server(s) separated by comma.
9. Click OK.

That should do it. If it works, please tell.
:lolflag:

Thanx for your help 
doing these steps and then restarting computer and network manager solved my problem.:)

---

### Post by xtremethegreat1 on 2009-04-11
Awesome man!
Keep enjoying Ubuntu!

---

