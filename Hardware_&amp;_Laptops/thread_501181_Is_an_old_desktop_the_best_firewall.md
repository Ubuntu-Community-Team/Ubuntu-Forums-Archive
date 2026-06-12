---
title: "Is an old desktop the best firewall??"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by nite owl on 2007-07-14
Hi as I have just ordered a new notebook, I have decided to not follow in every other one of my new computers/notebooks steps, having to format it a month after recieving it :) I am looking at all different sorts of options, then I stumbled upon the concept of having an old desktop computer acting as a firewall? Is this a better option then just having a software firewall on your computer? If it would be I would defiantly want to set this up, however I am not to sure on how? would anyone have any insight in this subject?? Thankyou

---

### Post by xfile087 on 2007-07-14
Sounds like a good idea to me and you can even turn it into a personal file server to make backups too! You can also setup a local apt mirror for when you install software - much faster.

I'm hoping to do this with my Mac Mini.

---

### Post by lisati on 2007-07-14
Another option is the firewall built into some routers. The one I use (one of the Netgear family) has one built-in.

---

### Post by nite owl on 2007-07-14
I was looking at routers but my broadband modem is a usb modem that picks up wireless internet, It has no ethernet connections and I was told that means It cant be run on a router?

---

### Post by lisati on 2007-07-14
> **nite owl said:**
> I was looking at routers but my broadband modem is a usb modem that picks up wireless internet, It has no ethernet connections and I was told that means It cant be run on a router?

I don't know, sorry about that. Anyone?

---

### Post by nite owl on 2007-07-15
Actually has anyone used smooth wall before?

---

### Post by IntuitiveNipple on 2007-07-15
Unless you need an always-on router to serve multiple PCs on your LAN then running a PC *just* for fire-walling is a lot of overkill, especially in terms of the amount of power it'll consume, noise the fans make, and future management.

In your scenario running the firewall (netfilter/iptables)  on another PC wouldn't give you any appreciable advantages and in some cases could complicate matters if you want to use some complex multi-port protocols.

Not having the firewall on your notebook is actually a problem in some cases, because if you are using a notebook it implies you want to go out and about and use Internet connections in other places. In that scenario you really should have a firewall on the notebook.

Therefore, do you want to have to maintain two sets of firewall rules and try not to get confused over where it was you set some obscure rule 6 months ago? :)

You'll need to do remote log-in to the firewall, set up some interesting port-forwarding rules, and likely sometimes find something you need to do is prevented by the configuration and frustrates your attempts to sort it quickly.

I've been working with ipchains/iptables firewalls for years and for a simple home deployment my preferred option is a simple router+firewall+wifi combination which runs off 9 volts and runs quiet (no fans)  and iptables on the notebook/laptop PCs with **FireStarter** to make management of iptables simple.

---

### Post by nite owl on 2007-07-15
IntuitiveNipple a router would be alright. But I am not using a standard ethernet adsl connection. I have a usb modem that picks up wireless internet. Do you know of any routers that could accomadate this?

---

### Post by IntuitiveNipple on 2007-07-15
> **nite owl said:**
> But I am not using a standard ethernet adsl connection. I have a usb modem that picks up wireless internet.
What kind of interface does the USB device present in Linux? Does it present as a network interface or as serial/PPP interface?

The type of connection (USB or Ethernet) shouldn't affect the firewall since it works at the IP protocol layer for the most part.

I'd be interested in the specific details of your set-up: modem model & version, what drivers it uses in Linux, how it presents to Linux as a network device. 

Overall, investing in a combined DSL modem + router + firewall + WiFi device is a good move. Linksys and NetGear among many other manufacturers produce countless versions and you can get some very good deals on eBay.

I recently bought the Linux version of the Linksys WRT54GL (router + firewall + WiFi). I already had a DSL modem so I connected an Ethernet cable between the two and it was sorted. I could have bought a single device to combine the ADSL and router functions but I have a public subnet with servers directly connected to the ADSL modem ports.

If I had a standard home setup I'd have one device doing all the gateway work - its usually just a case of plugin, configure, and forget.

---

