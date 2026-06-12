---
title: "ACPI update messed up the internet connection"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by oygle on 2009-01-17
I have been trying to get [ppp0 and eth0 going on Intrepid with NM 0.7]("http://ubuntuforums.org/showthread.php?t=1022569") , and did, at least get eth0 'up' and the interface all working, for the past three days. It did take some CLI commands, but it was working okay with NM.

Last night, there was a ACPI update, a very small file, applied that.

Internet was still going okay afterwards, and also eth0 was up.

Rebooted this morning and could not get internet at all, network manager was having problems with the ppp0 connection, .. just no go.

I unzipped some backups, and the only files that have been changed in the whole filesystem were from the ACPI update.  :(

Now I know from NM bugs, that if eth0 is loaded first, then ppp0 will not work, and that seemed to be the problem from syslog, but why the change ??

Had to disable the lan card, but even then, the drivers for it were still being loaded

> Jan 18 11:02:04  kernel: [   22.603256] sky2 eth0: enabling interface
Jan 18 11:02:04  kernel: [   22.605412] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 18 11:02:04  kernel: [   24.161554] ACPI: WMI: Mapper loaded
Jan 18 11:02:04  kernel: [   24.289246] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both

Notice it is ACPI that is doing that.

So, what happened in the ACPI update to _force_ a driver to be loaded for a device that has been disabled in bios ?  This didn't happen beforehand, and it certainly messed up network manager.

After a number of reboots, and trying things, this, fortunately worked

```
sudo /etc/init.d/NetworkManager restart
```

Oygle

---

### Post by oygle on 2009-01-17
Please see [http://ubuntuforums.org/showthread.php?t=1042755](http://ubuntuforums.org/showthread.php?t=1042755)

---

### Post by bapoumba on 2009-01-18
Threads merged, and bump.

---

### Post by oygle on 2009-01-18
Booted up today, and now it's okay. Work that out.  :confused:

---

