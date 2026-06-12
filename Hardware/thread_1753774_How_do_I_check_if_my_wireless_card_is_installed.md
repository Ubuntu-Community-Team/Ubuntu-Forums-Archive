---
title: "How do I check if my wireless card is installed?"
date: 2011-05-09
forum: Hardware
---

### Post by rhuse on 2011-05-09
How do I check if my wireless card is installed? It is blacked out in the "network applet" and the physical button does not do anything.

Ubuntu 10.10
Intel® PRO/Wireless 3945 a/b/g

Edit: the sysinfo application crashed on me before but I does look like my wireless card is installed. Which brings me to my next question: How do I turn it on?

rfkill list all

Returns: 0: phy0: Wireless LAN
               Soft blocked: no
               Hard blocked: yes

---

### Post by matt_symes on 2011-05-09
Hi

Open a terminal and copy and paste into a terminal each of these commands (they are case sensitive)

```

sudo lshw -C network
lspci -nnk | grep -iA2 network
lsusb
```Post the results back here by copying and pasting from the terminal into your next post. Enter your password when asked. It will not be echoed to the screen. This is normal.

Kind regards

---

### Post by rhuse on 2011-05-09
*-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:b8:3a:a4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-28-generic firmware=15.32.2.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:43 memory:d4000000-d4000fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:85:02:41
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=46.239.119.8 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:4000(size=256) memory:d8000000-d80000ff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by matt_symes on 2011-05-09
Hi

What is the make and model of the PC/laptop ?

I assume you have checked the wireless kill switch to make sure wireless is enabled ?

Kind regards

---

### Post by rhuse on 2011-05-09
Fujitsu Siemens Amilo Pro V3405

If you by "kill switch" mean the physical button above the keyboard then yes. It does not do anything neither does the fn+f10 combo and LED is turned off.

Edit: Googled more and found this but it doesn't work either
sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

---

### Post by matt_symes on 2011-05-09
Hi

There was a bug report raised on this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665993](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665993)

Unfortunately you do not have a Dell or a HP so the solutions there will not help you. 

There may be a backport for you from natty. Have you had a look ?

In the meantime i am looking for a solution. If others know of a solution i am sure they will chime in.

Kind regards

---

### Post by rhuse on 2011-05-09
Thanks Matt.

I haven't been using linux in a couple of years and I just switched to 10.10 a couple of months ago from windows so I am not entirely sure what you men by "backport". 

Anyway, I use my computer pretty much as a desktop with a wired internet connection so it isn't a big deal for me. It's just a shame when everything else works so perfectly. I didn't even have to install any additional drivers like I had to do in windows.

---

