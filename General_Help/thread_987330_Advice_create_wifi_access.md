---
title: "Advice create wifi access"
date: 2008-11-19
forum: General Help
---

### Post by m0x on 2008-11-19
Hi everyone, I'm looking for some advice i need to create a hotspot for my school community i have this hardware

Compaq deskpro (384 mb ram, 2 nic cards, 40 gb hd)
1 antenna lynksys + access point lynksys

I was looking and i find that squid as a proxy and set up a dhcp server

am'i i the correct path to create the wifi access.?:confused:  


thanks

m0x

---

### Post by Titan8990 on 2008-11-19
Does you access point not include a DHCP server?

---

### Post by fragos on 2008-11-19
Assuming you Linksys access point is a standalone wireless router you have vertualy noting to do regarding DCHP. The router sets up a LAN and will by default assign any PC that connects a local address. All pc's have access to the Internet. You can cable connect PC's or servers -- usually 4 or 5. Chances are you'll want to use the mentioned PC as a data base server. Give it a unique host name and all Linux PC's on the LAN will be able to access it as {hostname}.local, no IP's required. If you're networking Windows boxes you will be using Samba on your Linux data base server.

---

### Post by m0x on 2008-11-20
thanks for the anwsers 

1.- the access point don{t have the dhcp service


I set up por testing purposes ubuntu 8.10 +squid + dhcp3-server, everything it{s almost fine only i have the issues with the dhcp server only assign 1 ip i will put th conf file (part of it) so you can check to see if everything looks fine


# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.51 192.168.1.150;
option domain-name-servers 200.23.242.185, 200.23.242.177;
#  option domain-name "internal.example.org";
option routers 192.168.168.1;
option broadcast-address 192.168.1.255;
default-lease-time 600;
max-lease-time 7200;
}

my eth0 it's attach to the dls modem so i have a dinamic ip
   eth1 it's static ip address 
address      192.168.1.50
netmask      255.255.255.0
network      192.168.1.0
broadcast    192.168.1.255

with squid everything it{s fine, all this it's for test purposes


thanks

m0x

---

