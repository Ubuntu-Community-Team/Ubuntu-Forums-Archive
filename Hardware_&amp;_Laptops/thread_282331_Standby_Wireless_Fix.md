---
title: "Standby Wireless Fix"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by drblast on 2006-10-22
I don't know if this has been posted before, but I found a fix for my wireless card not working after a suspend.

It seemed to me that the problem was the wlan0 device never came back up.  This isn't quite true, I found it DID in fact come back, but as eth1.  No idea why, but if you configure the eth1 device exactly the same as the wlan0 device in /etc/network/interfaces, the eth1 device will work as expected upon resume.

Here's my partial config:

auto eth1
iface eth1 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1

auto wlan0
iface wlan0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1

Hope this helps.

---

### Post by linuxguiri on 2006-11-12
where's the config file that i need to modify with this info?

---

### Post by chicagokarl on 2006-11-14
The config file referred to is /etc/network/interfaces

---

### Post by linuxguiri on 2006-11-15
Strangely, my /etc/network/interfaces has the wireless info (key, etc.) under eth1 instead of under wlan0.

I tried adding the same information to wlan0 but there is still no wireless on resume from suspend.

---

### Post by neocookie on 2006-11-16
I've found I get the same problem in Edgy... however, I switch between 3 or 4 networks weekly (home, work, family, friends' networks), so I can't force my wireless network config to one set of settings.

Any idea how I could fix this for my situation?

---

### Post by Decade on 2006-11-16
Do you know which drivers it was using? If it was maybe using one driver initially, giving it wlan0, and another driver later, giving it eth1.

---

### Post by linuxguiri on 2006-11-16
> **Decade said:**
> Do you know which drivers it was using? If it was maybe using one driver initially, giving it wlan0, and another driver later, giving it eth1.

I think it was using ipw3945 as the driver. Not entirely sure though.

I managed to get wifi to work after resume from suspend by erasing everything but the lo (loopback) connections in the config file and installing NetworkManager. Works now!

---

### Post by linuxguiri on 2006-11-17
> **neocookie said:**
> I've found I get the same problem in Edgy... however, I switch between 3 or 4 networks weekly (home, work, family, friends' networks), so I can't force my wireless network config to one set of settings.

Any idea how I could fix this for my situation?

Install Network Manager!

---

