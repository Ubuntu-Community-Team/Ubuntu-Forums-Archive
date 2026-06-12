---
title: "Toshiba Portege R835, getting suspend working on Ubuntu 10.10."
date: 2011-04-23
forum: Hardware
---

### Post by hedrinbc on 2011-04-23
It appears adding USB3 to the blacklist is the solution for suspend.

```
echo blacklist xhci_hcd | sudo tee -a /etc/modprobe.d/blacklist.conf >/dev/null
```

I'll update this thread if I discover anything else that needs to be tweaked. 

Hat Tip -> Thanks pr0grammer1 on [this thread]("http://ubuntuforums.org/showthread.php?t=1668950") for the idea and command even though he intended to target different hardware.

---

### Post by svast on 2011-04-24
Problem is that USB-3 gets disabled...
So my guess is that you won't be able to see the benefits of high-speed tranfers with USB-3 devices.

---

### Post by willsomebody on 2011-05-01
How well does ubuntu work on the r835 overall? I am thinking of getting one, and ubuntu compatibility is an important factor in my decision.

---

### Post by svast on 2011-05-02
> **willsomebody said:**
> How well does ubuntu work on the r835 overall? I am thinking of getting one, and ubuntu compatibility is an important factor in my decision.

I bought one last week, and hope to receive it soon.

---

### Post by regiomontanus on 2011-05-08
> **svast said:**
> I bought one last week, and hope to receive it soon.

I would love a follow-up once you get the computer and get it running! :popcorn:

---

### Post by svast on 2011-05-09
delivery a bit delayed, but be sure I will post my follow-up

---

### Post by svast on 2011-05-21
> **regiomontanus said:**
> I would love a follow-up once you get the computer and get it running! :popcorn:

I got mine: Toshiba Satellite R830-136 with 128GB SSD, now running Ubuntu 11.04 natty narwhal, everything seems to be working out of the box:
- integrated Display
- sound
- wifi
- ethernet 1GB
- webcam
- trackpad with 2 finger-scrolling
- Fn-xx keys for sound, etc.
The battery time is amazing, and the SSD makes that laptop very fast (that way I can confirm that the bottleneck usually is the HDD).

VGA and HDMI: not working out of the box with Unity. I can't get it to work with external VGA nor HDMI at full external display resolution (I have a full-HD 1920x1080 monitor). I think this is a bug in sandy bridge driver for Compiz or whatsoever, Ubuntu did not integrate the latest intel drivers yet.
**If I start the session with "Classic (no effects)", VGA/HDMI output is perfect**.


One bad thing: external display:

---

### Post by k3for on 2011-06-08
On 11.04, Toshiba Portege R835-P50X (Core i3 processor for the longer battery life, rather than the zippier i5) with 32GB SSD, which is fine - 16GB for the distro, 16GB for virtualbox vdi files like running Win7 inside.  

All hardware working except USB 3.0 not at all, WD MyBook 3TB or the 4-port hub I bought.  USB 2 is fine.  

Routinely get 8 hours of battery life and boot time is 4-5 seconds.

Am looking around for a solution - might be the "fix" they had to make to get suspend working.

---

### Post by atanumaulik on 2011-08-08
I am planning to buy Toshiba Portege R835-P56X. I would love to know whether anyone has used Ubuntu 10.04 LTS on this machine ? Has all the compatibility issues with Ubuntu (freezing and fan speed problems) been finally solved ?

---

### Post by caffiend on 2011-08-13
> **svast said:**
> I got mine: Toshiba Satellite R830-136 with 128GB SSD, now running Ubuntu 11.04 natty narwhal, everything seems to be working out of the box:
- integrated Display
- sound
- wifi
- ethernet 1GB
- webcam
- trackpad with 2 finger-scrolling
- Fn-xx keys for sound, etc.
The battery time is amazing, and the SSD makes that laptop very fast (that way I can confirm that the bottleneck usually is the HDD).

VGA and HDMI: not working out of the box with Unity. I can't get it to work with external VGA nor HDMI at full external display resolution (I have a full-HD 1920x1080 monitor). I think this is a bug in sandy bridge driver for Compiz or whatsoever, Ubuntu did not integrate the latest intel drivers yet.
**If I start the session with "Classic (no effects)", VGA/HDMI output is perfect**.


One bad thing: external display:

I'm running a portege R835 P50X and I cant get dvd to work, usb either or wifi sort of I'm running in virtual box so somehow windows hands over the wifi as a hard line anyone have any idea why the dvd isn't working tho?

---

### Post by svast on 2011-08-15
sadly, my satellite R830 136 broke last month, so I am back to my good old Vaio until it gets back from Toshiba tech support labs.
Looks like the motherboard or something similar died after 5weeks, hope the SSD won't get reset to Win7!!!

@caffeind: sorry for my poor English (I am not native speaking), I don't understand your issue: which OS is running as host, which one is in Virtualbox?

---

### Post by craig100 on 2011-11-04
I have a new Toshiba R380-138 on which I'm running ubuntu 10.10. Everything seems to work except Wifi.  Doesn't even appear on the network choices. Is this an issue with the Sandy Bridge architecture or is there a fix> I really, really, really don't want to upgrade to 11.10, Gnome Shell or Unity UI's.


craig@craig-TOSH:~$ sudo lshw -C network
[sudo] password for craig:
  *-network
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: e8:9d:87:a1:23:22
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c2600000-c2601fff
craig@craig-TOSH:~$

---

