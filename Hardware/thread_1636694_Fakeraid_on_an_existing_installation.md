---
title: "Fakeraid on an existing installation"
date: 2010-12-03
forum: Hardware
---

### Post by xfirestorm on 2010-12-03
Hello,

I've had experience with fake raids before, but always before the system was installed on many distributions, but never on Ubuntu. To make matters worse for me, this time I have an installed Ubuntu Server distro with a FakeRaid VIA VT6421 V-RAID controller. The RAID1 is built, but the system boots from the disk as if there was no RAID. Expected.
I would need to complete the RAID setup using dmraid, but how to do that, I do not have the option to reinstall the system. Can it be done in such a manner as to not loose data? I do have a backup, of the data, but the installation and all later installed apps and stuff will still be lost, and will have to do a re-install, not acceptable, it is an live server, used every day.

Thank you for your help!

Regards,
xfirestorm

---

### Post by ronparent on 2010-12-03
What output do you get in a terminal for 'sudo dmraid -ay'.

---

### Post by xfirestorm on 2010-12-06
Not a very good one:
```

root@mail:~# dmraid -ay
ERROR: via: invalid checksum on /dev/sda
ERROR: creating degraded mirror mapping for "via_ebhjjbhjcj"
root@mail:~# ls /dev/mapper/
control
```

---

