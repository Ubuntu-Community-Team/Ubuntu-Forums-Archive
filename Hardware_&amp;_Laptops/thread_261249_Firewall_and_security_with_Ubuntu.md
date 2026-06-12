---
title: "Firewall and security with Ubuntu?"
date: 2006-09-20
forum: Hardware &amp; Laptops
---

### Post by w3stfa11 on 2006-09-20
I'm a brand new Ubuntu user (yay me!) and I've got it installed on my laptop (dual-boot with xp). Maybe you guys are kind enough to help me out. What do I need to do to make sure my ubuntu installation is secure. I frequently use the wifi on my college campus. Do I need to install a firewall or is there one already built-in like in XP? Do I have to modify anything? Also, is an anti-virus or anti-spyware program needed? Again, I want to be secure. Thank you all! :D

---

### Post by Mapleman on 2006-09-20
I am real new to Ubuntu/Linux as well but I changed over from WindowsXP alltogther, I believe if you go to System > Administration > Synaptic Package Manager and do search for "fire" there are some firewall type packages you can install, using a router adds one as well depending on how you connect. Hope I helped eh;)

---

### Post by Mapleman on 2006-09-20
Firestarter is the full firewall package, not sure spyware/adware are a concern with Linux as still under the hacker's radar but a search on "ad" or "spy" under the package manager wouldn't hurt eh

---

### Post by Melcar on 2006-09-20
You don't need any security at all, but if you're the paranoid type (like me:p  ) you can use firestarter and clamav (firewall and anti-virus respectavely).

---

### Post by simonn on 2006-09-20
> **w3stfa11 said:**
> Do I need to install a firewall or is there one already built-in like in XP?

Yes and no, depending on how you think about it.

The linux kernel has built in network packet filtering, netfilter, which is configured using the program iptables.

However, by default the kernal allows all incoming and outgoing packets. In other words there is no firewall **on** by default.

You can use iptables directly to enter firewall rules, however this can be a little cryptic for a new (or even so called "power") user. IMHO if you have some free time it is worth getting to know how to use iptables though.

There are a few front ends to iptables/netfilter of which Firestarter is probably the easiest and most widely used.

So, using synaptic, install firestarter.

---

### Post by bluefuse on 2006-09-20
No need for Antispyware (yet) the day they make it I will stop using computers, I left MS becuse of that very reason, antivirus, I believe there are like 5 viruses ever created that can harm a linux/unix machine, and you have to download it running as root to harm the system, firewalls firestarter/shorewall.....if you installed KDE try bulldog....... A good router works best but you said you did wifi scanning so it would be random routes, not so good for security on youur end.:rolleyes:

---

### Post by missmoondog on 2006-09-20
the firestarter firewall is just a gui for iptables, but it is useful for looking at download/upload speeds, tracing incoming hits, and is something an ex-windows user would know how to interpet.

i almost believe anybody using linux, has enough common sense to know how to avoid virus' without an av, and as stated, there are only 4 or 5 virus' for linux anyway. spyware scans, defrags, diskscans/scandisks, and all that stuff, are a thing of the past. For now, anyway.

i only recently (1 year) switched over to kubuntu from windows, but have learned enough and liked it enough, that i now have only one computer out of 5 of my own, that still have windows on it anymore, and that's only because i need my scanner (visioneer - no supported drivers).

---

### Post by ramjet_1953 on 2006-09-20
If you want to feel warm & fuzzy, just dowload the 3 month trial of Panda.
There is a Debian binary that installs straight-up.
You have to register the trial, but it gives you 3 months of free updates.
It is an AV and firewall and pops up a window like Zone Alarm to warn you if an app is trying to access the net.
Being a newbie and paranoid myself, it has been a comfort, if nothing else.

Regards,
Roger:D

---

### Post by doobit on 2006-09-20
Firestarter is cool because it gives you real-time port monitoring in a GUI. It also makes thing quick and painless when you need to have port forwarding for Bit Torrent apps or aMSN or other communications applications that need port access.

---

