---
title: "Dell Latitude C400 / Ethernet Card"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by Michelle on 2005-04-22
I have a Dell Latitude C400 with a 3Com 3c905c Ethernet card, and it shows up find in the Device Manager (under 82801BAM/CAM PCI Bridge), but I don't know if it's not recognizing it as an ethernet card or what, but it says the device type is "unknown" and it doesn't work when I put the LAN cable into it at all.

And I'm also going to get a wireless card for it later, and any information on what a good one would be and how to install it would also be appreciated.  Please help, so I don't have to bug random people on AIM anymore...

I need it to work with a wireless connection, and I'd really hate to have to switch to XP, even though I got a legal copy from school for free. :\

---

### Post by mudra on 2005-04-23
Try some / none of the following.

su
<password>

ifconfig

(What do you get as an output from that ?)

you can then try setting up by doing the following:

ifcofing eth0 192.168.0.1 (or whatever network address you need) assuming your lan is eth0 (see output from first command for a hint).

route add default gw 192.168.0.1 (or whatever your network is)

Then try pinging and see if anything works.

If you want to surf the net you may need to add an entry to /etc/resolv.conf for your dns server.

For the wireless card try a google search that should turn up a lot of information for you.

I use a NETGEAR WG511 and that works well, although I have heard that there are problems with the new ones that have just come out.

Hope this helps.

Mudra

---

### Post by rusi_pathan on 2005-04-25
I would recommned an internel Intel PRO/Wireless 2200 b/g Mini PCI. Installation is very easy and it works under ubuntu right away. Though just be sure to disable the parallel port in the BIOS as it results in IRQ errors.

---

