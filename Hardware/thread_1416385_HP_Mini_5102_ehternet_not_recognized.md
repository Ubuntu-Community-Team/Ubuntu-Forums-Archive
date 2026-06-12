---
title: "HP Mini 5102 ehternet not recognized"
date: 2010-02-26
forum: Hardware
---

### Post by Icoo on 2010-02-26
Well long story short...there is no driver for my network card in the installer...my network card is apparently a Marvell 4381. I have seen the same problem by googeling over at Jolicolud and they were able too fix their installer (HP Mini 5102 is now officially supported - [http://getsatisfaction.com/jolicloud/topic/hp_mini_5102_wireless_wired_not_working_at_all](http://getsatisfaction.com/jolicloud/topic/hp_mini_5102_wireless_wired_not_working_at_all)). I tried to install Ubuntu but the installer can't find an ethernet port...any help is appreciated

---

### Post by jynyl on 2010-02-26
Same here; HP mini 5102, booting Ubuntu remix off USB, doesn't recognise ethernet or wireless connections.  (Both work fine on this netbook under Win7.)  Same problems with Kubuntu remix.

---

### Post by Icoo on 2010-02-27
> **jynyl said:**
> Same here; HP mini 5102, booting Ubuntu remix off USB, doesn't recognise ethernet or wireless connections.  (Both work fine on this netbook under Win7.)  Same problems with Kubuntu remix.

Well I solved it this way...install Ubuntu 9.10 via the Live CD, ethernet and wireless will not work. Then go to the Broadcom site, download the STL wireless driver, compile it and at leat wireless will be working (most important to me)...the ethernet support should be there in kernel 2.6.33...I will try to compile it and try it out...

---

### Post by jynyl on 2010-02-27
The HP specs say the 5102 has NIC from Marvell, model 88E8072.
It appears there is a driver available from the Marvell website ...
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)
(Haven't tried this myself yet.)

---

### Post by jabrande on 2010-03-14
> **Icoo said:**
> Well I solved it this way...install Ubuntu 9.10 via the Live CD, ethernet and wireless will not work. Then go to the Broadcom site, download the STL wireless driver, compile it and at leat wireless will be working (most important to me)...the ethernet support should be there in kernel 2.6.33...I will try to compile it and try it out...

It says in the README file for the STA driver that the driver is pre-compiled in Ubuntu, but I guess this version does not work. Did you make any modifications when you compiled and got the wireless working. I would be most grateful for tips on how to make my HP 5102 talk to the world!

---

### Post by jabrande on 2010-03-14
Great! It works without changes, just download the STA wireless driver from broadcom and compile it following the instructions in the README file. Thanks!

---

### Post by czr on 2010-03-21
Added a bugreport against the kernel here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543314](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543314)

Instead of using the bcm drivers, you can also do this on lucid:
```

apt-get install bcmwl-kernel-source

```

This will download the driver sources and build the wl driver using DKMS (so that it will be rebuilt on kernel upgrades).

The NIC issue can be fixed by using the 2.6.33 version of the sky2 driver, however, that would require manual kernel rebuild. I don't yet know of any easier way that wouldn't require changing away from the lucid kernel (which is 2.6.32).

---

### Post by DukeLuke on 2010-03-21
Below are the commands output, but Ethernet is not reconized!

   [SIZE=2][FONT=Arial, Helvetica, sans-serif]
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:26:82:5a:8c:9f  
          inet6 addr: fe80::226:82ff:fe5a:8c9f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

sudo lshw -c network

  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:5a:8c:9f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:94200000-94203fff

I am a newbie to Linux and unsure how to compile kernel code yet...


[/FONT][/SIZE]

---

### Post by ronzo on 2010-03-22
Does anybody know if both NICs (wired and wireless) will work out of the box with the 2.6.33 kernel?

Do other components NOT work under lucid using the 2.6.32 kernel?

Thanks a lot in advance!

---

### Post by mtinman on 2010-03-25
> **jynyl said:**
> The HP specs say the 5102 has NIC from Marvell, model 88E8072.
It appears there is a driver available from the Marvell website ...
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)
(Haven't tried this myself yet.)

I did try this, and the installer shell program provided by Marvell (which, btw, is written for Fedora, with the 2.6 kernel) ends up in an error. Also, my HP Mini 5102 (Product: FN100UT#ABA) uses the 88E8059 driver, according to my Windows XP device manager. Hope this helps.

---

### Post by jynyl on 2010-04-04
The instructions on this posting; [http://ubuntuforums.org/showthread.php?t=1368699]("http://ubuntuforums.org/showthread.php?t=1368699") seemed to work for wireless on a 5102 here.

---

