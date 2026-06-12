---
title: "network cable to recognized"
date: 2022-08-01
forum: Hardware
---

### Post by jgw on 2022-08-01
I bought a Gigabyte GA-78LMT-USB3 rev: 4.1 motherboard and am trying to set it up.  Everything is working but the internet.  I have plugged in the lan cable but its not recognized (the little light doesn't come on and there is no connection).  I checked the bios and the lan is activated.  They system setup knows something is plugged in and the system network identity says "wired connection 1".  As soon as the system boots up the system starts a constant beeping tone so I knows something is wrong.  I plugged the internet cable into another machine and it worked fine.  I searched for a solution on the net and it seems this happens quite a bit but I never found any solutions that worked for me.  

```
 sudo lshw -C *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 06
       serial: 94:de:80:0f:f3:8d
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-41-generic firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 ioport:ee00(size=256) memory:fddff000-fddfffff memory:fddf8000-fddfbfff
greg@movies:~$ 

```

Any help would be appreciated.

Thank you................

---

### Post by #&amp;thj^% on 2022-08-01
Something is up then, I have the very same Nic
```
inxi -N
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi


```
With out internet I'm not sure how to help you, do you have a wifi dongle that works on linux?

---

### Post by TheFu on 2022-08-01
For that NIC we need to look at the specific revision. Sometimes the r8169 driver is correct and sometimes the r8168 is the correct driver.

None of this removes the possibility that the NIC is bad on the motherboard.  I'd try booting using some other OSes to see if it works with them or not. If it does, then I'd try forcing the r8169 driver. If that doesn't work, force the r8168 driver. If neither of those work, I'd spend $25 and get an Intel PRO/1000 NIC PCIe card and be done.  Any that used the igb or e1000e drivers tend to "just work".

There are other things you could do ... like getting the latest driver source code from the vendor, compiling it and maintaining it until a later kernel finally includes the driver that you need. It wouldn't hurt to know when that happens, but the $25 Intel NIC solves the problem with very little hassle and will likely work for the entire lifetime of the system. Plus, you'll have better performance and lower CPU overhead, as Intel NIC do more of the processing directly on the NIC, not using the CPU resources.

---

### Post by jgw on 2022-08-02
thank you for the replies.

greg@movies:~$
inxi -N
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 

I guess I do have a driver.  This machine also thinks that my memory is in wrong although that's pretty hard to do,, other than making sure they use the same color for the two inserts.  The reason for my thought on the memory is because I get 1 long beep  then 1 long and one short even though I have re-set them several times.  Guess I will have to buy some more memory although what I have should be good.  I also re-booted with a boot memory stick.  booted just fine but didn't change anything.  I am considering swapping this motherboard out for another (ASUS M5A78L-M/usb3) as they both use the same cpu (AMD FX-4300 3.8GHz Quad Core Socket AM3+ CPU Processor).  I am losing faith in this motherboard.  I will give the other one a try tomorrow and see what happens.  

Any thoughts are welcome - thanks again!

---

### Post by #&amp;thj^% on 2022-08-05
On Arch r8169 just works and on Ubuntu I'm using:
```
inxi -N
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
   ** driver: r8168**
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi
```
and 
```
lsmod | grep r8168
r8168                 552960  0

```
This has been the best option for my NIC
```
lsmod | grep iwlwifi
iwlwifi               450560  1 iwlmvm
cfg80211              974848  3 iwlmvm,iwlwifi,mac80211

```
```
apt policy r8168-dkms
r8168-dkms:
  Installed: 8.049.02-1ubuntu1
  Candidate: 8.049.02-1ubuntu1
  Version table:
 *** 8.049.02-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy/universe i386 Packages
        100 /var/lib/dpkg/status

```

---

