---
title: "Network not working on Vnware Ubuntu"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by jp006 on 2009-06-20
Spent over 20hrs on the net/google, ~4 resintalls (total 3 days), still can get My VMware Ubuntu's 9.04 Network to work.

**From Guest Ubuntu I can not ping the host, and from host I can't ping guest.**
I have turned off my Laptop/XP the ZoneAlarm firewall.

My Main (Host) machine is Win XP (Laptop).
I only have a Linksys router to connect to Internet via ADSL.
I do NOT have a switch, or a dedicated DHCP server.
1 other machine connected to Routher for surfing
My Host's IP is set DHCP and not static, currently it is: 
        IP Address. . . . . . . . . . . . : 192.168.1.66
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

I now have VM Ware server 1.0.2 i also tested it with VM Ware 2, still gave same issue.

I have used **Bridged network**, since I want my Ubuntu to use Internet.

I have given Ubuntu static ip address e.g. 192.168.1.68 / 255.255.255.0, restarted net service, still no luck.

I normally use wireless, read on a site bridged might not work on wireless, so now testing it with wired (my laptop to router), still same issue.

I did the same test at my Work PC, everything worked fine, I guess maybe because over there they have proper network and DHCP server.

Please...please someone kindly help or give directions...

---

### Post by Ganymedes on 2009-06-21
Well, this is almost certainly a misconfiguration, because the underlying technology is pretty solid.

You did not say what you had on your Ubuntu box for the default gateway? I assume that it is wrong and if wrong would cause things like that. You need to have the same as on the Host.

But if it is more complicated then perhaps you like to read about a couple of principles in this:

1. 
First, why do you not use NAT-network and DHCP? There is typically no real cause for Bridged - certainly Internet usage is not a cause.

Since you Host is working, I think you could get it to work in no time by doing this.

If you use NAT, it does not matter what connection you have to network on your Host, wired - wireless - 3G, if it works on the Host, then the client will work, too.


2.
For Bridged - Host does NOT need to be configured for Internet, nor does it need "to work". Obviosly VMware client IS dependent on the Host hardware working, like the network card working, and thus testing that Host works, is probably needed at some time.

If you use Bridged, you need to configure your client as you configure the Host.

3.
If you have ever touched with NAT network addresses, they need to be correct. But if you use DHCP on your client, it does not matter what the NAT address space is.

---

