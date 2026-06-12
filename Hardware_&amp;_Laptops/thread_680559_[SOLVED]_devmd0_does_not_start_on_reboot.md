---
title: "[SOLVED] /dev/md0 does not start on reboot"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by a_posse_ad_esse on 2008-01-28
I've created a RAID-0 array through

```

sudo mdadm --create /dev/md0 --level=0 --raid-devices=6 /dev/hdb1 /dev/hdb2 /dev/hdb3 /dev/hdb4 /dev/hdc4 /dev/hdd1

sudo mdadm --scan --detail >> /etc/mdadm/mdadm.conf

```

The result is an array that works fine when created, or when "sudo mdadm -As /dev/md0" is run.  It does not start on its own after a reboot, however.  I am unsure why.  Is this a bug?

Thanks

---

### Post by a_posse_ad_esse on 2008-02-02
Any ideas?

---

### Post by a_posse_ad_esse on 2008-02-12
The new kernel update fixed the problem.

---

