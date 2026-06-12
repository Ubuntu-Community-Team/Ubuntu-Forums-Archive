---
title: "Madwifi (Atheros wireless) freezes system?"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by hizaguchi on 2006-11-08
I'm wondering if anybody else has been having any problems with the Madwifi driver for Atheros wireless chipsets.  Specificially, it seems that the driver causes the system to randomly freeze if connected to a 128-bit WEP encrypted network.  This is happening in both Dapper and Edgy, but I don't know how long it has been going on because I only recently encrypted my home network.  I hesitate to report this as a bug because I don't know if I'm the only one experiencing the problem.  Anybody else?

---

### Post by alex.miller422 on 2006-11-16
I am having the same problem. My system used to freeze once every 3-4 hours, under Dapper. Under edgy, I'm lucky if I get 10 minutes.

Disabling the atheros modules in /etc/modprobe.d/blacklist stop the system freezing.

---

### Post by alex.miller422 on 2006-11-16
I am compiled and installed the SVN madwifi driver from madwifi.org after making my previous post.

So far, no lock ups:)

---

### Post by FingerPie on 2006-12-27
Hi,

I posted a related issue elsewhere, what steps did you take to remove your prior installation?  I see a lot of help on the madwifi pages, was that your guide?

-FP

---

### Post by dannyboy79 on 2006-12-27
i do NOT have this issue with dapper. my xubuntu machine works awesome with a netgear wg511t card. which has the atheros chip. I use 128 WEP also. Using a Netgear Wireless Router also. don't know what else to suggest to get it to work?

---

### Post by alex.miller422 on 2006-12-28
I followed the instructions from the madwifi site, for installing from source.

After checking out the source code and building, I ran 'sudo make install', This asks if you want to remove a previous installation, which I said yes to.

---

### Post by dannyboy79 on 2006-12-28
i suppose maybe you could try this as a last ditch effort but ubuntu already comes with madwifi support built in which is why my atheros card worked out of the box as well as why it asked you if you wanted to remove the previous installation.

---

