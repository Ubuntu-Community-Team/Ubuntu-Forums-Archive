---
title: "Jaunty &quot;suspend failed&quot; bug with battery saving script"
date: 2009-04-29
forum: Hardware
---

### Post by Axx83 on 2009-04-29
I filed a bug for Jaunty, as many users like me are experiencing this bug:

[https://bugs.launchpad.net/ubuntu/+bug/368961]("https://bugs.launchpad.net/ubuntu/+bug/368961")

> If there's battery saving script putted in /etc/pm/sleep.d that includes a line such as:

echo 6 > /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level

the notebook fails to suspend on Jaunty

the message in pm-suspend.log is:

/etc/pm/sleep.d/90-save_power.sh suspend suspend: /etc/pm/sleep.d/90-save_power.sh: line 16: echo: write error: Resource temporarily unavailable
Returned exit code 1.

where line 16 is exactly:

echo 6 > /sys/bus/pci/drivers/iwl3945/0000:03:00.0/power_level

the notebook suspended fine on Intrepid with the same script.

What other infos should I include ?

Thanks

Please contribute to this bug to solve it as fast as possible.

---

