---
title: "Ubuntu server 9.04 LAN setup"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by RayTheRat on 2009-07-21
I'm new to Ubuntu and although I've been using linux for years, I'm far from an expert at it.

I had a web/mail server/gateway running ClarkConnect for the last 7 or 8 years.  It just cratered.  I knew it was coming, so I started building a new server.

It's a Dell Optiplex pox with 512mb RAM and 40gb disk, 2 NICs (or course) and is about 3 times bigger and faster than the old box.

I've installed US 9.04 and got the box to communicate with the outside world via the cli interface and apt-get.  This all works fine.

I can't find out how to set up the internal (ETH1) network so my workstations can use the gateway (transparent...the actual gateway address is on the Cisco 678.)

I made a feeble stab at adding another eth1 entry to /etc/network/interfaces but no joy.

I'd like to have the US box run a DHCP server, but I haven't figured out how to do that either.

I've read a lotta how to's but I haven't seen anything on this...probably because I have to recable and re-address things to use a workstation with a browser.  

So any assistance would be very, very much appreciated.

---

