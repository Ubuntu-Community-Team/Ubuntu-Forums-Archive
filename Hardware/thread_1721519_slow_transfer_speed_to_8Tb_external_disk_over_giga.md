---
title: "slow transfer speed to 8Tb external disk over gigabit ethernet"
date: 2011-04-04
forum: Hardware
---

### Post by daveli on 2011-04-04
Hi there! I am having difficulty transferring data from my computer to an external 8Tb hard disk using a gigabit ethernet cable. The current speed is about 10-12Mb/sec and I think this should be much higher. 

I have Kubuntu 10.04 installed with two network cards configured, one for internet and server connection (eth0) and the other connected directly to the hard disk (eth1). After looking around on the web, both interfaces work at the same time but I cannot set the Jumbo Frames so that the connection between the PC and the hard disk to be faster. I configured the disc ftp server to accept 9000 byte frames and I have tried to modify this size in linux with no luck. 

I have found that the tg3 driver that the card uses (a Broadcom card) has a MTU of 1500 by default but I cannot modify this value. I tried modifying the */etc/network/interfaces* and does not help. If I try setting the MTU, after setting the interface with  ifup eth1 mtu 9000 I get an error and it only works with MTU values of 1500 or less. 
    
    Checking the ifconfig output I can see the connection is set to  1000Mb/s, so I understand the connection is Gigabit so in theory the wire would allow a faster transfer.

What else can I try??

Thanks

D.

---

