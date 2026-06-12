---
title: "Waiting for interface to come up.. (takes foreverrr)"
date: 2005-12-19
forum: Hardware &amp; Laptops
---

### Post by gbkyle on 2005-12-19
During the boot of my machine it takes atleast 2-3mins to get passed the waiting for interface to come up.. I am using a Linksys Wireless Wifi Card (BCM4306) w/ndiswrapper.. 

my /etc/network/interfaces reads...

```
auto wlan0

iface wlan0 inet dhcp
auto eth0
up dhcpd -q -cf /etc/dhcpd-wlan0.conf -pf /var/run/dhcpd-wlan0.pid -lf
/var/lib/dhcp/dhcpd-wlan0.leases wlan0
down kill `cat /var/run/dhcpd-wlan0.pid`
wireless-essid linksys

iface eth0 inet dhcp

```

 I Dont know what could be causing it.. by the time i get into gnome, Wireless is up and running fine..

---

### Post by lorenco on 2005-12-19
I have the same problem....

I have a Thinkpad with Both Wireless and Ethernet.  I suspect that dhcp timeout havesomething to do with this... ?? 

I would think (but still have not tried...) that if you enable only one interface that will get the IP, your problem goes away (if you have more than one interface...)  The interface that is not connected will take two odd minutes to timeout before proceding...  (Maybe even providing a static IP will help to prove this...)

This is my thinking...  this was ALOT quicker in hoary though ?

What changed, I Do not know.

---

### Post by gbkyle on 2005-12-19
That makes sense.. But i thought i had my interface disabled. I took it out of network/interfaces but i guess it popped itself back in, how do i permanently disable my eth0?

---

### Post by Lambert on 2005-12-19
If you want to use wireless instead of wired on boot then you need to make these changes.

1. remove that line auto eth0
2. system>administration>networking choose the eth0 in the list, click on properties and remove the check from enable this interface

---

### Post by lorenco on 2005-12-29
I do not have the luxury of using a single interface, I have wireless @ home
and Ethernet in the office as primary (some wireless as well but not configurred)

I fixed the long wait by adjusting the timeout values in "/etc/dhcp3/dhclient.conf" :
timeout 15;

Now it waits for 15 secs and not 60 :cool:

---

