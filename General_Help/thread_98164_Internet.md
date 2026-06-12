---
title: "Internet"
date: 2005-12-02
forum: General Help
---

### Post by ::Lagro on 2005-12-02
How could I configure my network to have DHCP access to the internet?
Not in graphic mod, I need to make this in terminal.

Thank you!

---

### Post by towsonu2003 on 2005-12-03
generally, assuming your network is recognized by ubuntu, and it is an ethernet card, and its name is eth0: 

*plug in the card*
sudo ifconfig eth0 up
sudo dhclient eth0

if your configuration is different, try posting output of sudo ifconfig and sudo iwconfig (if wireless)

---

### Post by ::Lagro on 2005-12-03
Thank You!

---

