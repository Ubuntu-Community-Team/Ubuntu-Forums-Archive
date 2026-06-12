---
title: "Two wifi cards"
date: 2015-01-23
forum: Hardware
---

### Post by sheldondawson35 on 2015-01-23
How do I get two wifi cards working in windows and ubuntu via virtualbox? I'd like to have one connect to the internet by wireless n and one connect one to a router not connected to the internet to access files?

I have one that is a Intel(R) Dual Band Wireless-AC 7260 and havn't purchased the second one. What should I buy for the second one?

---

### Post by weatherman2 on 2015-01-23
Install your wireless devices in the host file system, not in the guest (OS installed inside Virtualbox).  Let the guest interface to the network through the virtual networking device to your host, not directly to a wireless card.

There are easier ways to do what you say you want to do without the needless complication of two separate wireless cards.  For example, you can put a server on your network and configure your networking hardware (e.g. router) to disallow direct internet access to it or allow only one route (your laptop to it) to exist.

---

