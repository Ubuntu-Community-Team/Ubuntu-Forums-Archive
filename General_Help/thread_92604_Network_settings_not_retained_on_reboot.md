---
title: "Network settings not retained on reboot"
date: 2005-11-19
forum: General Help
---

### Post by JimMartin on 2005-11-19
Hello All:

I have what seems to be a curious problem with my Ubuntu. Every time I boot into Ubuntu, the network settings revert to the original values: DNS Servers are 192.168.0.1 and 198.60.22.2 and the Search Domain is domain.actdsltmp. 

If I leave those settings in place, any web site takes many minutes to load (if it ever does). The tech support guys at Xmission here is Salt Lake City (all of whom run Ubuntu on their desktops) helped me out by instructing me to reset the DNS Servers to 198.60.22.2 and 198.60.22.22 and to delete the Search Domain entry. Once I made those changes everything worked and I pages load as expected. 

The problem is that I don't seem to be able to convince Ubuntu that I really want to keep those values. I've tried everything that I (and the guys at Xmission) can think of but it still resets everytime. Anyone else seen this glitch? Got a fix?

Kind of annoying to reset them everytime...

Thanks,

Jim

---

### Post by kruz on 2005-11-20
system>logout> save session and restart

---

### Post by JimMartin on 2005-11-20
[QUOTE=kruz]system>logout> save session and restart[/QUOTE]

Sure seems like it ought to work but doesn't. Sorry I should have mentioned that I tried that.

Any other ideas?

Thanks,

Jim

---

### Post by dcstar on 2005-11-20
[QUOTE=JimMartin]Hello All:

I have what seems to be a curious problem with my Ubuntu. Every time I boot into Ubuntu, the network settings revert to the original values: DNS Servers are 192.168.0.1 and 198.60.22.2 and the Search Domain is domain.actdsltmp. 

If I leave those settings in place, any web site takes many minutes to load (if it ever does). The tech support guys at Xmission here is Salt Lake City (all of whom run Ubuntu on their desktops) helped me out by instructing me to reset the DNS Servers to 198.60.22.2 and 198.60.22.22 and to delete the Search Domain entry. Once I made those changes everything worked and I pages load as expected. 

The problem is that I don't seem to be able to convince Ubuntu that I really want to keep those values. I've tried everything that I (and the guys at Xmission) can think of but it still resets everytime. Anyone else seen this glitch? Got a fix?

Kind of annoying to reset them everytime...

Thanks,

Jim[/QUOTE]
Do you use DHCP or Static IP settings?

---

### Post by JimMartin on 2005-11-20
[QUOTE=dcstar]Do you use DHCP or Static IP settings?[/QUOTE]

DHCP.  I just now tried going to a static IP. That did retain the settings upon reboot but did not seem to connect. I accepted the default subnet mask and that may simply not have been the right one. 

So this looks promising. Any other advice?

Thanks,

Jim

---

