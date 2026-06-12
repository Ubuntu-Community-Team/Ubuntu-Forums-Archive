---
title: "custom hal quirks for bug workarounds?"
date: 2008-04-27
forum: Hardware
---

### Post by Randall on 2008-04-27
Hi,

Two questions I hope someone can help with:

1- I just re-installed my [laptop]("https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV2600CTO") with Hardy. I had a nice workaround for [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/81767") in Gutsy which made my laptop suspend-to-ram oh so sweetly reliable.

Now, in Hardy, this fix no longer works. I think I have tracked this down to the fact that gnome power management and hal are taking control of acpi events, so the scripts in /etc/acpi/resume.d/ are no longer executed.

So, how can I get hal to execute my nice little 2-line script to fix this keyboard bug?

2- hal appears to have lots of workarounds for existing bugs which is calls "quirks". How can I get this info back to the relevant people so that in the future I don't have to hack the acpi/hal/whatever to get it to work again?

THanks,
Randall.

---

### Post by ryuko2002 on 2008-04-29
I'm on the same situation. There is related information here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/83243](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/83243)
"Solution:
  sudo sh -c 'echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind'
  sudo sh -c 'echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind'

You have to put the two above lines into the Power Manager configuration (/etc/pm/hooks/). If you are using diferent suspend script put it there."
The old solution was unbinding and then binding using scripts in /etc/acpi/suspend.d and resume.d, but I haven't figured out where to put those lines now. /etc/pm contains directories config.d, power.d and sleep.d but they are all empty

---

