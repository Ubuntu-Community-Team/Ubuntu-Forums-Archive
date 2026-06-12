---
title: "Ethernet Atheros AR8151 not working properly (have to disable/enable all the time)"
date: 2012-10-09
forum: Hardware
---

### Post by Repgahroll on 2012-10-09
Hello there.

At home I have a rj45 hub connected to an router (DHCP). It is working perfectly, however, I just changed the MoBo of one of my computers and this one has an Atheros AR8151 ethernet card. It works okay, however, when I'm downloading something, like a torrent file, it often just stops working and I have to disable and re-enable it on the graphical manager all the time to get it working again.

Any help on this?

Thanks in advance.

PS: The new MoBo is a G41MT-S2P. Very popular.
I have installed the 12.04.1 version today. Vanilla.
I'm posting below the return of lspci and ifconfig:
```
alan@alan-G41MT-S2P:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v1.0 Gigabit Ethernet (rev c0)
alan@alan-G41MT-S2P:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:f6:cf:a5  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::1e6f:65ff:fef6:cfa5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:196910 errors:0 dropped:2124 overruns:2124 frame:2124
          TX packets:156830 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:211354189 (211.3 MB)  TX bytes:19829623 (19.8 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:575173 (575.1 KB)  TX bytes:575173 (575.1 KB)

```

---

### Post by Repgahroll on 2012-10-09
Any help on this?

I would like to use Gnome 3, but sometimes when I'm browsing it stops working and there's no enable/disable option in Gnome 3.

Is it possible that this have something to do with a very long cable (50m) I plugged recently in this very same hub/switch? Maybe something is causing the switch to malfunction (inductance or sumpin)?

---

### Post by Repgahroll on 2012-10-10
=/ this forums used to be more helpful in the past...

I've tried the steps here: [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697) but didn't solve.

When the thing stops working, if I enable/disable the network it begins to work again, now I'm pretty sure this is a symptom of driver/module problem or network hardware malfunction (in this case the onboard card, I don't know if it could be the router or switch).

---

### Post by kurt18947 on 2012-10-10
Do a search in networking & wireless.  I believe chili555 has some input on this Atheros device.

---

### Post by Repgahroll on 2012-10-10
Yeah yeah, it seems I got it working, at least it worked today perfectly the entire day, seeding and downloading torrents @ >200Mb/s, I'm gonna let it work overnight and tomorrow I'll post a definitive conclusion.

It's strange, because it magically began to work properly after a reboot, so, for future reference, I'm linking both the chili555 and pytheas22 posts here:
[http://ubuntuforums.org/showpost.php?p=9446984&postcount=6](http://ubuntuforums.org/showpost.php?p=9446984&postcount=6)
[http://ubuntuforums.org/showpost.php?p=11057965&postcount=17](http://ubuntuforums.org/showpost.php?p=11057965&postcount=17)

Looks like the only additional step is to reboot, because only modprobbing doesn't work, maybe because of the previous active modules, dunno. Also, double-check the steps because the first time I was installing I've skipped the "./scripts/driver-select atl1c" line, which is crucial.

Thank you. Wait for my post tomorrow.

---

### Post by Repgahroll on 2012-10-11
Hello guys.
Yeah, looks like it's working properly now.
I'm gonna uninstall wicd.

---

### Post by Repgahroll on 2012-10-11
EDITED

In fact it's working.

Only problem I was having was due the installation of new kernels.

Thank you.

---

