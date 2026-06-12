---
title: "IBM/Lenovo ThinkPad R51e Networking Issue"
date: 2009-04-25
forum: Hardware
---

### Post by MadDawg010 on 2009-04-25
I have a ThinkPad R51e with a Broadcom NetXtreme Fast Ethernet interface and a 11b/g Wireless LAN PCI Adapter and neither one seem to be fully recognized by Ubuntu. The ethernet port works somewhat, but I cannot connect to the Internet, or even my modem, however I can connect to my router. 

I can't seem to change the address on the interface for some reason. I can make a new connection, but it is never applied. I'm just stuck with the same 192.168.1.107 (/24) address when I look at the network utility in the admin menu.

When I boot into Windows, I can get connected with no issues, regardless of which interface I use.

Any suggestions/things I should know?

---

### Post by coffeeaddict22 on 2009-04-25
Hi,
There's a lot of stuff around, as wifi in particular has been a problem for Linux.  Things have changed quite a bit(for wifi) in the last 8 months, so be a bit wary of old webpages.  
There's a good page or two in the wiki; try [https://help.ubuntu.com/community/NetworkDevices]("https://help.ubuntu.com/community/NetworkDevices")
Essentially, start with the wired connection.  Wired is easier.
find a terminal, and try ```
ifconfig
``` which should tell you a bit about your network.  ```
sudo lshw -C network
``` will also add information on the hardware, and from there you should have an idea whether it's a hardware issue, a driver problem, or a network glitch.  If you need more help, post the output from the above commands back here.

---

### Post by sahabcse on 2009-04-25
sudo ifconfig eth0 192.168.1.107 netmask 255.255.255.0 up

For more info 
[http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html](http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html)

---

### Post by MadDawg010 on 2009-04-25
Alright, my ethernet interface works fully now. I don't know what was causing the problem, but it just started working for me.

Thanks for the replies. I'll keep this bookmarked in case I run into problems again.

---

