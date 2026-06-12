---
title: "Highpoint RocketRAID 2640x1 RAID installation woes"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by CharlesA on 2009-10-03
Hello,

I installed ubuntu 9.04 on my file server but I cannot get the raid driver to install into ubuntu.

The driver on the highpoint site [here]("http://www.highpoint-tech.com/usa/bios_rr2640.htm"), is for Ubuntu 8.0, not 9.04. I'm not quite sure how to build the driver to the current version of the kernel.

I am running Ubuntu Server 9.04 kernel version 2.6.28-15-server.

I'm totally lost, any help would be appreciated.

Thanks!

EDIT: Nevermind, I finally figured out that I could use the open source driver. I need some more practice with ubuntu.

---

### Post by inobe on 2009-10-03
i am surprised the array wasn't automatically detected during the setup ?

---

### Post by CharlesA on 2009-10-03
> **inobe said:**
> i am surprised the array wasn't automatically detected during the setup ?

It wasn't sadly. The only thing that was detected was the regular SATA drive. The installer did download a raid driver (I think) but it didn't work I'm guessing, since I didn't see the array after the install completed.

I'm just glad I was able to get it working.

---

### Post by inobe on 2009-10-03
thanks for sharing your experiences and how you solved the problem:)

---

