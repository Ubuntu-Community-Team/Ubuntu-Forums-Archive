---
title: "600e drops ath0"
date: 2006-07-09
forum: Hardware &amp; Laptops
---

### Post by FoggyMtn on 2006-07-09
Hey ya'll

I'm posting this here and not in the wireless because I felt it was more of a laptop issue....

I've got a TP 600e with a netgear pcmcia card.  There is wep encryption to a wrt54g and a seperate box running Smoothwall acts as my firewall.  

Here's the issue.  Everything works great when the laptop is up and running.  When I suspend it (manually: sudo apm --suspend, couldn't get it to work automatically :( ) the unit, well, suspends.  When I wake it back up, my wireless access is gone.  I have to do a :
sudo ifdown ath0
sudo ifup ath0

Is there a way to either correct this, or automate it?  It's not bad for me to do, but if my wife picks up the laptop, she gets frustrated when it won't just work.

Thanks for the help

rob

---

