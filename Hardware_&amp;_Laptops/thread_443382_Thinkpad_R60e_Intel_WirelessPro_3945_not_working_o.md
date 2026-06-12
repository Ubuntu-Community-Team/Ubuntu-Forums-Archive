---
title: "Thinkpad R60e Intel Wireless/Pro 3945 not working on Ubuntu 7.04"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by wnmusic on 2007-05-14
Hi, all

I've just installed the KUbuntu 7.04 on my Thinkpad R60e laptop, seems all stuffs work perfect expect for the wireless connections. The kernel would load ipw3945 driver, and from the dmesg I could not see any abnormal outputs, just module load infos. 

When I iwconfig eth1( which is the wireless card) the output suggest that I have already connected to my AP, with essid correct and the signal quality is great (99/100). However I could not ping to the AP. always unreachable. When I use iwevent, I could see the output like this: 

xxxxx: Not-Associated
xxxxx: 00:17:9A:FF:66:97 (my AP mac)
xxxxx: Not-Associated
xxxxx: 00:17:9A:FF:66:97 
xxxxx: Not-Associated
xxxxx: 00:17:9A:FF:66:97 

I wonder if anyone has the same problem? and looking forward for your replies .

Regards

NWang

---

### Post by wub on 2007-05-16
HI,

My experience is a bit different but might help you.  I have a Fujitsu Lifebook, with same Intel 3945 card.  I'm running 6.10 (can't recall the nickname right now), from Linux Forum DVD, and has a lot of KDE aps although I'm running Gnome.

The System > Administration > Networking aplet works OK for my wired connection, but I can't get it to allow me to set most of the stuff I need for wireless.

However, I also have Applications > Internet > KWiFiManager and Kwlan.  Of these three different options, I found that KWiFiManager is the only one that can get my wireless card set up.

Once I see that there is a signal and the connection is working, I usually find that the connection still does not work.  I am >not< using DHCP (I probably be, but I'm not), so I end up using 'sudo -i' so I can run a few commands that only root has authority for.

First, I give myself a reasonable IP address:  my wireless card shows up as eth0 in ifconfig, and I am using 192.168.2.XXX as my local network, so I do this:

ifconfig eth0 192.168.2.45

then I need to tell my system where to send packets that go to the internet, my gateway is 192.168.2.110, so:

route add -net default gw 192.168.2.110

>then< everything is good, but name service won't work until I update /etc/resolv.conf.

with my ISP (Cox) 68.6.16.30 is a good nameserver, so I edit /etc/resolv.conf to contain this line:

nameserver 68.6.16.30

and save the file.

At that point, everything works.


I'm sure there is a way to get the other tools to work, but for now this is 'good enough'.  I just did that dance this evening so I could hit this site.  It is awkward, but it does work.

Good luck.

---

### Post by Jo0Lz on 2007-05-27
This is a way to set it up maybe, but I find it way to much trouble.
The nice thing about wireless was that it's so easy to set up. Now, all the steps give me a headache, and to be honest, it doesn't even work. :{.

---

