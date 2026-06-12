---
title: "Ubuntu Terminal Server"
date: 2005-11-26
forum: General Help
---

### Post by leetcharmer on 2005-11-26
I'm building a network for my church with some previous IT experience in the windows business realm.  But -- I am a linux convert, been so for about 2 years now and I'd like to create this network with Ubuntu influence.

I've done some research on how real businesses utilize linux within their internal network and found LTSP.  To my great surprise, Ubuntu supports LTSP.

I've got about a budget of $500 total on setting up this network (ethernet wiring complete and we've got the business cable modem installed w/ 1 Linksys WRT54G Router).

What should I use to setup this network (hardware), and can you give me some pointers on setting up the server?  Thanks a lot!

---

### Post by kosmic on 2005-11-26
Ok help in configurating the system you can look where :
 
[https://wiki.ubuntu.com/ThinClientHowto]("https://wiki.ubuntu.com/ThinClientHowto")
 
 
In hardware, hum you need for example an HUB (is less expensive than a bridge) and Ethernet cards like 10/100Mb or 100/1000MBs for each one of the LTSP machines you will use, if the machines already have the ethernet card built-in you only need the Hub and the cables :)

---

### Post by skirkpatrick on 2005-11-26
Ethernet switches are almost as cheap as hubs and you will not get packet collisions with a switch.  With a hub, only two machines can talk at a time.

---

### Post by kosmic on 2005-11-26
oh yes I've forgoten switches, switches is much better than HUBs thank for posting it out **skirkpatrick**

---

### Post by skirkpatrick on 2005-11-26
It's actually getting difficult to even find hubs in the States anymore.

---

### Post by leetcharmer on 2005-11-26
should I go: Internet->Router->ServerPC->Switch->Thin Clients?
-or- Internet->Switch->Router->ServerPC->Thin Clients?

how does this [switch]("http://www.pcimicro.com/.sc/ms/dd/1121281410616664/9/nc/Network%20-%20Switch%20%5E2F%20Router--Generic/4363/16%20Port%2010%5E2F100Mbps%20Auto%20Negotiation%20Switch%20%28Black%29%20") look?

I also read that Edubuntu comes w/ LTSP setups, should I just use Edubuntu, would that make this easier?

---

### Post by crouton on 2005-11-28
ServerPC->Switch->Client.  You want internet access controlled through the server (along with all other settings).

---

### Post by lleb on 2005-12-02
[QUOTE=leetcharmer]should I go: Internet->Router->ServerPC->Switch->Thin Clients?
-or- Internet->Switch->Router->ServerPC->Thin Clients?

how does this [switch]("http://www.pcimicro.com/.sc/ms/dd/1121281410616664/9/nc/Network%20-%20Switch%20%5E2F%20Router--Generic/4363/16%20Port%2010%5E2F100Mbps%20Auto%20Negotiation%20Switch%20%28Black%29%20") look?

I also read that Edubuntu comes w/ LTSP setups, should I just use Edubuntu, would that make this easier?[/QUOTE]

Internet, router, switch if the router is not also a switch, then everything into the switch.

for more power and protection, if the church has an old PII laying around with a small HD (2-6G or so), then i would sujest getting an IPCop box up and running with 2 - 3 NICs.  this way you can return that linksys router and have more flexibility and power in your firewall NAT router.

---

### Post by leetcharmer on 2005-12-02
We got the Linksys router to act as a WiFi Hotspot more than anything.

---

