---
title: "When updating to 9.10 my computer."
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by BradleyUK on 2009-11-01
Crashes when it was installing the update and now wheni try and reboot the system it comes up with this error:

one or more of mounts listed in /etc/fstab can not mount yet:
(Esc For Recovery Shell)

```
/: waiting for /dev/disk1/by-uuid/aa177f7d-32a6-4cd8-ab4e-d64cc168e5fc
/tmp:waiting for (Null)

Swap: waiting for uuid=ce1f45a6-5790-4efa-a7fc - a0e3b33bfd60
```

I pressed Esc to get recovery shell and this comes up...
```

Mountall: cancelled
init: mountall main process (764) terminated with status 1

General error mounting filesystems
A Maintenance shell will now be started
(Control - D) will terminate this shell and re-try)
Give root password for maintenance.
```

When I try to type the root password it won't type it on screen only enter & esc work.

How do you solve this problem? :(

**RESOLVED**

---

### Post by BradleyUK on 2009-11-01
anyone know how to fix this?

---

### Post by p0cky84 on 2009-11-01
Upgrading form any Ubuntu to 9.10 is a bitch.
You might find some solution out here, but the best shot is to just do a new clean install.

Also; way to early bump. ~ **Shame on you.**  >:@

---

