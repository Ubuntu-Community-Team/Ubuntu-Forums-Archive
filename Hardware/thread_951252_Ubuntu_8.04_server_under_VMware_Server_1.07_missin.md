---
title: "Ubuntu 8.04 server under VMware Server 1.07 missing eth0 PC32net / Lance"
date: 2008-10-17
forum: Hardware
---

### Post by ipyakuza on 2008-10-17
Hello, I have VMware 1.07 server running on Ubuntu 8.04 server and this works great.  One of my guest machines is Ubuntu 8.04 server and it works fine but is missing eth0.  lsmod shows the NIC is AMD pcnet32 LANCE but I cannot ifup eth0 (says missing eth0).  I have it defined under /etc/network/interfaces with static ip yadda yadda.  Any ideas / starting point?  Other guest os's such as CentOS and FreeBSD 7 are working fine with eth0 (same bridged network settings)

---

