---
title: "Mediatomb issues"
date: 2008-11-13
forum: General Help
---

### Post by EvilTchnlgy on 2008-11-13
Hey guys, I'm trying to get mediatomb setup with my ps3 and im having some issues. i installed mediatomb via the repositories on intrepid...
I was a bit surprised when despite changing my /etc/default/mediatomb to INTERFACE="eth0" that when I started mediatomb as a non service it kept showing starting on the ip of wlan0...

Running "mediatomb -ip 192.168.0.1" results in the following:

root@phenomx4:/home/brendan# sudo mediatomb -ip 192.168.0.1

MediaTomb UPnP Server version 0.11.0 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2008-11-13 02:55:42    INFO: Loading configuration from: /root/.mediatomb/config.xml
2008-11-13 02:55:42    INFO: Checking configuration...
2008-11-13 02:55:42    INFO: Setting filesystem import charset to UTF-8
2008-11-13 02:55:42    INFO: Setting metadata import charset to UTF-8
2008-11-13 02:55:42    INFO: Setting playlist charset to UTF-8
2008-11-13 02:55:42    INFO: Configuration check succeeded.
2008-11-13 02:55:42   ERROR: main: upnp error -208
2008-11-13 02:55:42   ERROR: Socket error.
2008-11-13 02:55:42    INFO: Please check if your network interface was configured for multicast!
2008-11-13 02:55:42    INFO: Refer to the README file for more information.
2008-11-13 02:55:42   ERROR: upnp_cleanup: UpnpUnRegisterRootDevice failed

I checked and cannot find anything that is using upnp either.... I did stop the process by running "/etc/init.d/mediatomb stop"
I tried running "ipconfig eth0 allmulti" to no avail..
I figured it may have something to do with my /etc/network/interfaces file which only consists of the following

auto lo
iface lo inet loopback

The only reason I didn't just add an entry for my eth0 interface was that I was afraid it would interfere with my current networking setup, originally I setup wlan0 through gnome as to resolve through DHCP dynamically and that was it. Eventually I installed the dhcp server and firewalker and used that to share my wireless internet connection with my eth0 interface. (I think I configured eth0 through gnome but i'm not sure...). I have since used  guidedog to forward ports between the 2 interfaces. I have also added multiple exceptions to my iptables but am not quite sure how to  list my iptables.. I figured t would be the results of iptables -L but that definetly does not include any of the port exceptions i appended...


Sorry if I rambled a bit but I was jsut trying to cover everything and didn't want to sink my internet connection.

So a little diagram to show the connection sequence from the outside world to the ps3 (each object corresponds to the interface or process below it)
ROUTER------COMPUTER(wlan0)----Computer(eth0)-----SWITCH--PS3
DHCPSERVER--DHCPCLIENT(wlan0)--DHCP SERVER(eth0)--XXXXXX--(static ip)

---

### Post by Vodkaneat on 2008-12-16
Try something like:

mediatomb -e wlan0 -p 8080

Works for me :)

---

