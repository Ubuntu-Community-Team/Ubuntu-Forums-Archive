---
title: "No Network on clean install 8.10 CD"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by ReaderK on 2009-02-12
Hi guys. My son (16) just had his first go with Ubuntu & linux after downloading a CD image of 8.10 last night. 

The CD worked great as a LiveCD and we were able to use his wired network from inside the booted LiveCD.  BUT after doing the install to hard drive Ubuntu booted without a working network and I found some posts that implied this was a problem some months ago but without a clear fix. 

eth0 showed up in ifconfig with a dummy IP.
eth0 did not appear in /etc/network/interfaces. 

I found that by configuring the interface manually in 
/etc/network/interfaces and specifying ALL OF:

```
auto eth0
iface eth0 inet static
   address 192.168.1.6
   netmask 255.255.255.0
   gateway 192.168.1.1
```

and restarting the network layer with 
```
sudo /etc/init.d/networking restart
```

It mostly worked.  It worked most reliably after a **reboot**.

If it sheds any light on the problem at the first point we tried setting the interfaces file we set its IP to blah.8 and did the restart.  At that point it started working BUT had clearly talked to DHCP and obtained the gateway (which we'd forgotten in interfaces) and been given the proper blah.6 address! All seen with ifconfig. This seemed very odd. On a reboot it properly obeyed the interfaces file static/IP/netmask but had no gateway as we hadn't defined it at that point. Which confirms the net restart had allowed DHCP to kick in and take priority over the interfaces file. All very weird.

---

### Post by Kuno81 on 2009-02-13
The network envirement of 8.10 is not managed by /etc/network/interfaces anymore. 
The network manager replaced this. 

I had same problem with network connection at a clean 8.10, too. So i deinstalled the network manager and did it in the old-school-way with the interface-file.

See:
[http://ubuntuforums.org/showthread.php?t=1067857](http://ubuntuforums.org/showthread.php?t=1067857)

Maybe this helps.

---

