---
title: "Downloading Kernel Source"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by gstuartj on 2005-08-29
I often use Ubuntu on my servers, and I'm now doing an install on my home machine. Anyway, this computer uses a wireless card to connect to the internet. It is based on the RT2500 chipset, and so I need to install the kernel module for that chipset. Problem is, I need the kernel sources to compile it, and I can't just do "apt-get install linux-tree" because I have no internet access. I'd rather not move this computer across the house to the router. :-P Any suggestions?

---

### Post by az on 2005-08-29
Just use the linux-headers.

Install build-essential and linux-headers-2.6.10-5-386

You should not need to full source.

---

### Post by gstuartj on 2005-08-29
It's good that I won't have to install the full source, but how would I download the packages on my other Linux partition, then install it on the Ubuntu partition? Is there a particular URL I can go to to get the packages? (AMD64, BTW) Once I have them, what's the specific command to install them? Sorry if I'm being a n00b. I've been using Linux for more than a year, but I've been pampered by Suse's. ;)

---

