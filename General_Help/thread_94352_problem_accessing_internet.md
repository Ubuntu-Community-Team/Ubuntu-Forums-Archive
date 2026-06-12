---
title: "problem accessing internet"
date: 2005-11-23
forum: General Help
---

### Post by racermike1967 on 2005-11-23
Hi, I just did a clean install of breezy and now my cable connection does not work.  I am not able to access the internet.  Is there a way to fix this?

---

### Post by jaykup on 2005-11-23
go to system > administration > networking

make sure your eithernet card is enabled, and is set up for DHCP or you can manually set a static IP (must set DNS as well if you go this route)

If that all looks ok, make sure the connections are OK and restart your cable modem.

---

### Post by racermike1967 on 2005-11-23
I have tried those methods you mentiond but it still doesn't work

---

### Post by jaykup on 2005-11-23
are you directly connected to the modem?

try running

ip addr

and see if you have either a network (192) or an internet (w/e) IP

---

### Post by racermike1967 on 2005-11-23
I tried "ip addr" but I did not see either of the items you mentioned.

---

### Post by jaykup on 2005-11-23
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:50:22:d4:11:c9 brd ff:ff:ff:ff:ff:ff
    inet 192.168.12.200/24 brd 192.168.12.255 scope global eth0
    inet6 fe80::250:22ff:fed4:11c9/64 scope link
       valid_lft forever preferred_lft forever


that is what my eth0 interface looks like

the IP address is 192.168.12.200

are you directly connected to the modem?

---

### Post by racermike1967 on 2005-11-23
What does "directly connected to the modem" mean?  I thought that since I was using a cable internet, I use the ethernet rather than the modem.  Anyway, in my network settings for my modem connect it says "The interface ppp0 is not configured".

The output I get when i type in "ip addr" is :

2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
link/ether 00:0d:60:77:ef:f6 brd ff:ff:ff:ff:ff:ff
inet6 fe80::20d:60ff:fe77:eff6/64 scope link
valid_lft forever preferred_lft forever

---

### Post by jaykup on 2005-11-23
You're not getting an IP address if you're using DHCP in your network settings.

Directly connected means you are not running though a router, and the computer you are on is connected using a public IP (like 66.32.85.115) vs a private IP a router gives out (192.168.1.7)

You need to determine wheither you are using a router or not, then find out of the router is set up correctly.  If it is, then make sure the modem is connecting to the internet.  If both those are working (or just the modem if you don't have a router) then you need to check your settings in your network properties.

Most of the time you will just be using DHCP, and if its enabled, and set up correctly, then the last thing it can be is a network card that isnt supported by Linux.

A perfect test would be to unplug the computer's ethernet cable, plug it into a working windows machine, and see if you have internet.  THis will determine if your router/modem configuration is bad, or if its linux.

Hope this helps.

---

### Post by racermike1967 on 2005-11-24
When I had hoary installed on my laptop, my internet connection was fine.  All I did then was enable my ethernet port.  Now that I have done a clean install of breezy, my internet connection does not seem to work, but when i pull out the ethernet cable and plug it into my windows machine, it automaitcally works.  Right now I am on a friend's  wireless connection and internet seems to work fine but slow.

---

### Post by maol62 on 2005-11-26
OK, it looks like you have the same problem as I had when I made a clean install of Breezy. In my case its related to ipv6 and my router doesnt support ipv6. Therefore I have to shut down ipv6 and this is how I do it.

First I add my ISPs two DNS entries in /etc/resolv.conf (where xxx and yyy are the two entries):

*sudo gedit /etc/resolv.conf*

nameserver xxx.xxx.xxx.xxx
nameserver yyy.yyy.yyy.yyy
nameserver 192.168.1.1

The last row is pointing at my router and this could, of course, be something else in your configuration. 

Second, because the /etc/resolv.conf file is owerwritten when rebooting, I have to lock the file from being changed:

*sudo chattr +i /etc/resolv.conf*

Third I prevent ipv6 from starting up:
[I]
sudo gedit /etc/modprobe.d/aliases[/I]

and look for this row:
alias net-pf-10 ipv6

and then replace it with these three rows:
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off

Last I launch Firefox and types about:config in the address field. Then type ipv6 in the filter field. Change the entry network.dns.disableIPv6 from false to true.

Then it should work just fine. I'm not an expert so maybe this aint the right way or the best way but at least it works for me. :)  If someone have a better solution please share your knowledge!

---

