---
title: "No ethernet even w/ ethernet cable attached on TinyCore Linux"
date: 2009-05-28
forum: Hardware
---

### Post by johnnyxxxcakes on 2009-05-28
I am trying to install Tiny Core Linux as the operating system on my ASUS Eee PC 1000HA. When I booted the operating system, I wanted to test everything out to see if I could be comfortable with the switch. I have experimented with Tiny Core a bit and I know how to install files and whatnot, but here is my problem:

If I wanted to begin installing applications to see how they run on the Eee, I would have to hook up an ethernet cord, and then download the wifi drivers. When I hook up the ethernet cord, it doesn't automatically connect to the network. I went into the control panel and enabled the DHCP Client, and then I went to the appsbrowser and tried to search for a package, but it told me there was no connection, and that I should try later. I tried restarting the Eee and boot up again, this time with the ethernet cable plugged in, but I still get no connection. I tried the DHCP Client again, but noticed that everytime I close out of the window, the DHCP Client resets itself to off.

Anybody have any clue what I should do?

---

### Post by x22 on 2009-05-28
well, usually something like this will work:

ifconfig <interface> up
dhclient <interface>

---

### Post by johnnyxxxcakes on 2009-05-28
> **x22 said:**
> well, usually something like this will work:

ifconfig <interface> up
dhclient <interface>

Okay, first I tried "ifconfig -a" which somebody else recommended, and it gave me this:

> 
dummy0    Link encap:Ethernet HWaddr 26:2B:2E:52:1B:F5
          UP BROADCAST RUNNING NOARP MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1248 (1.2 KiB) TX bytes:1248 (1.2 KiB)


Then I tried "ifconfig dummy0 up" and I get:

> 
tc@box:~$ sudo ifconfig dummy0 up
tc@box:~$


So I'm guessing it did something. I tried to press the DHCP Client button again but I get nothing. I opened a terminal and tried "ping google.com" but it just tells me that's a bad address or something.

---

### Post by Vermind on 2011-08-20
Hello,
Any luck with this?
I have an EEE PC 1000HA with Ubuntu 10.4 on it. It properly associates with my WLAN box, but fails to get an IP address from the ISP's DHCP server. I also have an old Internet connection that I will be letting go of soon. If I hook its modem up to the WLAN box, the EEE PC associates with the WLAN and successfully gets an IP address. Both the cable internet and the old one are bridged, just the old one works and the new one doesn't.

With a cabled connection, I get the same issue: No IP address. With static addressing I can connect to the WLAN box, but that will not give me Internet.
So, I am wondering what's wrong with the DHCP server of my new ISP vs the old one?
All the other devices in the home can connect to the new one just fine.

I have tried the 3.0 kernel, the 2.32 kernel, the 2.35 kernel, different wireless drivers, Linux Mint 11, Ubuntu 10.04.

---

### Post by Vermind on 2011-08-21
My current solution: I put
```
options rt2860sta mac="another mac address"
```
into ```
/etc/modprobe.d/my-macaddr.conf
```

where another mac address is the mac address of another one of your devices, or you can install macchanger and ask it for a random vendor+id pair and put it there. rt2860sta is my network driver, yours might differ.

The root cause is the internet provider's lease database, which is probably messed up.

---

