---
title: "gutsy - parallels ripped my wireless and sound"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by clilush on 2008-03-11
I installed ubuntu gutsy on my laptop (hp/compaq nc 6300) and it was working beautifully.  I installed parallels through the Add/Remove method in order to do support and training on winxp pro.  After a fight with trying to get the network working from the xp guest (I even installed the parallels-tools in the virtual machine) I decided to uninstall parallels and go with something else (virtual box).

After having uninstalled parallels I now have no wireless and no sound.  I can see the device for the wireless in the Hardware Information (gnome, System menu) and in the Restricted Drivers Manager ("ipw3945" -- but listed as "not in use").

I have a feeling that when I uninstalled parallels it ripped out the configuration for my wifi device (it was eth1 -- thank g*d that my eth0/wired connection still works!).  Any thoughts or fixes?

edit.... My wireless switch is a button at the top of the keyboard and when I press it it doesn't light up and nothing comes up in the syslog (tail -f /var/log/syslog) and when I look at my nm-applet it shows nothing to do with wireless.

---

