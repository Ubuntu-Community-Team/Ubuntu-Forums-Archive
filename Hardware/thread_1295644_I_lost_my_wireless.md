---
title: "I lost my wireless"
date: 2009-10-19
forum: Hardware
---

### Post by RandyRitter on 2009-10-19
Please bare with me, I am a ubuntu novice.

I recently installed ubuntu server on a dell inspiron 830.  I did this on a laptop only because it was available but everything went perfectly.  As I was experimenting with some of the available packages, I suddenly realized that it was no longer recognizing my wireless card.  Everything was working fine, when I was plugged in it used the wire, when not it switched to the wireless.  Now, it appears to not even know there is a wireless card.  One of the networking packages I installed must have corrupted something.

I suppose I could reinstall from scratch, but that wouldn't really teach me anything.  The problem is I don't know where to start in trying to track down and repair this issue.

So, could I have some suggestion where to look and what to look for?

Thanks very much!

---

### Post by Dark_Stang on 2009-10-19
Go ahead and run the following commands and post the output, that will help us get some more details.
```
ifconfig
iwconfig
```

Edit: Also... uh, why did you install the server edition on a laptop? Why not the desktop edition?

---

### Post by RandyRitter on 2009-10-20
Command output:

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b2:69:cc  
          inet addr:10.110.3.20  Bcast:10.110.15.255  Mask:255.255.240.0
          inet6 addr: fe80::21d:9ff:feb2:69cc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3129127 (3.1 MB)  TX bytes:388971 (388.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

virbr0    Link encap:Ethernet  HWaddr e2:32:94:90:f0:84  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::e032:94ff:fe90:f084/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:3990 (3.9 KB)

---------------------------------------------------------------------------
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

virbr0    no wireless extensions.

pan0      no wireless extensions.

------------------------------------------------------------------------------

If I understand what this is saying, I gather that the OS is no longer even recognizing that there is a wireless card in the machine.  How do I go about installing new hardware?  Is that the correct next step?

BTW:  The reason for the laptop is simply testing.  I´ve played around a little bit with desktop and wanted to try out server and LAMP.  The laptop was a convenient piece of hardware at the time.  This is not a long term home for it.  Just learning...:)

Thanks again for the help!

---

### Post by RandyRitter on 2009-10-20
If found the following command in help.  It shows that there is a card there but that it is unclaimed.  The help suggested that I use a utility to utilize a Windows driver.  I downloaded the driver and the utility and installed the driver however there was no change on the results of the ifconfig or the iwconfig.

$ sudo lshw -C network

  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
...

Still looking.....

---

### Post by Dark_Stang on 2009-10-20
Intel cards are supported out of the box... Hm...

---

### Post by RandyRitter on 2009-10-20
Yes, I believe the Intel cards must be supported.  When I first performed the install, everything worked great!  Wired and wireless.  Somewhere along the way one of the packages I tried out must have removed something it should not have.

How do I ask ubuntu to "re-discover" the Intel card and associate the appropriate drivers?

---

### Post by RandyRitter on 2009-10-21
I tried installing the free wireless drivers but as I got into it, they did not appear to support intel cards.  Is that true?

Anyone have any ideas how I can have Ubuntu Server ¨re-discover" the hardware on my machine?

---

