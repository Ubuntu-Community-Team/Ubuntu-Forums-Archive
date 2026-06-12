---
title: "no connection with ethernet cable"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by jenb on 2009-06-30
Hi I'm very new to ubuntu,
I just installed ubuntu server 9.04 on a msi wind desktop.  I got ubuntu working but I am unable to connect to the internet with an ethernet cable.  
When I enter the command: sudo dhclient eth0 
I get:
.........
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: noo such device
Bind socket to interface: No such device


Route command reveals:

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use IFace

Any ideas?

---

### Post by linuxmagick on 2009-06-30
Can you post the results of ```
ifconfig -a
```?

---

### Post by jenb on 2009-06-30
ifconfig -a gives:


eth1
Link encap:Ethernet HWaddr 00:24:21:52:27:3c
Broadcast Multicast MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
rx bytes:0 (0.0 B) TX bytes:0(0.0 B)
Interrupt:251 Base address:0x2000

lo
Link encap:Local Loopback'
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)

thanks

---

### Post by jenb on 2009-06-30
When I think about it I didn't install an Ethernet driver.  I assume I need to do this.  I found it and downloaded it to a CF card from a different computer.  Once the CF card is inserted into the computer with ubuntu server, how do I get it off the card and installed properly (if that is the problem)?

Thanks for helping

---

### Post by linuxmagick on 2009-06-30
You shouldn't need to install a driver for it.  Ubuntu (Linux in general) can recognize most network adapters right out of the box. From the output you provided it looks like your network adapter is detected as eth1 instead of eth0.  

Does sudo dhclient eth1 work for you?

---

### Post by jenb on 2009-06-30
sudo dhclient eth1 gives:

Listening on LPH/eth1/00:24:21:52:27:3c
Sending on LPF/eth1/00:24:21:52:27:3c
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
* Reloading /etc/samba/smb.conf smbd only
...done.
bound to 192.168.1.100 -- renewal in 34567 seconds.

---

### Post by linuxmagick on 2009-06-30
Okay.  It looks like the interface eth1 received a network address of 192.168.1.100 from the DHCP server.  Are you still experiencing any problems with the connection?  It should be good now from what I can tell from what you posted.

---

### Post by jenb on 2009-06-30
ohh..yes it works, great.

Is there something I need to do so Ubuntu will know how to connect when I reboot?

Thanks for stepping me through this!

---

### Post by linuxmagick on 2009-06-30
No problem.  I'm really surprised that it isn't getting the address when you boot up.  I installed wicd for my network manager instead of using the default network manager, so I'm not as familiar with it.  There may be some setting you need to check.  Maybe someone else will have the answer you're looking for.  In the mean time, you could simply edit and add dhclient eth1 to the file /etc/init.d/rc.local.  That should accomplish getting an address from DHCP at boot.

---

