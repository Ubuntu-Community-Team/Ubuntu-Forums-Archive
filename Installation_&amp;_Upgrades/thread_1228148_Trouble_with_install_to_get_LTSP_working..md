---
title: "Trouble with install to get LTSP working."
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by wilman100 on 2009-07-31
Hi, Have downloadedubuntu -8.10-alternate-amd64.iso and run it to installan LTSP server.

I only have one network card - intended to be for the clients.

Did get one error message part way through.....

No interface for LTSP dhcpd config found. Please configure the file /etc/ltsp/dhcpd.conf manually.  What should be changed in it.

I tried connecting in via PXE on i386 machine but although ip address seems to be picked up client states............

TFTP
TXE-T01 : File not found.
PXE - E3B: TFTP Error - file not found

My clients are all i386. Have tried running sudo ltsp-build-clint arch i386.

I get root directory /opt/ltsp/amd64 already exists with an additional restricted univers multivers  message.

Can you help ?

Regards


Dave

---

### Post by smaclean on 2009-09-08
You need to perform additonal configuration steps to get LTSP working with a single NIC. 2 NIC's are the norm and preferred because of the amount of traffic that can be generated dependign on the amount of thin-clients connecting to your server. If you must use one NIC, these directions might help. Note, the guide on the link below is using Red Hat, the file locations may differ on other distro's.

[http://www.k12ltsp.org/install.html#single_card](http://www.k12ltsp.org/install.html#single_card)

---

