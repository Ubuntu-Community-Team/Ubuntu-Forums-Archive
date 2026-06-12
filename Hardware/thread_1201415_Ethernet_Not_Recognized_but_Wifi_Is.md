---
title: "Ethernet Not Recognized but Wifi Is"
date: 2009-07-01
forum: Hardware
---

### Post by trentscott4 on 2009-07-01
I just installed Ubuntu 9.04 on my HP Mini 110-1033CL and it seems my Ethernet jack is not being recognized.  I can connect to the Internet via Wifi, but wired does not work (even after reboot with cable plugged in).  Here is the output of 'ifconfig':

```
eth0      Link encap:Ethernet  HWaddr 00:25:56:3c:20:a7  
          inet6 addr: fe80::225:56ff:fe3c:20a7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:208
          TX packets:26 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6567 (6.5 KB)  TX bytes:4663 (4.6 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

It seems that eth0 is my wifi. Any ideas?  Thanks.

---

### Post by trentscott4 on 2009-07-01
Still need help.  The output of lshw -C network says my Ethernet card is unclaimed/disabled:

```
8.9.108 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:f9:71:d7:81:42
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
Here's what I know about this card:

```
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:1062] (rev c0)
	Subsystem: Hewlett-Packard Company Device [103c:308f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at ec80 [size=128]
	Capabilities: <access denied>
```

---

### Post by walt.smith1960 on 2009-07-01
):PMy first post.  I'm a non-IT type hobbyist.  I had the same thing with Asus Eee1005HAB.  WiFi adapter was not recognized but a TrendNet USB ver.3.1 was recognized.  Wired LAN was not recognized.  I did update, upgrade, then backplane drivers. The integral WiFi adapter is now recognized.  I was wondering about NDISwrapper. Will NDISwrapper work on a LAN adapter?

---

### Post by trentscott4 on 2009-07-02
bump

---

### Post by makinglife on 2009-07-03
1.)Well your running 9.0.4 im not so good with WIFI cards try Re-Installing your OS.
I did that and it make it working.

2.) go to system administration hardware drivers it might just be disabled.

3.) UPDATE your ubuntu if you can get on some wifi network. if your neighborers have some then take it from them and use it for the moment

Thanks
--
-MakingLife

---

### Post by rtb on 2009-07-11
To be clear, the original poster (trentscott4) said that wireless was working but ethernet is not.  I can confirm I've seen the same thing on another HP Mini 110 with Ubuntu Netbook Remix (UNR) 9.04.

  Strange thing is, HP's Mini Mi (another flavor of Ubuntu) does work.  The driver used there is atl1e, version 1.0.0.6, for the kernel 2.6.24-22-lpia.

  The atl1e module available in UNR 9.04 is version 1.0.0.7-NAPI for kernel 2.6.28-13-generic.

  I first tried "modprobe atl1e".  I next tried adding atl1e to /etc/modules and rebooting.  Neither worked.

---

### Post by rtb on 2009-07-11
Cross reference to [thread 1206649]("http://ubuntuforums.org/showthread.php?t=1206649"), which appears to address the same problem.

---

