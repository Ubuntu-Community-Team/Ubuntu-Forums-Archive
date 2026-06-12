---
title: "IBM R52 no hibernate"
date: 2008-09-04
forum: Hardware
---

### Post by sv1cdn on 2008-09-04
Dear all.
Been using 8.04 to an IBM R52 laptop with 512 RAM. At first Ubuntu created a swap partition of about 500MB and my laptop could turn into hibernate fine.
I changed this partition to 1024MB, edited fstab with the new id in order to load it automatically. Currently swap works ok but laptop fails to get into hibernate. Suspend works though, but it consumes power!
Any suggestion on what to troubleshoot? Help is limited, managed to discover something about s2disk but no lead...
As stated in other topics, Laptop brightness is not correctly set, even with the applet. It also shows in dmesg. But that is another less important problem.
Take care!

---

### Post by sv1cdn on 2008-09-05
Made it work!
Had to update /etc/initramfs-tools/conf.d/resume with the UUID of the new swap partition. Then run sudo update-initramfs -u and hibernate worked!

---

