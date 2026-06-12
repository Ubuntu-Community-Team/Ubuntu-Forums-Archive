---
title: "VPN connection and Network adapter"
date: 2005-11-10
forum: General Help
---

### Post by neur0 on 2005-11-10
1. Does anybody have an idea how to set up a VPN connection? My ISP uses VP network and the standarad pppconfig doesnt cover making VPN connections.
2. How do I know if my network adapter (3com 3c905b) works under Ubuntu?
It is "active" as an Ethernet card in network configuration window.
PS As you can see, I am new to Linux .

---

### Post by hajk on 2005-11-10
Open a terminal from the Applications/Accessories/Terminal menu, then type
"sudo ifconfig". The output should tell you whether your Ethernet connection is up and running. Another way of checking this is by typing "sudo route". In both cases the Ethernet device (most likely eth0) should be associated with an IP address. And finally, you could type "dmesg | more" and check for messages concerning your Ethernet connection. You could test the connection by pinging a known address, e.g. by typing "ping -c 3 www.yahoo.com". 

As to VPN, you should ask the help desk at the institution that you want to connect to whether an IPSec-based VPN client (like CISCO) will work. If so, you can start Synaptic and install the "vpnc" package. Ask the above help desk for the VPN gateway address, the group ID and Password to be used (in addition to your own ID and password) in order to make a connection. 

Let us know if you need more assistance with this.

---

### Post by neur0 on 2005-11-10
I think that my Network Adapter works. 
I couldn't find "vpnc" in Synaptic though. Maybe it has a diferent name or something?
I have all the parameters for the VPN connection as I have it running on my Win partition.
As for asking my ISP's help desk or support for anything related to Linux, I'm afraid I'm out of luck. They don't know much about even Windows networking. They probably think Linux is some kind of a pet-name for my computer ;) . 
But I am prepared to try any solution.
I can't ping yahoo as I need to connect to the VPN to be online, but I will try to ping my gateway (I'm on a switch connected to a router AP that has a wireless connection to the ISP's VPN).

---

