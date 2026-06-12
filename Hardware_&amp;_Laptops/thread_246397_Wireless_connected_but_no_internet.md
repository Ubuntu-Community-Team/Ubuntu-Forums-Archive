---
title: "Wireless connected but no internet"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by SlimShooted on 2006-08-29
Hi I'm sorry if the question has alrady been asked but i'm new to linux so I really don't know where and what to search.
Here is my problem, my ubuntu is connected to my rooter, the signal is good but when I lunch firefox or anything which uses the internet, I can't access it.
If anyone has a solution please telle me.
Thanks

---

### Post by rcd412 on 2006-08-29
"sudo dhclient (interface name IE eth0)" give that a try

---

### Post by SlimShooted on 2006-08-29
So,I tried and it is still not working but this is what it gave me at the end:

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by rcd412 on 2006-08-29
interesting... how are you trying to connect to the internet?

---

### Post by SlimShooted on 2006-08-29
I've seted up a wireless connection and the network monitor says it is connected but when I lunch Firefox it says Server not found

---

### Post by rcd412 on 2006-08-29
yea the no offers recieved after running dhclient means you don't have a net ip address... i would just double check everything again, make sure your router is set up as a dns server and there are enough slots open for another connection.

---

### Post by SlimShooted on 2006-08-29
Yes it is a DNS server and there must be enought slought cause I had UBUNTU 5 running on it 5 days ago on the same computer

---

### Post by mangoti on 2006-08-29
Check if wireless is enabled, if security (wep or other) is not the issue. You can also try to reboot the router.

---

### Post by SlimShooted on 2006-08-29
The router can't be the problemù because i am actually using it

---

### Post by rcd412 on 2006-08-29
not really sure what the problem is then, apart from disconnecting and reconnecting... see if you can connect to the router with ethernet using that computer

---

### Post by mangoti on 2006-08-29
> **SlimShooted said:**
> The router can't be the problemù because i am actually using it

Well, it could be. The problem can be that the wireless nic is not getting the IP address, or the router is not handing out the IP to that particular card. If you do not have the correct wep key for example you will not be getting any IP address.

Have you tried to put a static IP to see if it works?

---

### Post by IcemanV9 on 2006-08-29
Install network-manager - sudo aptitude install network-manager-gnome

More info if need --

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking?highlight=%28wireless%29)
[http://www.ubuntuforums.org/showthread.php?t=125150&highlight=wireless+howto](http://www.ubuntuforums.org/showthread.php?t=125150&highlight=wireless+howto)

---

### Post by SlimShooted on 2006-08-29
I can connect to it eaven with the wireless, when I type the ip adresse

---

### Post by rcd412 on 2006-08-29
we realize that... connecting to the router is only have of the battle, it still isn't giving you a dns address

---

### Post by mangoti on 2006-08-29
Can you give a hint about what hardware/router you have?

---

### Post by littlec on 2006-09-01
I'm in the same boat as you Slimshooted.

mangoti: my router is a trendnet tew-431brp and my wireless usbcard is D-link dwl-g132

My card is now able to recognize my router with accesspoints, but no luck finding nameservers/dhcp.

---

