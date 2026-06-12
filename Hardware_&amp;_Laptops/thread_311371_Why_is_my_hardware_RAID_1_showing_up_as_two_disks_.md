---
title: "Why is my hardware RAID 1 showing up as two disks in setup?"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by jmillikin on 2006-12-02
I'm trying to install 64-bit Dapper to a server. The server seems to have hardware RAID - I can access a RAID setup screen from the bios, and set my drives to be a mirror. However, the Ubuntu setup still sees both drives. I'm using the 'alternative' installation disk.

---

### Post by PilotJLR on 2006-12-02
What type of server, and what type (brand/model) RAID controller.

I've not experienced this issue, except for machine with "fake" software RAID  controllers. In other words, the presence of a hardware controller card does NOT mean the RAID activity is done on the card itself.

---

### Post by jmillikin on 2006-12-02
That might be the problem - it's a fairly cheap controller, nVidia CK804. I've never heard of a fake RAID controller before.

---

### Post by PilotJLR on 2006-12-02
I actually have the exact same controller as you! Yeah, it's loosely called "fake raid".

A true hardware raid controller should cost $400 and up.

The solution here is to setup a software RAID setup using mdadmn. This is essentially what the controller would do using the Windows-drivers anyway.

---

