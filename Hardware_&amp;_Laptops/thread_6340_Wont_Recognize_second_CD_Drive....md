---
title: "Wont Recognize second CD Drive..."
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by animalstyle on 2004-11-27
I originally installed Ubuntu with a CDRW drive on the Secondary IDE as Master.  I then added a DVD-ROM drive to the Primary IDE on slave, with my hard drive as master.  The drive is recognized in my BIOS and even in the Device manager in Ubuntu, but it still doesnt show up when i go to Computer ---> Disks on the start menu.  Any suggestions?

---

### Post by jayclark on 2004-11-27
A DVD Player drive likes to be a slave instead of master.  In my experinece it will cause them not to register in the os etc. Have you tried to manually add it. I don't have Ubuntu running in front of me but it should be right-click> add new device and so on.

---

### Post by jdong on 2004-11-27
post the contents of /etc/fstab.

---

