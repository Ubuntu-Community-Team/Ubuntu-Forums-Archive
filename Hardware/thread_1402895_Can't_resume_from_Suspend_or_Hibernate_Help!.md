---
title: "Can't resume from Suspend or Hibernate: Help!"
date: 2010-02-09
forum: Hardware
---

### Post by maxxjr on 2010-02-09
After suspending, and trying to resume, the screen remains blank, and I cannot access the PC from the network.

After hibernating, the PC resumes, except I have no keyboard or mouse control, likely related to the error messages below:

[  809.786082] hub 3-1:1.0: hub_port_status failed (err = -62)
[  809.788081] hub 3-1:1.0: hub_port_status failed (err = -62)
[  809.790072] hub 3-1:1.0: hub_port_status failed (err = -62)
[  809.792063] hub 3-1:1.0: hub_port_status failed (err = -62)
[  809.826081] hub 3-1:1.0: hub_port_status failed (err = -62)
[  809.830079] hub 3-1:1.0: cannot disable port 1 (err = -62)
[  809.830084] pm_op(): usb_dev_restore+0x0/0x10 returns -62
[  809.830086] PM: Device 3-1.1 failed to restore: error -62
[  809.832080] hub 3-1:1.0: hub_port_status failed (err = -62)
[  809.836062] hub 3-1:1.0: cannot disable port 4 (err = -62)
[  809.836065] pm_op(): usb_dev_restore+0x0/0x10 returns -62
[  809.836066] PM: Device 3-1.4 failed to restore: error -62
[  809.836873] PM: Image restored successfully.


I can still access the PC from the network (which is how I got to the above log file).

Any suggestions on how to get one or both suspend and hibernate working?

Jaunty/9.04

Thanks!

---

