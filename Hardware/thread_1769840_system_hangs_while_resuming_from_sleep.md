---
title: "system hangs while resuming from sleep"
date: 2011-05-28
forum: Hardware
---

### Post by wis38 on 2011-05-28
Hi,

I've a small home nas built with Ubuntu since 8.04, and  regularly updated at each Ubuntu refresh (after a while, just for  security).

After migrating to 11.4 from 10.10, I had the bad  surprise discovering my hardware is no longer able to come back from  sleep: the server simply hangs.

My hardware is an Intel D945GCLF2 motherboard with a Atom 330 dual core, with a RAID1 disk configuration.

I'm using extensively sleep mode + wake on lan to keep the server up only when needed, and save power consumption.

Before  the last update, everything was working perfectly... Now, system looks  going in stand-by correctly, but when resuming the attached screen  switches on but stays black, and network interface is now answering (no  ping, no other network services, although led on the switch indicates  the ethernet connection has passed from 10/100 -when in stand-by, to  allow wake-on-lan- to Gbit).

Sleep sequence in syslog has changed from the upgrade.

Before, it was:
May 26 15:25:39 HomeNAS anacron[15520]: Anacron 2.3 started on 2011-05-26
May 26 15:25:39 HomeNAS anacron[15520]: Normal exit (0 jobs run)
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> sleep requested (sleeping: no  enabled: yes)
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> sleeping or disabling...
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> (eth0): now unmanaged
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> (eth0): device state change: 8 -> 1 (reason 37)
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> (eth0): deactivating device (reason: 37).
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> (eth0): canceled DHCP transaction, DHCP client pid 14796
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> (eth0): cleaning up...
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> (eth0): taking down device.
May 26 15:25:43 HomeNAS avahi-daemon[857]: Withdrawing address record for 192.168.0.7 on eth0.
May 26 15:25:43 HomeNAS avahi-daemon[857]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.7.
May 26 15:25:43 HomeNAS avahi-daemon[857]: Interface eth0.IPv4 no longer relevant for mDNS.
May 26 15:25:43 HomeNAS avahi-daemon[857]: Interface eth0.IPv6 no longer relevant for mDNS.
May  26 15:25:43 HomeNAS avahi-daemon[857]: Leaving mDNS multicast group on  interface eth0.IPv6 with address fe80::21c:c0ff:fec0:686a.
May 26 15:25:43 HomeNAS avahi-daemon[857]: Withdrawing address record for fe80::21c:c0ff:fec0:686a on eth0.
May 26 15:25:43 HomeNAS NetworkManager[856]: <info> (eth0): carrier now OFF (device state 1)
May 26 15:25:45 HomeNAS postfix/master[1310]: reload -- version 2.7.1, configuration /etc/postfix
May 26 15:25:46 HomeNAS kernel: [31495.314775] PM: Syncing filesystems ... done.
May 26 15:25:46 HomeNAS kernel: [31496.421398] PM: Preparing system for mem sleep
[then, follows the wake-up sequence started the day after]

while now, it has:
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> sleep requested (sleeping: no  enabled: yes)
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> sleeping or disabling...
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> (eth0): now unmanaged
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> (eth0): device state change: 8 -> 1 (reason 37)
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> (eth0): deactivating device (reason: 37).
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1248
May 28 19:11:41 HomeNAS avahi-daemon[786]: Withdrawing address record for 192.168.0.7 on eth0.
May 28 19:11:41 HomeNAS avahi-daemon[786]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.7.
May 28 19:11:41 HomeNAS avahi-daemon[786]: Interface eth0.IPv4 no longer relevant for mDNS.
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> (eth0): cleaning up...
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> (eth0): taking down device.
May 28 19:11:41 HomeNAS avahi-daemon[786]: Interface eth0.IPv6 no longer relevant for mDNS.
May  28 19:11:41 HomeNAS avahi-daemon[786]: Leaving mDNS multicast group on  interface eth0.IPv6 with address fe80::21c:c0ff:fec0:686a.
May 28 19:11:41 HomeNAS avahi-daemon[786]: Withdrawing address record for fe80::21c:c0ff:fec0:686a on eth0.
May 28 19:11:41 HomeNAS NetworkManager[791]: <info> (eth0): carrier now OFF (device state 1)
May 28 19:11:41 HomeNAS postfix/master[1097]: reload -- version 2.8.2, configuration /etc/postfix
May 28 19:11:42 HomeNAS anacron[2179]: Anacron 2.3 started on 2011-05-28
May 28 19:11:42 HomeNAS anacron[2179]: Normal exit (0 jobs run)
[and of course, given the hang, in the syslog follows the boot sequence]

Any suggestion? Something I should look at more carefully?

In the meanwhile I'll disable sleep mode, but I'd like to recover it ASAP.

Thanks for the help,

Giorgio

---

### Post by wis38 on 2011-05-28
Hi,

a short update.

When system goes in stand-by automatically (at 8.04 time I made a custom install hybrid desktop + server, for allowing desktop interactive usage while having RAID1 with redundant boot and server services), stand-by correctly syncs disks, and wake-up works  ;)

Sleep does not work only when voluntarily sending the server to sleep with the command on GUI.

Workaround is much simpler now: just avoid sending to sleep manually, but wait timers doing it for me.

---

### Post by wis38 on 2011-05-30
It happened again, even with sleep on timeout... :(

I'll try to dig further this "long" week-end (here in France).

In the meantime, any quick suggestion to setup hybernation (or hybrid sleep) as default action instead of sleep?

Thanks

---

### Post by digger76 on 2011-07-09
Hi,

I'm having a similar problem with my server since migrating to 11.04.
I'm using rtcwake -m mem to supend my server during the night and wake up in the morning.
It worked perfectly until 10.10 but since 11.04 the server hangs in the morning and I have to reset the machine.
It is interesting, that rtcwake from the console works perfectly, but from the cron job I have the described behavior.

Did you find any solution for your problem so far?

---

