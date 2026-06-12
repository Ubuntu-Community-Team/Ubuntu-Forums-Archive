---
title: "How do you view available wireless networks in 10.04?"
date: 2010-05-11
forum: Hardware
---

### Post by mikeharris7 on 2010-05-11
Hi all - wasn't sure if this was the right forum to post this in. I'm not sure the wireless drivers are installed properly though, and it is on a Dell Mini 9 netbook/laptop. I can't find a place to view available wireless networks. Can someone point me in the right direction?

---

### Post by lisati on 2010-05-11
Next to the speaker icon on the top panel, there should be two arrows. Clicking on that should show which wireless networks are available

---

### Post by mikeharris7 on 2010-05-11
hmmm - I have the battery icon on the left of the speaker icon and an envelope/mail icon on the right of it. Perhaps my wireless drivers aren't installed properly?

---

### Post by byStanderone on 2010-05-11
...this might be of help: [http://www.qc4blog.com/?p=857](http://www.qc4blog.com/?p=857)

---

### Post by mikeharris7 on 2010-05-12
I tried following the instructions for the fix, but in synaptic package manager when I type 'broadcom' I have bcmwl-modaliases as the only choice. Also, when I right click on it 'mark for re-installation' is grayed out.

---

### Post by mikeharris7 on 2010-05-12
ok - I tried sudo apt-get remove &#8211;purge bcmwl-modaliases but am getting an error that command line option -p [from -purge] is not known.

---

### Post by 3rdalbum on 2010-05-12
Run the command:

```
nm-applet
```

to get the Network Manager icon to appear. It should appear even if you don't have wireless or don't have a wireless driver, it does more than just manage wifi networks.

---

### Post by Dougie187 on 2010-05-12
> **mikeharris7 said:**
> ok - I tried sudo apt-get remove &#8211;purge bcmwl-modaliases but am getting an error that command line option -p [from -purge] is not known.

that's because it's --purge not -purge

Also, to check if your wireless is installed, can you open a terminal (Applications->Accessories->Terminal) and type this, and the post the output on here.

```
lshw -c network
```

---

### Post by mikeharris7 on 2010-05-12
ah - I was looking at the comment section of the link listed above and it looked like a single dash. Thanks for that. Here's the output of the command you just gave me:

michael@michael-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0

---

### Post by mikeharris7 on 2010-05-12
ooops - sorry, didn't grab all of it in the copy/paste. Here's the rest: 

version: 02
       serial: 00:21:70:e3:b7:27
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:23:08:5e:e0:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
michael@michael-laptop:~$

---

