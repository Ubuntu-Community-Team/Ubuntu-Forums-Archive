---
title: "Wake on LAN Stopped Working in Hardy"
date: 2008-07-31
forum: General Help
---

### Post by slowtrain on 2008-07-31
I've been trying to get Wake on Lan (WoL) to work on my office machine.  I was able to wake the computer from my home computer in Gutsy, but once it was awake, it lost its Internet connection--a Gutsy suspend issue.  I then tried moving to Hardy.  Here, my computer does not lose the Internet when woken from suspend, but cannot be woken using WoL.

As far as I can tell, I have everything configured correctly.  ethtool eth0 indicates this (both before and after suspend):
Wake-on: g

I've turned on PCI wake support in the BIOS and have tried waking with WoL with timed wake both on and off in the BIOS.

cat /proc/acpi/wakeup shows everything disabled, so I've tried waking after this command, which enables PCI0 and HUB0 (no explicit NIC device in wakeup), a command that worked for another ubuntu user:
grep 'PCI0.*enabled' < /proc/acpi/wakeup >/dev/null ||  grep 'PCI0.*enabled' < /proc/acpi/wakeup >/dev/null ||  echo PCI0  > /proc/acpi/wakeup

I have turned on blocking of connections from my home computer in firestarter and then checked to see whether the "Events" window shows my attempt to connect to port 7 using wakeonlan from my home computer at least while my office computer is awake.  Yup, the Events do show the connection attempt, so apparently there is a clear path to the computer, at least when firestarter blocking for my home computer is turned off.

I have tried wakeonlan both directing the output directly to my office computer ipaddress and to nearby machines (at least according to cat /proc/net/arp).

Any thoughts on what else I might try?  What stumps me is that WoL used to work in Gutsy (at least a couple times I tried it) but now in Hardy it doesn't.

Peter

---

### Post by reeja on 2008-08-20
Just to bump it up...

I do have the same problems - with my 7.10 Ubuntu server installation WOL worked from shutdown (even with Xen installed). After upgrading to 8.04 WOL stopped working. 

I have an nForce 500 chipset, i.e. my NIC is using the forcedeth driver.

Any ideas? And yes - I have read through all the threads, including halt options, ethtool, wakeonlan, reverse MAC... to no avail :(

Kind regards,
reeja.

---

### Post by amitkher on 2008-08-20
Actually ethtool reporting g for wol is sometimes not enough. Try shutting down by
```

sudo /usr/sbin/ethtool -s eth0 wol g
sudo /sbin/halt -hdp

```

Check whether you can wake it now.

---

### Post by reeja on 2008-08-26
Hi amitkher,

I tried the commands you described - though the halt script in /etc/init.d/ is configured with exactly these parameters: WOL from S5 still does not work :(

I think I will try with some acpi/apm boot options. Does anybody got some ideas in this direction?

Greetz,
reeja.

---

