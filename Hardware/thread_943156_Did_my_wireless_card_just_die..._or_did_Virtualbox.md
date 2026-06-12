---
title: "Did my wireless card just die... or did Virtualbox eat it?"
date: 2008-10-09
forum: Hardware
---

### Post by Ubuntiac on 2008-10-09
My system was running just peachy.

Whenever it's running well though I seem to get urges to do things that break it. Here's my latest:

Wireless works.
[LIST=1]
[*]Decide to try Intrepid beta in a VM. Install virtualbox. Run Intrepid ISO in Virtualbox. Pretty.
[*]Quit virtualbox. Uh oh. Where's my wireless? Reboot.
[*]Hmmm... wired connections are working. Network manager doesn't show any wireless devices.
[*]Quick! Uninstall Virtualbox. Hmmm... still no wireless. Hmmm... dmesg still says something suspiciously Virtualbox sounding:
[/LIST]
> [   63.839774] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   63.839780] vboxdrv: Successfully done.
[   63.840222] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   63.840229] vboxdrv: Successfully loaded version 1.5.6_OSE (interface 0x00050002).


...and ifconfig isn't seeing my atheros card:
> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:d1:88:59:b4
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe88:59b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:60000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:48327928 (46.0 MB)  TX bytes:2916020 (2.7 MB)
          Base address:0x40c0 Memory:e0300000-e0320000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1000 (1000.0 B)  TX bytes:1000 (1000.0 B)


Heck, even lspci doesn't seem to see it...

Any ideas anyone?

---

