---
title: "Another Wireless Card Problem..."
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by mercnboy3 on 2005-12-18
I am using a Linksys WPC54GS Wireless Network Card to try to connect to my D-Link Wireless Access Point.  I have successful installed the necessary driver via ndiswrapper.  ( Driver used lsbcmnds ).  Everything is good, I have setup the  interface through System > Administration > Networking.  But when I run dhcpd I get the following: messages

There is already a pid file /var/run/dhclient.pid with pid 8785
killed old client process, removed PID file

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:13:10:f2:el:a8
Sending on LPF/wlan0/00:13:10:f2:el:a8
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received
No working leases in persistent database - sleeping

* Assume the Router that the WAP is conected to has DHCP up and running.

---

### Post by greenway on 2005-12-19
Use "ifconfig" to see if your wireless adapter is up and running, which it probably is. If it running, I think the problem might be with your DHCP server because the wlan interface is not finding any leases on the network.

---

### Post by mercnboy3 on 2005-12-19
Why is it looking for 255.255.255.255?

---

### Post by mercnboy3 on 2005-12-19
Why is it looking for 255.255.255.255?

(oops, twice) :(

---

### Post by greenway on 2005-12-19
Well, it's not really looking for 255.255.255.255. It's broadcasting a request for a lease from your DHCP server, 255.255.255.255 is the address used for broadcasting "messages" over your network, it just means sending a message to all listening servers on your network.

---

### Post by mercnboy3 on 2005-12-19
What is the sit0 device?

Do you think this could be caused by an invalid ESSID?


My Signal Strength applet is reporting a 100% signal strength, but the link light is not on.

---

### Post by Lambert on 2005-12-19
sit0 is an interface to help the transition from ipv4 to ipv6 protocol. It basically allows a machine running only the ipv4 protocol to be able to tunnel into and connect to a network running just ipv6. It has no affect on your current problem.

Post the output of these commands.

iwconfig

ifconfig

sudo iwlist wlan0 scan

Also when you installed the driver via ndiswrapper, did you pull the driver from a folder on your hard drive? In that folder did you have any other file such as .sys or .bin?

What are the details of your network setting? open signal? wep or wpa encryption?

---

