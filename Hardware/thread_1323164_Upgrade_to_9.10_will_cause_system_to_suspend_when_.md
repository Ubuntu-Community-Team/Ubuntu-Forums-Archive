---
title: "Upgrade to 9.10 will cause system to suspend when idle"
date: 2009-11-11
forum: Hardware
---

### Post by bdw on 2009-11-11
Greetings!

I upgraded to Ubuntu 9.10 and when the system is idle for a period of time, about 20 minutes, it will suspend.  I am using KDE and PowerDevil, and I'm using the Performance profile which is set to "Do Nothing" when the system is idle.  Powerdevil is the only power manager running, powersaved is not running.

I cannot find any config file that will control this.  The only solution that I can find is to uninstall the "pm-utils" package and that will prevent the system from suspending when idle.  Of course, I still want to have the monitor powered off automatically when idle but not have the whole system suspend as this machine is being used as a print server as well as a desktop system in my home network.

acpid is running, but I couldn't find any config file that would control the idle time.

I'm really at a loss as how to resolve this problem.  Any hints or am I missing something else?  :confused:

---

### Post by kio_http on 2009-11-11
Look in KDE system settings, there's probably an option somewhere!

---

### Post by bdw on 2009-11-11
> **kio_http said:**
> Look in KDE system settings, there's probably an option somewhere!

I've looked in KDE system settings but I didn't see anything else other than PowerDevil for power management.  In Hardware I did see the HAL Power Daemon but there's no way to configure that, it would seem.

I'm still not able to find either the HAL configuration file or any other configuration file that is triggering the suspend when idle condition and I'd really like to stop that from happening...:mad:

---

