---
title: "Get data from RAID 0 in different PC"
date: 2010-03-05
forum: Hardware
---

### Post by cpressland on 2010-03-05
Hey guys,

We've got a server thats died at work and I've been tasked with getting the data off. The problem is corosion on the motherboard, gotta love Dell. The Hard Drives are fine however they're in a RAID0, we don't have another motherboard to hand so I want to slam the drives into another PC with Ubuntu installed and try and get the data off them. Originally the drives were running with CentOS but OS shouldn't matter as I'm only going to be dealing with the filesystem.

Any ideas/hints guys?

Thanks

CPressland

---

### Post by paulisdead on 2010-03-05
Were these running on a RAID card in the box, or even an onboard RAID controller, or was it software RAID?  If it's just linux software RAID, you probably just need to install mdadm, and plug the drives in and the system should detect something at /dev/mdX.  You mentioned it's Centos, so you may need to install the lvm packages as well.

If it's hardware RAID, you'll need the same RAID card or motherboard to bring the drives up, typically.  Sometimes you can get away with just a really similar card.

---

### Post by psusi on 2010-03-05
If it is an Adaptec hardware raid, I think the dmraid utility can recognize their metadata and treat them like a fakeraid.

---

### Post by cpressland on 2010-03-05
It was running on the Onboard Controller, so far I've managed to get the drives detected with lvm and mdadm. Now it's just a quick copy command and off we go.

Thanks guys.

---

