---
title: "Need help setting up wireless. Static IP..etc.."
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by hammerton on 2007-11-07
Hello everyone, I just installed Ubuntu 7.10 on my Acer 5630 and am having a little bit of trouble setting up my wireless. 
See the problem for me is that, I have a WPA encrypted password along with a static IP and a DNS. When I got to manually connect to my wireless it never detects the network and never allows me to connect to the net. BUT when I enable roaming mode and type in the network information (WPA key and Network name) it connects to network but won't allow me to use the net because it doesn't detect my IP, Default Gateway, and DNS. Does anyone have a solution to this problem. I'm really interested in using Linux specifically Ubuntu but its just to bad I'm that pretty new at it. 

I'm using a: 
Intel® PRO/Wireless 3945 802.11 a/b/g wireless LAN card

Any help would be greatly appreciated. Thank you.

---

### Post by hammerton on 2007-11-07
Anyone have a solution, I would really like to start using Ubuntu.

---

### Post by wieman01 on 2007-11-07
The networking applet (Network Manager) does not support the use of static IP as of today. The next Ubuntu release will come with an updated version of NM which will. For the time being there is nothing you can do but enable DHCP.

If you are not afraid of command line, etc. give my WPA tutorial a go... it is specifically meant for users who need static IP. 

A third option is actually [WICD]("http://wicd.sourceforge.net/") which is capable of both DHCP and static IP.

---

### Post by ltcolfury on 2007-11-07
> **wieman01 said:**
> The networking applet (Network Manager) does not support the use of static IP as of today. The next Ubuntu release will come with an updated version of NM which will. For the time being there is nothing you can do but enable DHCP.

If you are not afraid of command line, etc. give my WPA tutorial a go... it is specifically meant for users who need static IP. 

A third option is actually [WICD]("http://wicd.sourceforge.net/") which is capable of both DHCP and static IP.

Thanks for that link to Wicd! Finally I can set my address as static. I was just looking for an alternative solution and you solved it.

---

