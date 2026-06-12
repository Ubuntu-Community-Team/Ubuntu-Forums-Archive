---
title: "HP LJ Pro M402dn"
date: 2018-12-31
forum: Hardware
---

### Post by merlinus on 2018-12-31
The printer is connected to my router, and worked perfectly until I had to reinstall 18.04 today.  Now it cannot be detected as a network printer, only as ipp://NPI5E588B.local:631/ipp/print, which does not work.  NPI5E588B is its device name on the router, and it has its own IP address.

Unfortunately HP does not support linux, so I cannot get any assistance from them.

---

### Post by him610 on 2018-12-31
Click on Settings > Printers 
Does it show up in Printers - localhost
If not, click the Add icon, fill in the blanks as necessary (including URL and Make and Model. HP develops most of the ink/laser printer drivers so you should find correct one.)
If it shows up, click on the printer icon> Properties, correct the information displayed (including URL) My own Device URL shows up as *socket://192.168.1.199:9100*

After a new (re)installation, it is normal to re-establish the correct configuration of attached devices. I think the same applies to full upgrades too. I find it convenient to assign a static IP address to my printers. You don't want a wondering IP address assigned by your router's DHCP for printers or fileservers.

---

### Post by merlinus on 2019-01-01
Thanks for the info.  I have assigned a static IP address to the printer.  The problem was that I did not have hplip installed, so the correct driver was not listed.

---

