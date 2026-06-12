---
title: "postconf error on network restart"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by Skip Da Shu on 2009-07-21
I upgraded my v8.10 desktop today.  When I came back to it there was some message about postfix... I hit NEXT and went back to my scratch install of Jaunty on another machine.  When I came back a bit later it was done and after a reboot all seemed good.  Then I saw the little red x on the network-manager-gnome applet in the top panel was still around.  I had problems with v8.10 when it first came out with my then static IP.  I know back then I updated the /etc/network/interfaces file but can't recall if I modified anything else or not.  

In an attempt to get that applet to work again... I tried:

sudo dpkg-reconfigure network-manger-gnome
and
sudo dpkg-reconfigure network-manager

2nd one told me my interfaces file was invalid.

I deleted the interefaces file and tried it again... got some error about not having an interfaces file. 

I put it back and restarted networking (sudo /etc/init.d/networking restart) and rx'd the following:

```
:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          postconf: fatal: open /etc/postfix/main.cf: No such file or directory
There is already a pid file /var/run/dhclient.eth1.pid with pid 3247
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1f:d0:d4:80:37
Sending on   LPF/eth1/00:1f:d0:d4:80:37
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.218.18 port 67
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1f:d0:d4:80:37
Sending on   LPF/eth1/00:1f:d0:d4:80:37
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.218.17 from 192.168.218.18
DHCPREQUEST of 192.168.218.17 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.218.17 from 192.168.218.18
bound to 192.168.218.17 -- renewal in 32941 seconds.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
 * Stopping NTP server ntpd
   ...done.
                                                                         [ OK ]
:~$  * Starting NTP server ntpd
   ...done.
```

As you can see my DHCP server is assigning a (and the proper) ip address to this machine but I don't know what this "postconf" error is or how to make it go away.

My interfaces file is nothing but:
```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
```

What do I need to run to create a valid **/etc/postfix/main.cf**?

---

