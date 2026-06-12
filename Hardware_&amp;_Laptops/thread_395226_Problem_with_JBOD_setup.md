---
title: "Problem with JBOD setup"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by FrostDust on 2007-03-27
I recently bought a RAID card ([http://www.compusa.com/products/product_info.asp?product_code=329470]("http://www.compusa.com/products/product_info.asp?product_code=329470")) and attached two hard drives to it, 20 GB and 8 GB in size, in JBOD mode. For normal operations, it works fine. However, whenever I try to do the following things, the drive becomes unreadable, until I reboot the system:

[LIST][*]fdisk, even when activated during start up[*]Copy amounts of data 500 MB or more in size to another drive[*]Burn a large amount of data from the drive to a disc using K3B
[/LIST]
Additionally, trying to share the drive on DC++ results in the the program (ldcpp) crashing immediately, although downloading to the drive works fine.

I have my /home on a 40 gb drive, and the rest of my file system on a 30 GB drive. Is this a driver/hardware problem, or would switching to something like LVM be a wise solution? Or is something totally different the answer?

---

