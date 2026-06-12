---
title: "Very challenging - IP Conflict"
date: 2008-07-30
forum: Hardware
---

### Post by Danie1a on 2008-07-30
Hello, 

I want to describe for you a very weird problem that I encounter with my laptop at my job. I'm the only one who has that problem (though I'm not the only one who has Ubuntu) 

 The problem is that I and one of my colleague (who has Windows) have problems with the internet - only us have this problem and only when we are both on the network. I have configured my IP statically (when I was using DHCP it was always trying to get my colleague's IP address (she stil has DHCP configured).  In general the communication between us is really difficult although we are in the same LAN. 

This problem appeared since I start bringing my laptop at work (my normal PC broke). 

Since I'm not the only one that has Ubuntu - but the only one who has a laptop - I considered that this could be a hardware problem. 

thanks in advance,

I'm hope I described my problem well enough - and I'll be here to answer any of your question.

---

### Post by coffeecat on 2008-07-30
You're right; it is weird.

I'll probably be derided for this suggestion because even I think it's daft, but I'll put it forward anyway. Check the MAC addresses of the NICs that you and your colleague are using. Make sure they're not the same.

And before anyone starts chucking rotten tomatoes in my direction, yes I know that MAC addresses are meant to be unique. The chances of one manufacturer (or two) making a mistake and then two identically-addressed NICs meeting up in the same office are probably impossible, but... :(

Not that this should make any difference because the problem occurs when you both use DHCP, but is the static address you chose in a range not used by the router when allocating IP addresses? Otherwise you're in danger of getting an IP address clash.

---

### Post by evets25 on 2008-07-30
You never actually said what the problem is in the post, so I'm assuming that somewhere, somehow, one of the computers is giving you a message that says there's an IP conflict. What exactly is the problem though? What are the symptoms? I mean, it's good to know that only you and this other person are having the problem, and that it's an IP-address related problem, but what, exactly IS the problem? 

IF it is the case that there is an ip address conflict at work, AND that you have configured a static IP address, then the solution is obvious: pick another IP address, and check the configuration of the DHCP server (if you can) to make sure your static IP doesn't fall in the range of addresses that are handed out via DHCP.

---

### Post by Danie1a on 2008-07-31
The problem is that mine and hers internet is going down and coming back, and in special the communication between us is almost always down.I'm going to  check the MAC address ...
The IP Conflict was when we were both on DHCP. 
In the next week I won't be able to answer or check new solutions because my colleague is on vacation, but I stil wan't to try to solve this. 

10x a lot.

---

### Post by lisati on 2008-07-31
I would have thought that it would be more likely to be the hostname of the computer than the MAC address - aren't MAC addresses different from NIC to NIC?

---

### Post by doas777 on 2008-07-31
> **lisati said:**
> I would have thought that it would be more likely to be the hostname of the computer than the MAC address - aren't MAC addresses different from NIC to NIC?

they are supposed to be, but companies license them in blocks from Internic (or so i'm told) and they will occasionally duplicate them to save costs.

DHCP shouldnt be affected by teh host name, unless you are using DDNS and your clients attempt to register the DNS name based on the DHCP address.

one thing you may wanna try is to delete the DHCP cache record for both PCs. they can get confused at times.

---

