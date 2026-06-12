---
title: "linux software raid"
date: 2008-06-05
forum: Hardware
---

### Post by bal3wolf on 2008-06-05
Ok i was having raid issues so i changed out a ide card and now my raid does not wanna work right and takes forever to boot.  I found out the reason 2 of my drives keep changing from /dev/sdd5 to /dev/sdd6 and every other reboot it changes back.  I can get the raid to work if i do these commands.  How can i add the uuid to the /etc/mdadm/mdadm.conf for each drive so it will always be able to find them even if they change their #.


sudo fdisk -l
sudo mdadm --stop /dev/md0
sudo mdadm --assemble /dev/md0 /dev/sdc5 /dev/sdb5 /dev/sda5 /dev/sdd5

---

