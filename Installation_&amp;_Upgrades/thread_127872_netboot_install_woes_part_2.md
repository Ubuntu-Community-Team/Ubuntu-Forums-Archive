---
title: "netboot install woes part 2"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by Brunellus on 2006-02-10
I have abandoned dhcp3 in favour of dnsmasq as my dhcp server.  I can bring dnsmasq up and down with no problems, and, by adapting the directions here:

[https://wiki.ubuntu.com/Installation/LocalNet](https://wiki.ubuntu.com/Installation/LocalNet)

I can get my client to boot and load the installer.  

The netboot installer doesn't seem to be able to download the release file from anywhere, though.  I was under the impression that, having followed the directions in the Installation/LocalNet wikipage, that the installation would proceed with the client pulling all the ncessary packages from the computer acting as dchp/tftp server on the *local* network, without needing to pull packages from the Internet.

Questions then are:

1) How do I " # out the DNS - routers to make sure the install didn't figure out how to pull files from the net." in /etc/dnsmasq.conf ?  The directions are for dhcp3-server, which I never got to work right.

2) If I can do no such thing, how do I make sure that the client (which sits in the 192.168.1.1xx subnet) can route to the wider network through the server?

---

