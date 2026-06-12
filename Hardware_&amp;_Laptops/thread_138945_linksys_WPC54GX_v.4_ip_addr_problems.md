---
title: "linksys WPC54GX v.4 ip addr problems"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by aosmith on 2006-03-02
so my card shows as being connected to my AP, it does not use authentication of any type.  my problem lies in the actual connection, i cannot obtain an ip via dhclient, static ip doesnt work either.  Im using a linksys WPC54gx (w/ srx) and ndiswrapper for the driver.  The wireless router is a linksys BEFW11S4.  Any ideas on why this connection isnt working?
thanks
-Alex

---

### Post by Q4U on 2006-03-03
Please post output of sudo dhclient. I guess you were successful in pinging your router and an external site (using the ip address) right? Thanks. Q4U

---

### Post by aosmith on 2006-03-03
nope cannot ping out to router or other sites.  output of dhclient says no valid leases in database - sleeping afte about 6 trys on 255.255.255.255:67

---

### Post by Q4U on 2006-03-03
Oh sorry I'm so stupid sometimes... I thought I read that you have problems getting the IP of your DNS!

Anyways, I suggest that you look at the very detailed guide hosted in this forum  ([https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29)](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29)). I tried this myself and I found extremely helpful.

Follow all the steps in the order suggested. Then, when you think you have diagnosed which link in the chain is broken, we can work from there. Hope this is helpful. Q4U

---

