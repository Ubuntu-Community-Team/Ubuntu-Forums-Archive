---
title: "Home partition not recognized after upgrade"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by gforster on 2009-03-31
So I just upgraded to 9.05 (Jaunty) beta. I wiped my root partition and did a clean install. I left my old home partition alone. Install went fine, everything works really nicely.  

The problem is that my old home partition is no longer my home partition, it is a completely separate partition. How do I get it to recognize my old home partition as my partition?

---

### Post by Vico Vicario on 2009-04-01
You need to set it up in fstab:

1) reboot in failsafe mode as root

2) completely empty the new /home directory to reuse as mount point, but do not remove it. You need the empty dir. You can move the contents (user dirs) to /opt for example.

3) add old partition to /etc/fstab. For example

UUID=e4d5352b-e420-4d95-a24f-d0d7dd7c97d0 /home ext3 relatime 0 2

Use ls -l /dev/disk/by-uuid/ to find out UUID of your old partition. Choose correct filetype for your partition instead of ext3.

4) sudo mount -a

5) check if old /home is mounted

6) if so reboot

V.

---

### Post by gforster on 2009-04-01
Thank you. Worked like a charm. Whatever that means.

---

