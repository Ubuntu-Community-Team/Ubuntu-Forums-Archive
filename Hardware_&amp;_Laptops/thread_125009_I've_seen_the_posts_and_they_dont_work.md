---
title: "I've seen the posts and they dont work"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by closeyourwindows on 2006-02-02
ok, so here the low down:
I have ubuntu 5.10 on solo 9300 gateway laptop pentium III. I am using two pcmcia cards, one for lan and other for wireless.  the lan has never had an issue and works without fail each time.  the wireless has never worked.  the card is linksys wpc54g v.2 and I do have the driver installed.  according to the wireless-gui the hardware is present and lights are on.  
I have been reading the posts and I tried all of them with no hope for wireless nirvana.  

so far here is where I am at.
```
nate@picfix:~$ sudo iwconfig
Password:
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

nate@picfix:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

nate@picfix:~$ sudo ndiswrapper -m modprobe config already contains alias directive

nate@picfix:~$ ndiswrapper -l Installed ndis drivers:
bcmwl5  driver present

nate@picfix:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:DA:2F:16:9B
          inet addr:xx.xx.131.159  Bcast:255.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::250:daff:fe2f:169b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:3 txqueuelen:1000
          RX bytes:2376667 (2.2 MiB)  TX bytes:177308 (173.1 KiB)
          Interrupt:9 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:858776 (838.6 KiB)  TX bytes:858776 (838.6 KiB)


```
 now I think all I need is to set up wlan0.

---

### Post by mpvano on 2006-02-03
Did you do anything more than just configuring ndiswrapper? You know you have to arrange things so that it gets loaded at every boot for it to work.

Try this in a terminal window:

lsmod | grep ndis

and see if ndiswrapper shows up in the output.

If not, I believe the simplest way to get things configured to load it is to add it's name to the list in /etc/modules.

Before you do that, try loading it manually and see if you get any error messages.

sudo modprobe ndiswrapper

If you get errors here, you need to fix them first. If you tried to build ndiswrapper from source - you may have done it incorrectly - most of the "cookbook" recipes for doing this don't work properly or assume you know what you're doing already. If you didn't build ndiswrapper from source, then you could have a windows driver that doesn't work with it. You may need to visit the ndiswrapper wiki to find out where to get the correct driver.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

