---
title: "Ubuntu and Asus M2400Ne"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by feldhege on 2007-10-15
Hello everyone,
   I just got a free Asus M2400Ne laptop that had a bad hard drive in it. I had a new one lying around so I went and put it in. I decided I should try to see what all this Linux stuff is about :) and installed Ubuntu. Everything appears to run and it pulls our dhcp information just fine. Only trouble is that nothing goes through most of the time. It almost appears that something is blocking it from reaching the outside world. I am the Administrator for our company so I know it is not the firewall. It is really weird. For instance I will try to ping and it will pull the resolved ip address and then hang. If I wait long enough (maybe 3 to 5 minutes) it will start pinging. Of course this is too long for web pages and most network apps. I am at a loss. I did find some postings here of people who made modifications to their ubunto configs and got it going but I am not sure how to do this. I also found one website that talked about some changes he made and then recompiled because of the Dothan Stepping CPU that Asus uses. It was from 2004 so I don't know if this has been done in the current version. Anyway, can anyone help a first timer?

The laptop has
1.5Ghz processor
Intell 2200BG wireless
40 Gig drive
256 Memory
realtek ethernet port.

Robb Feldhege

---

### Post by fsando on 2007-10-15
Hi feldhege
Not sure I can help but perhaps I can inspire you to go on ;)
Which version of Ubuntu do you run? I own a M2000N which is very similar to yours it runs Ubuntu 6.10 since newer versions won't install on it. I also had to upgrade bios to v208 to have this one install. Though if the installation seems to work it is likely not the problem.

There is a general advice about disable certain settings regarding ipv6 (do a search to find the exact instructions). The symptoms are long search times but not that long I reckon, never been a problem for me.

If you use static ip you may be pointing your machine to a wrong gateway or similar - this in my experience gives exactly those symptoms. I am no expert though. 

You may try the command 'ifconfig' (like windows 'ipconfig') it will tell you the ip address of your machine

ifconfig eth0 (gives info on eth0)

---

### Post by feldhege on 2007-10-15
That is similar to what I am finding. Long search times when running network applications such as firefox or terminal server. It just seems to hang and then takes off running like normal. It is not the desktop locking up because while it is hanging, I can do other things like nothing is wrong. I wondered about disabling ipV6. I may do a little more searching and see if I can figure out how to do that.

Robb

---

