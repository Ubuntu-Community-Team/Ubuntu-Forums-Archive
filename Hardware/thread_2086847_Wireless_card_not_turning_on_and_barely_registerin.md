---
title: "Wireless card not turning on and barely registering"
date: 2012-11-22
forum: Hardware
---

### Post by AnArmoredMarch on 2012-11-22
Okay, so I've been messing around with this laptop for a while now. It's a Compaq Presario A900. The short story of it is that a few years ago it caught a virus and my dad nearly threw it out. I picked it up a few months ago and wiped the HDD clean, then installed Windows 7. Tried the windows 8 pre-release, but I got sick of it crashing so much that I just decided that I would try out Ubuntu.
It's been a nightmare so far.
First there was the problem of not knowing what I was doing, but then I worked out that there was a driver problem, but managed to fix that with Widows Wireless Drivers, before I had to get Wine and unpack the driver (took a while; long story), but by the time I finished that, I had realized the fan wasn't running and the computer was over heating. It crashed before I could get an external fan hooked up. When I got it running again, the wireless card wouldn't register. I know it's probably dead and I'll have to go buy an external one, but I want to look at ever option before spending any money.
Some additional info:
Rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d1300000-d130ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:30:bc:02
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.108 latency=64 maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:d1200000-d12000ff

Also, should be mentioned that there is a button on the console. The light is orange; it's been orange since I installed Ubuntu. When I push it, the rfkill toggles hard block to yes (or no, depending on where it is). Other than that, pushing it does nothing at all.
Also, when I go to system settings>network, there is no wireless option there. Only wired and network proxy.
Any and all help is appreciated.

---

### Post by ahallubuntu on 2012-11-22
I highly doubt you burnt out the wireless card due to overheating - rather, I think you would have burnt out something else first.  It's common to have issues with wireless cards in Ubuntu.

In fact, it appears you are not the only one to have issues with it.  Read this thread:

[http://ubuntuforums.org/showthread.php?t=2002545](http://ubuntuforums.org/showthread.php?t=2002545)

Sadly, there is no solution given there.  (Keep googling for "AR242x / AR542x ubuntu".) You could try Ubuntu 12.10 if you haven't already and hope maybe that works better than an earlier version of Ubuntu.

Or - like you said, break down and buy a USB wireless card.

By the way, if you still don't have the CPU fan working, you ought to fix it.  Probably a pain to rip your laptop apart to do so, but it's very important to keep that CPU cool as you probably now realize.  Some external fan probably can't do it as well.

---

### Post by AnArmoredMarch on 2012-11-23
I'll probably deal with the fan problem later, but just so you know, I've always had problems with the wireless card in this thing, and it's just kind of always had heating problems, and the hard drive sucks...Just needs to be replaced, but I don't have the money.

Little update, I stole the USB card from my desktop (gaming computer, windows 7), It's a belkin n300 micro wireless receiver. Doesn't work, but I'm guessing that it's because of the fact that it needs more than the driver to work, and has zero compatibility for Linux. But if I can't get the wireless working, I'm probably just gonna strip this thing of any good working parts and then trash the rest, find some poor sucker with a hard drive problem and buy his computer for $50.

running Ubuntu 12.04, I'll try updating, see if that helps.

---

