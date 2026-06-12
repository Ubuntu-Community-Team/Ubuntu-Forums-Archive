---
title: "HP xw8400 workstation suspend and hibernate don't work"
date: 2011-07-25
forum: Hardware
---

### Post by haynold on 2011-07-25
Hi:

I have a HP xw8400 workstation, which is (supposedly) ACPI-compliant for 32- and 64-bit systems. When I try to suspend under 64-bit Natty, the system just dies, though--blank, but not powered-down, screen, disks and fan keep running, and nothing but a hard reset will wake it up again. Suspending from console with GDM and nvidia disables didn't make a difference.

Do you have any suggestions?

The log is unspectacular, but the machine runs with quite a few modules active, notably nvidia and software RAID:
```
Jul 25 02:04:42 prometheus ntpdate[1583]: adjust time server 91.189.94.4 offset -0.089554 sec
Jul 25 02:04:43 prometheus kernel: [   33.230010] eth0: no IPv6 routers present
Jul 25 02:04:56 prometheus NetworkManager[856]: <info> sleep requested (sleeping: no  enabled: yes)
Jul 25 02:04:56 prometheus NetworkManager[856]: <info> sleeping or disabling...
Jul 25 02:04:56 prometheus NetworkManager[856]: <info> (eth0): now unmanaged
Jul 25 02:04:56 prometheus NetworkManager[856]: <info> (eth0): device state change: 8 -> 1 (reason 37)
Jul 25 02:04:56 prometheus NetworkManager[856]: <info> (eth0): deactivating device (reason: 37).
Jul 25 02:04:56 prometheus NetworkManager[856]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1537
Jul 25 02:04:56 prometheus avahi-daemon[858]: Withdrawing address record for 192.168.37.122 on eth0.
Jul 25 02:04:56 prometheus avahi-daemon[858]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.37.122.
Jul 25 02:04:56 prometheus avahi-daemon[858]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 25 02:04:56 prometheus NetworkManager[856]: <info> (eth0): cleaning up...
Jul 25 02:04:56 prometheus NetworkManager[856]: <info> (eth0): taking down device.
Jul 25 02:04:56 prometheus kernel: [   46.380428] tg3 0000:1f:00.0: PME# enabled
Jul 25 02:04:56 prometheus kernel: [   46.380495] tg3 0000:1f:00.0: wake-up capability enabled by ACPI
Jul 25 02:04:57 prometheus avahi-daemon[858]: Interface eth0.IPv6 no longer relevant for mDNS.
Jul 25 02:04:57 prometheus avahi-daemon[858]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::21a:4bff:fe53:f696.
Jul 25 02:04:57 prometheus avahi-daemon[858]: Withdrawing address record for fe80::21a:4bff:fe53:f696 on eth0.
Jul 25 02:04:57 prometheus NetworkManager[856]: <info> (eth0): carrier now OFF (device state 1)
Jul 25 02:04:57 prometheus postfix/master[1118]: reload -- version 2.8.2, configuration /etc/postfix
Jul 25 02:04:57 prometheus anacron[2024]: Anacron 2.3 started on 2011-07-25
Jul 25 02:04:57 prometheus anacron[2024]: Normal exit (0 jobs run)
Jul 25 02:04:58 prometheus kernel: [   47.556806] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro,commit=0

```

---

