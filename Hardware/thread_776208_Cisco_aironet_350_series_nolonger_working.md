---
title: "Cisco aironet 350 series nolonger working"
date: 2008-04-30
forum: Hardware
---

### Post by lala25 on 2008-04-30
Hi I have just upgraded my Toshiba 1400-s151 from 7.10 to 8.04.  It has a Cisco aironet 350 series (air-pcm350) wireless card to connect to the network.  After the upgrade the cisco doesn't seem to be recognized or active.  at start up the lights flash for less than a second and then nothing.  I did notice some text message at boot up.  Not sure it is related, but it is as follows:

PXE - E61 media test falure, check cable
PXE - M0F exiting intel boot agent.

Otherwise things seem to have gone fine.  Please help me get my wireless working.

I typed in lspci -v command and got this
00:0a.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f7efe000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at eec0 [size=64]
        Memory at f7ec0000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <access denied>

and the lshw -C network shows:

  *-network               
       description: Ethernet interface
       product: 82551QM Ethernet Controller
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:00:39:c7:22:af
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.105 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

ifconfig shows:
eth0      Link encap:Ethernet  HWaddr 00:00:39:c7:22:af  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fec7:22af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22644076 (21.5 MB)  TX bytes:4135417 (3.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:180030 (175.8 KB)  TX bytes:180030 (175.8 KB)

and iwconfig shows
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

Thank you.

---

