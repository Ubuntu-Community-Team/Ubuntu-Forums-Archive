---
title: "ubuntu network problem"
date: 2005-11-11
forum: General Help
---

### Post by D1G1T4L on 2005-11-11
ok so i have a windows and ubuntu box connected to the the router, the router sees MY ubuntu box but i cant ping the ubuntu box from my windows box and i cant ping from the ubuntu box and web pages, etc dont load

i tried doing dhclient command but all it does is wrirte
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCVER on lo to 255.255.255.255 port 67 interval 66
......

NO DHCPOFFERS received
No working leases in persistent database - sleeping....


i now statically assigned the ip but nothing changed

i also tried doing
sudo ifdown eth0
sudo ifup eth0
ifconfig

it just writes the same thing as dhclient (see my previous post for the info of what it writes)

ifconfig just shows

eth0 and bunch of info(such as hd address, static ip address that i assigned 192.168.0.100 - for some reason it also shows Bcast: 192.168.0.255, i dont know what that is though) and lo with bunch of info



can anyone help?

---

### Post by Kyral on 2005-11-11
Uhh...I don't know a lot about Networking. Perhaps this thread is better in the Networking Support forum

---

### Post by rcerreto on 2005-11-11
Are you able to access the internet from the Windows box? I presume you are not.

Usually routers act as DHCP servers so that you can get not only IP Address but also DNS server address and **gateway** address.
Look at your router documentation, if you can start DHCP services you are home, just set to get IP Address automatically by DHCP.
On both boxes: Ubuntu and Windows.

If you can't have a DHCP server running you'll have to set by hand not only IP Address but also Gateway and DNS addresses.
Again, both on Ubuntu and on Windows.

On Ubuntu, in a console, type:

**sudo route add default gw 'your-gateway-ip-address-here' eth0**

What's your gateway's ip address?
Well, a router has 2 different IP Addresses: one toward the internet, received by your ISP, and one internal toward your LAN which has a default factory setting. Look again at your router documentation to know which one. Frequently it's 192.168.0.1 but your could be different. For instance, mine is 192.168.0.254. 
Use your internal ip address in the route command.

On windows, you'll have to enter the same address in the advanced section of tcp/ip properties. Of course after setting its own static ip address.

Now your two boxes should be able to ping each other.

You still have to set DNS address. Just add one line to /etc/resolv.conf:

**nameserver 'your-ISP-DNS-ip-address-here'**

Of course you need to know this address which is far from being obvious.
Enter the same info in windows in the DNS tab of tcp/ip properties.

Now cross fingers and take a breath, you should be able to access the internet.

HTH

---

### Post by D1G1T4L on 2005-11-11
[QUOTE=rcerreto]Are you able to access the internet from the Windows box? I presume you are not.

Usually routers act as DHCP servers so that you can get not only IP Address but also DNS server address and **gateway** address.
Look at your router documentation, if you can start DHCP services you are home, just set to get IP Address automatically by DHCP.
On both boxes: Ubuntu and Windows.

If you can't have a DHCP server running you'll have to set by hand not only IP Address but also Gateway and DNS addresses.
Again, both on Ubuntu and on Windows.

On Ubuntu, in a console, type:

**sudo route add default gw 'your-gateway-ip-address-here' eth0**

What's your gateway's ip address?
Well, a router has 2 different IP Addresses: one toward the internet, received by your ISP, and one internal toward your LAN which has a default factory setting. Look again at your router documentation to know which one. Frequently it's 192.168.0.1 but your could be different. For instance, mine is 192.168.0.254. 
Use your internal ip address in the route command.

On windows, you'll have to enter the same address in the advanced section of tcp/ip properties. Of course after setting its own static ip address.

Now your two boxes should be able to ping each other.

You still have to set DNS address. Just add one line to /etc/resolv.conf:

**nameserver 'your-ISP-DNS-ip-address-here'**

Of course you need to know this address which is far from being obvious.
Enter the same info in windows in the DNS tab of tcp/ip properties.

Now cross fingers and take a breath, you should be able to access the internet.

HTH[/QUOTE]

No my windows box works and yes my router ip is 192.168.0.1 asll those settings u just mentioned are already setand i added it the router internal ip as gateway and dns in settings in UBUNTU, but its just i cant ping anything from ubuntu and internet doesnt work

---

### Post by rcerreto on 2005-11-12
OK, next try.
I assume you can't even ping the router.

One lively chance is that your NIC is not working under Ubuntu.
I had this problem with an integrated LAN controller on an Asus MB, namely:

Ethernet controller: Marvell Technology Group Ltd. Yukon Gigabit Ethernet 10/100/1000Base-T Adapter (rev 13)

Ubuntu (Hoary) loaded what seemed to be the correct module but its version was not alligned with my ethernet chip. 
Everything looked OK but the NIC was actually 'dead'.
I recycled an old NIC which worked fine.
Now, with Breezy, also the new integrated NIC runs OK. 

You could be experiencing a similar problem.
The simple fact that you can't get an IP address from the router is a strong hint.

Try booting with a Knoppix 4.0.2 LiveCD, which is usually very clever at hw auto-detect. If you can ping with it the problem is better defined.

---

