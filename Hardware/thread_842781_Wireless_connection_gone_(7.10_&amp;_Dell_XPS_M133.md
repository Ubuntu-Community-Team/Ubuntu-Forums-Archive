---
title: "Wireless connection gone (7.10 &amp; Dell XPS M1330)"
date: 2008-06-27
forum: Hardware
---

### Post by stash1071 on 2008-06-27
Hi, I recently purchased a Dell XPS M1330 laptop that came with Ubuntu Gutsy 7.10 pre-installed and my wireless connection was working fine.  

I ran Update Manager and had some packages installed (do not recall which but there were a lot), rebooted, and now I do not see a wireless connection option under Network Settings.

I've found several posts on this subject, but none seem to work for me.  I'm not that far along settings things up that I could revert back to the OS from the CD, but I'd be forever afraid to install updates again.

Here's a listing of the commands I found to run:

```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

$ lshw -C network

  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:5d:a6:4c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 latency=0 module=tg3 multicast=yes

$ lspci | grep -i wireless
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

The wireless driver appears to be detected just fine:

```

$ lsmod | grep ipw
ipw3945               119840  0 
ieee80211              35656  1 ipw3945

$ dmesg | grep -C 4 -i ipw
[   14.436000] ieee80211_crypt: registered algorithm 'NULL'
[   14.444000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.444000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.512000] Linux video capture interface: v2.00
[   14.532000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp
[   14.532000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   14.532000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.532000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   14.532000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection

```

But the device does not stay up:

```

$ sudo ifup eth1
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

```

Any help would be greatly appreciated here.  This seems to happened to several others who've been able to resolve the problem, so I wonder what makes my case different.

Thanks in advance

---

### Post by stash1071 on 2008-06-29
I was able to get a wireless connection back in the network manager, but am unable to detect any networks, so some progress at least.

I followed the instructions here (even though my problem was not LED related):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090)

I upgraded to Ubuntu 8.04 then:

```

$ sudo apt-get install linux-backports-modules-hardy
$ sudo rmmod iwl3945
$ sudo modprobe iwl3945
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
prystasj@dell-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by fabbaz on 2008-09-16
and did it work with 8.04?
my gf's m1330 has the same frustrating bug.
i didn't so far upgrade any of my systems on 8.04 because of hardware incompatibilities - but maybe it would be the best choice for this particular notebook.
thanks and good luck!

---

