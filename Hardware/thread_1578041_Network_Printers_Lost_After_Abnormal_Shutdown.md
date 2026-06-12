---
title: "Network Printers Lost After Abnormal Shutdown"
date: 2010-09-19
forum: Hardware
---

### Post by anezch on 2010-09-19
Hi,

I have an Ubuntu Lucid box in my office set as an application server. The application is actually accessed by the client via SSH. So for printing purpose, I installed each printer attached on each client as network printers in the application server.

The problem is when the application server shut down abnormally due to power failure, the network printers are gone. It was happened several times and I had to re-install all the printers one by one. Because of this I then keep a backup copy of /etc/cups/printers.conf so I can restore printers more easily.

How to prevent this from happening?

Thank you and sorry for my English :)

---

