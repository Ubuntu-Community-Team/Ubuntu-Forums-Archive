---
title: "no wireless internet"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by WarrenKarl on 2009-05-07
Hi,

I love Ubuntu.  I installed Jaunty from the CD that I downloaded
and my wireless internet does not work.  This is strange because I had no problem with it on Intrepid.

I did a sudo lshw - C network and this is what I got:
*-network                
       description: Network controller 
       product: BCM4328 802.11a/b/g/n 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 03 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: ba:91:b0:79:10:b0 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

I don't know what any of this means, but it is clear that the network is DISABLED.  

Please help.  I am going through Ubuntu withdrawl.

---

### Post by chellrose on 2009-05-07
You might try the suggestions here:
[http://kubuntuforums.net/forums/index.php?topic=3103555.0](http://kubuntuforums.net/forums/index.php?topic=3103555.0)

---

### Post by WarrenKarl on 2009-05-08
Hi,
It's me again.  I have failed to get the wireless internet working.
Here is some more information.  I have a Broadcom wireless card in my HP
laptop.  The number is BCM4328.  I took my laptop to a wire and downloaded
b43-fwcutter and got the appropriate firmware.  Now when I go to System>Administration>Hardware Drivers, it tells me that I have the
Broadcom driver, that it has been activated, but that it is not used
(whatever that means).

When I do a iwconfig I get
l0 no wireless extensions
etho no wireless extensions
pan0 no wireless extensions

I have tried a sudo /etc/init.d/networking restart but nothing
happened.

Does anyone have any further ideas for me?
Please.

---

### Post by WarrenKarl on 2009-05-08
P.S.

Ubuntu does not see the router.  I have a network icon that shows bars
with no signal and an x.  If I left click on it all the options are greyed
out.  If I right click on it, I can edit wireless network connections, but
there are no wireless connections. 

Should I try to manual add a wireless connection?  If so, do I need to
put in my MAC address and other details?  

The router worked perfectly with Intrepid and works perfectly when wired
to the computer.

I hope someone knows.

---

### Post by chellrose on 2009-05-10
I don't have any further ideas, sorry.

But here's a bump for your thread.  Maybe someone smarter than me will see it and jump in. :KS

---

### Post by dsiddens on 2009-05-11
no wireless on this HP laptop, AMD64, Jaunty, Broadcom 4311,2.

---

### Post by banduan on 2009-05-11
Similar problem, posted in another thread. Problem started with Jaunty and was carried on when downgraded to interpid.

---

### Post by Peter09 on 2009-05-11
Need to see full output of

 ```
ifconfig
```

and contents of

/etc/network/interfaces

---

### Post by banduan on 2009-05-11
> **Peter09 said:**
> Need to see full output of

 ```
ifconfig
```

and contents of

/etc/network/interfaces
Don't wanna take over this thread, so I'm posting output in my thread.
[http://ubuntuforums.org/showthread.php?p=7256655#post7256655](http://ubuntuforums.org/showthread.php?p=7256655#post7256655)

---

