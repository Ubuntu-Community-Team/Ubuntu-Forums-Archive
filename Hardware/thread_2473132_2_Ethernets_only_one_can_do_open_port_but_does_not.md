---
title: "2 Ethernets only one can do open port but does not work on WAN"
date: 2022-03-25
forum: Hardware
---

### Post by Raymond Day on 2022-03-25
I got Google Wi-Fi and a mesh system. So port forward will not work on it.

So I got another Google Wi-Fi and put it between my main Google mesh and cable modem.

Then I got a USB to Ethernet and put it on the side of the 1 Google Wi-Fi and port forward 443.

The other port real ethernet is on my LAN and works good.

Here is my ifconfig -a

ifconfig -a
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.86.11  netmask 255.255.255.0  broadcast 192.168.86.255
        inet6 fe80::2e0:4cff:fe68:13f2  prefixlen 64  scopeid 0x20<link>
        ether 00:e0:4c:68:13:f2  txqueuelen 1000  (Ethernet)
        RX packets 67688734  bytes 10175707612 (10.1 GB)
        RX errors 0  dropped 45  overruns 0  frame 0
        TX packets 87113405  bytes 47129848944 (47.1 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enx7cc2c6304f23: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.87.119  netmask 255.255.255.0  broadcast 192.168.87.255
        ether 7c:c2:c6:30:4f:23  txqueuelen 1000  (Ethernet)
        RX packets 48901  bytes 4817683 (4.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 28596  bytes 3978164 (3.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5276876  bytes 1624655913 (1.6 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5276876  bytes 1624655913 (1.6 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 20:79:18:ad:17:86  txqueuelen 1000  (Ethernet)
        RX packets 2858750  bytes 3518399322 (3.5 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2058387  bytes 2448289197 (2.4 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

So the USB to Ethernet is named enx7cc2c6304f23


They have different subnets. 86 and 87 the 87 one I got port forward on. With the Google Wi-Fi between the 87 subnet.

But I can only get to Apache port 443 on my LAN.

I guess Apache uses all Ethernet ports right?

How can I get this to work though the 2nd Ethernet on the WAN got port forward all ready to it.

-Raymond Day

---

### Post by Raymond Day on 2022-03-28
Even WordPress will get a error because it's not on the WAN.

RSS Error: WP HTTP Error: cURL error 7: Failed to connect to wordpress.org port 443: No route to host

I can ping things and it works.

-Raymond Day

---

### Post by The Cog on 2022-03-28
I think your lack of answers is because nobody has any idea what you are trying to do - what doesn't work. 

You say you set up port forwarding, but I'm not sure what that means - what you configured or why: can you show config?
Where is the apache you can't get to? On your LAN, in the server or somewhere on the internet?
No route to host - please also post the output of the command "ip route".
> I guess Apache uses all Ethernet ports right?
Apache listens on whatever addresses/ports you configure it to listen on. It doesn't care about interfaces. But actually, this question makes me think that maybe the apache is on your Ubuntu box. Check which addresses it's listening on. The command to see all listening TCP processes is ```
sudo ss -lntp
``` and you are looking for (I think) httpd and 443. 
A local address of 0.0.0.0 or [::] is good - it will accept calls to any address on your box. 
A local address of 127.0.0.1 or [::1] is bad - it won't accept connections from outside the box.

---

