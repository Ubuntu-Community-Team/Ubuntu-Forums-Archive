---
title: "Sharing internet connection in VMware"
date: 2005-11-19
forum: General Help
---

### Post by Ubuntu_User on 2005-11-19
Hi. I just installed Ubuntu in VMware as a guest OS (host is Windows XP SP2).

I have other Windows guests and to share the host's internet connection with them, I simply enabled ICS (Internet Connection Sharing) for "VMware Network Adapter VMnet1", and used the host-only connection. In Windows guests, it's configured to automatically get the IP and the DNS address.

I use a crappy ADSL USB modem to connect to the internet.

How can I do the same with Ubuntu?

Thanks a lot. :)

---

### Post by manicka on 2005-11-19
System-->Administration-->Networking

I'm assuming you'll see VMnet1 in the connections.

Click on properties and set it to use DHCP

---

