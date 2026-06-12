---
title: "Samsung n210 wireless problems"
date: 2011-04-01
forum: Hardware
---

### Post by Parasitic on 2011-04-01
I am sure you guys have seen this thread a thousand times already by looking at google search results, but I really need tailored support here. 

I bought a samsung n210 for my mum formother's day this sunday and I have scrubbed off the bloatware windows 7 rubbish and installed ubuntu 10.10 (not netbook version, although wish I had tried the netbook release at this res) and OOTB wireless is not working, I have tried a few things that google turned up so the driver is a little off, I think all I need is a working driver.

Anyway, here is some code:

```
lspci -nn | grep Network
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)
```


```
sudo lshw -C network
[sudo] password for mandy: 
  *-network DISABLED      
       description: Wireless interface
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:9a:7d:c1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:40:b9:6e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f0200000-f0203fff ioport:3000(size=256)

```

Please help!

Thanks in advance!

---

### Post by Parasitic on 2011-04-01
Too add a bit more info the wireless is not picking up networks, and I know there is at least 6 my other devices pick up, also, it won't connect if I set it manually. "enable etworking/wireless" is obviously ticked in the applet menu and I have tried editing the disable wireless by default file to keep it on....

---

### Post by Parasitic on 2011-04-01
```
root@mandy-N210:/home/mandy/Desktop/rtl8192e_linux_2.6.0011.1029.2009# modprobe r8192e-pci
FATAL: Error inserting r8192e_pci (/lib/modules/2.6.35-28-generic/kernel/drivers/staging/rtl8192e/r8192e_pci.ko): No such device

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have tried this twice: [http://ubuntuforums.org/showthread.php?t=1391750](http://ubuntuforums.org/showthread.php?t=1391750)

---

### Post by Parasitic on 2011-04-02
Bump for justice!

---

### Post by Parasitic on 2011-04-02
in /lib/modules I have 2 kernels lying about, is that normal?

/lib/modules/2.6.35-28-generic

/lib/modules/2.6.35-28-generic

same for firmware etc...

how do I know which is in use?


I'm new to this, can't you tell?

Desperate to get wireless working, I have also tried installing an updated realtek driver, in addition, I get a message when the computer boots about the driver but it's gone before I can read it.

---

### Post by Parasitic on 2011-04-02
Somebody please help I feel quite alone here, needs to be ready by tomorrow.

---

### Post by Parasitic on 2011-04-02
SOLVED!

I feel like such a fool, it seems during installation conflicting drivers were installed or something went wrong.

Using the "Additional Drivers" applet I removed both and then installed ONE again...

presto, worked straight away. All is well.

For anyne having this problem, before you do anything do try this!

---

