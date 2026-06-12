---
title: "RAID help"
date: 2010-02-10
forum: Hardware
---

### Post by Lostdrifter0001 on 2010-02-10
Ok I have gotten fairly good with Ubuntu server but I'm having a hard time with this one. My company had purchased a new server (put together from parts off of Newegg.com). The point of the server is to become our first virtual server.

Because of this we do plan to setup a few production VM's on it but first I need to get Ubuntu installed. I have tried to do hardware Raid with a Highpoint 2320 on Ubuntu 9.10 64 bit, but that has fail. So now I want to try and setup software raid with Ubuntu 9.10 64 bit.

The plan is to take 2 80GB in RAID 1 for the host OS. Then use 3 750 in RAID 5 to house the VM's. I would like to mount /var to the 750 array as Vmware stores all of the VM's in /var.

Can anyone help me?

---

