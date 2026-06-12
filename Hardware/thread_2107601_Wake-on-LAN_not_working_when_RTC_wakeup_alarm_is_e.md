---
title: "Wake-on-LAN not working when RTC wakeup alarm is enabled"
date: 2013-01-22
forum: Hardware
---

### Post by joe_s on 2013-01-22
I'm trying to set up Wake-on-LAN _and_ RTC wakeup alarm on a recycled server that has Ubuntu 12.04 LTS installled. The hardware is based on a seasoned Gigabyte 7IX motherboard with PCI 2.2 and ACPI supported.

The machine is set up to wake up 15 minutes before backup time every night, using /sys/class/rtc/rtc0/wakealarm as described, for example, here:
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
The last backup job terminates by running a script that re-writes wake alarm info for the next day to the BIOS, then powers down the server. All of that is working nicely.

Now, sometimes there's a need to remotely wake up the server on demand to perform some maintenance work. That's why WOL came into play. I was able to set that up as well, by adding a line
```
ethtool -s eth0 wol g
```to a custom shutdown script. Works like a treat -- for as long as RTC wakeup alarm is _not_ active. However, with RTC wakeup enabled, WOL ceases to function. So, while it looks to me like the two wakeup methods are mutually exclusive, none of the many related documents and forum threads I've been reading in the past two days was able to shed any light on this.

Is this a known limitation? Am I missing something that needs to be configured before both RTC wakeup and WOL can be used in combination?

Thank you in advance for any tips or pointers!

---

### Post by joe_s on 2013-01-25
Actually, what I found is a workaround, rather than a solution:

I've created a cron job on another server (which is running 24/7) in the same network. The cron job sends a magic packet to the first server (the one I want to wake up) at pre-defined times.

That way I no longer need to set up RTC wakeup on the first server, but only WOL. This gives me both options: Having the server wake up at pre-defined times AND waking it up on demand.

---

### Post by tgalati4 on 2013-01-25
Sounds like a bug (or feature) of the ACPI BIOS.  Since this is an older machine, there may be a firmware update that you can reflash the motherboard with.  WoL is tricky is the best of circumstances.  It's possible when RTC wake is turned on it disables the pci bus that the network card is connected to.  You could use acpitool to explicitly leave that bus powered all the time.  That is my guess as to what is going on.

It's possible that that is the correct behavior.  If you are using RTC to wake the machine, you don't want ANYTHING else to wake it until the appointed time.

---

### Post by joe_s on 2013-01-25
Thanks. I tried using acpitool to leave the PCI bus powered (enabled) -- unfortunately to no avail. Maybe you are right that it's intended behaviour. Anyway, I'm happy with my workaround.

---

