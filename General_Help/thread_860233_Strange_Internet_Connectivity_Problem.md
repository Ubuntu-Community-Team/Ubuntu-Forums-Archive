---
title: "Strange Internet Connectivity Problem"
date: 2008-07-15
forum: General Help
---

### Post by darkconcept on 2008-07-15
Hello,

I have the following problem and wondering if someone more experienced could help as I am very new to Linux.
I installed ubuntu desktop at my house and all went fine, got connected to the net etc...
I then transferred my laptop to the office, but I can get no internet connectivity.
The only difference between my home and office setup is the model of the router (the office one is a linksys wag200g).
Tried tweaking network settings and searching the web for solutions but to no avail.
Could really use some help here.

I must also add that I checked the router settings meticulously and they appear ok. Also, my brother's notebook that runs xp connects just fine from the same jack that the ubuntu computer is getting no connection.

DC

---

### Post by deadtom on 2008-07-15
This is a pretty broad question. We really need to know a bit more about the office network.
Is it DHCP or do you have to assign an IP address? Is there a proxy or firewall you need to authenticate through? If it is DHCP are you getting an IP, DNS and gateway address and if so, have you tried to ping or traceroute and if so how far are you getting?

---

### Post by coffeecat on 2008-07-15
How old is the office router? The reason I ask is that older router firmware (that's both older routers and older firmware :wink: ) can't cope with the IPv6 modified IPv4 addressing enabled by default in Ubuntu (and most other Linux distros). It is not enabled in Windows XP, which is why XP works fine in these situations.

There's a quick way to check whether this is the problem, using Firefox. Open firefox in Ubuntu and type 'about:config' (no quotes) in the address bar. Type 'ipv6' in the filter (no quotes). You should now see only one line beginning 'network.dns.disable.IPv6'. Change the 'false' at the end to true by double-clicking on it. Now close Firefox and restart. If you can now surf the web, you have established that IPv6 is the problem. That's fine for Firefox, but you still won't be able to access the net with other apps such as the package manager or update tool. There are three possible fixes.

1 Disable IPv6 system wide in Ubuntu. You have to edit a system file and I can't remember the details. Search the forum - This has come up many times. This is not the best solution. IPv6 will have to be used sooner rather than later. It is enabled by default in Vista and has been the default in MacOS for the last 2 or 3 versions of OSX.

2 Update the router firmware. This may not be feasible - I understand that - and updated firmware for that model may not be available.

3 Don't use DHCP. Assign a fixed network IP address for Ubuntu. You also have to manually put in the gateway address , subnet mask and DNS server addresses. Post back if you need help with this. Be warned though that this also may not be feasible. You have to choose a network IP address that the router is not going to assign to another machine. How big is the office network? Also, IP addresses for internal networks are either in the 192.168.x.x or 10.0.x.x range. If your home and office ones are different that's going to cause you headaches.

**Edit:** - just realised, there's a fourth solution. Get your office to get themselves a new router. Could you bribe someone to spill coffee all over the old one? :)

---

### Post by darkconcept on 2008-07-16
Thanks guys.

Deadtom the router is configured to give DHCP addresses starting from the 100 (i.e., 192.168.1.100). Before that the addresses are reserved for static (non-routable) IPs. I tried pinging but no go.
I also configured the network connection in ubuntu both for static and for dhcp without success.

Coffeecat, I think it might the solution might be the ipv6 thing. Thanks for taking the time to suggest it. I will try it tomorrow (dont have the laptop with me today) and see if it works.

DC

---

