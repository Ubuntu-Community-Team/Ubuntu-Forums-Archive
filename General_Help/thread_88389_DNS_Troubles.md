---
title: "DNS Troubles?"
date: 2005-11-10
forum: General Help
---

### Post by Jibboom on 2005-11-10
I recently installed Ubuntu for the first time, and i'm having problems getting the internet working properly with it.

I am on a network, and connect through a router. I can ping the router and anyone on the network. I can also ping external sites, such as google using the ip address. If I type this IP address into firefox I can also access google, and perform searches, however when I try and click on any of the links given from a search it won't find the page. It also will not find the page if I type the address into firefox's address bar (ie [www.google.com](www.google.com) instead of the ip).

Everything works as it should do when I am using Windows.

I've looked through a few threads, but I haven't found anything that has solved the problem.

Any ideas how I can fix this?

---

### Post by az on 2005-11-10
How do you connect to your router?  By DHCP or static connection?  Because the dhcp should assign the same (correct) dns settings as has your router (unless you told it not to do so).

---

### Post by Jibboom on 2005-11-10
I connect by DHCP.

I thought i'd also mention, Synaptic isnt working, neither are things like GAIM.

---

### Post by Jibboom on 2005-11-10
Bump for the people on now.

I really need help with this, there are so many things I need the internet to set up.

---

### Post by Jibboom on 2005-11-11
One more thing, I CAN ping addresses in www. format in a terminal, ie ping [www.google.com](www.google.com) does work, but only typing in IP addresses works in Firefox.



(last bump... someone must be able to help me?)

---

### Post by teaker1s on 2005-11-11
for some reason your dns server isn't being found by ubuntu

 my suggestions are for a router
1)ask your ISP for DNS ip address and manually set it up in router
2)create a static ip in the router eg 192.168.1.60
3 system-administration-networking on gnome set a location and configure static ip and dns-be aware that your location will need clicking on again after reboot even though settings are there-not sure why
4 firefox type about:config and search ipv6

network.dns.disableIPv6 and toggle to true
5) depending on thunderbird email client version you may need to add the extension that allows config so you can disable ipv6 for thunderbird.

hope this points you in the right direction

regards

Daniel

---

