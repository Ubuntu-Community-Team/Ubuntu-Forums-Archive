---
title: "Driver for Atheros 5007EG"
date: 2008-12-22
forum: Hardware
---

### Post by agazaleh on 2008-12-22
I have been reading what was already posted, but I am  not sure if they apply to my situation. I apologize if I am asking the same thing. I am new to linux. I am running ubuntu 8.10 on a Toshiba satellite. My wireless router is an Atheros 5007EG. I think I need a driver that is compatible but I am not sure. When I look under Hardware Drivers it has listed "Support for Atheros 802.11 wireless LAN cards" and it says "this driver is activated and currently in use". Many of the posts I've read also mention going to System>Administrator>Networking but I don't have this option. I can go to System>Administrator>Network tools. Thank you to all who respond.

---

### Post by Patrick793 on 2008-12-22
Open a terminal and enter this.

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

This will install the driver for the Atheros 5xxx cards, which was not included with Intrepid.

After installing that, reboot, go to hardware drivers, and disable Support for Atheros 802.11 wireless LAN cards, leaving Support for 5xxx series of Atheros 802.11 wireless LAN cards.

Reboot again and wireless should be working.

---

### Post by agazaleh on 2008-12-23
Thank you for the help.
it tells me

E: Couldn't find package linux-backports-modules-intrepid-generic

I will try updating

---

### Post by agazaleh on 2008-12-23
Thanks worked perfectly.

---

### Post by Patrick793 on 2008-12-23
Glad it worked.

---

