---
title: "Networking Adapter Problem HP dv4 4038"
date: 2011-08-25
forum: Hardware
---

### Post by thedrifter on 2011-08-25
Hi there, 

I just got this bran new laptop yesterday and tried installing 10.10

It installed fin, except that networking is disabled.

When I do lshw I get the following.

drifter@drifter-HP-Pavilion-dv4-Notebook-PC:~$ lshw -class network

  ***-network DISABLED**      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:0a:db:34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c2500000-c250ffff
 ** *-network UNCLAIMED**
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c1400000-c143ffff ioport:2000(size=128)

Obviously Ubuntu sees my hardware but not sure why it's disabled, or how to enable it.  Is it a driver problem?  If so where can I find drivers for this particular hardware?

Would love to get this going.  I would really hate to have to have to live with Windows 7 on this beauty.

hmmm wait a second.  I see it says 64bit for the width.  I installed Ubuntu 10.10 32 bit.  Could that be it?

The reason why I did that was because when I put the 11.04 64 bit version CD for installation, it would not boot up to it.  So I decided to go to the ubuntu download page (from within the default Windows OS) and when I clicked on Download, it recommended 32 bit.

---

### Post by gordintoronto on 2011-08-25
32-bit is not the problem. 10.10 might be. It appears that you had a bad download or a bad burn of the 11.04 CD. Can you boot the CD on another computer?

Please post the output of lspci

Which type of network do you want to run, wired or wireless? The wireless adapter appears ready to rock and roll.

I've been using 64-bit for more than two years, and it has caused me zero grief.

---

