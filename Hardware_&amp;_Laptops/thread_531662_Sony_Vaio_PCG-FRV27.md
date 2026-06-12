---
title: "Sony Vaio PCG-FRV27"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by commiebstrd on 2007-08-21
Yay, first post on a new forum. Anyway, I have a sony vaio pcg-frv27 that I am trying to put Ubuntu on. Currently it is a dual boot system with the secondary os being Win XP Pro. I am a total n0ob with any *nix platform, but I do have many years with microsoft products and thier many issues. At the current moment  I cannot get my home network to be recognised. It does work in windows and I have no other issues with any of my other computers. I would really appreciate any help, but what I would mainly like if possible is a list of drivers that are or should be working already or some way for me to tell what I need to do to make this work. I have also included a Belark analysis of the windows side of my system.(it needs to be unrared)

---

### Post by serj_alligator on 2007-08-22
You have Realtek 8139 I have the same one and had no problems with laptops and desktops... Strange...
go to terminal and tell us responses on command
try > dhclient
maybe your dhcp server/router doesn't assign you ip address...
if that doesn't help type this command and tell us the output you get
> dmesg && lspci && ifconfig

Good Luck.

---

### Post by commiebstrd on 2007-08-22
Well here is the output from those commands. From my limited knowledge it looks like most of my hardware is working and has proper drivers, although I may be wrong. Again any help is really appreciated.

---

### Post by commiebstrd on 2007-08-22
Well, I brought this to work today and thankfully it connected right up to the network. So I guess comcast gets a friendly phone call. Anyway, I still would appreciate it if someone could go through whatever I posted before and let me know if there are any glaring issues.TIA commie

---

### Post by serj_alligator on 2007-08-23
I'm sorry...the dhclient has to be run as super user(root)...

Try:
> sudo dhclient
Also now I'm looking at my sony vaio and our output seem very alike and are the same for network interface...
It seems like your ethernet card communicates on network, but doesn't seem to receive IP from DHCP server(probably router).
Try the following command and see if it works out for you, I hope it does and that's what it seems like the problem to my...
If you get it working please post here so that other's could fix their problem....

Good Luck!

---

### Post by commiebstrd on 2007-08-28
Well I'm not exactly sure what happened with my internet/ethernet. At work it has always worked fine and continues to. The internet service at my house had the issue, while at work  I figured out that Ubuntu has automatic updates (ya I know..Go figure). So I installed them and brought the laptop home, plugged it into my switch and it works great. So maybe it was just needing the automatic updates. I don't know but thanks for the help and I am glad it works.

---

